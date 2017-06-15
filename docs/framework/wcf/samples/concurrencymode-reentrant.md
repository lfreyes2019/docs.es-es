---
title: "ConcurrencyMode reentrante | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b2046c38-53d8-4a6c-a084-d6c7091d92b1
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# ConcurrencyMode reentrante
Este ejemplo muestra la necesidad y las implicaciones de utilizar ConcurrencyMode.Reentrant en una implementación del servicio.ConcurrencyMode.Reentrant implica que el servicio \(o la devolución de llamada\) procesa solo uno mensaje en una hora determinada \(análogo a `ConcurencyMode.Single`\).Para asegurarse la seguridad para subprocesos, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bloquea el`InstanceContext` que procesa un mensaje para que no se pueda procesar ningún otro mensaje.En el caso del modo reentrante, `InstanceContext` se desbloquea justo antes de que el servicio haga una llamada de salida por la que permite la llamada subsiguiente, \(que puede ser reentrante como se muestra en el ejemplo\) para obtener el bloqueo la próxima vez que entre al servicio.Para mostrar el comportamiento, el ejemplo muestra cómo un cliente y el servicio pueden enviar los mensajes entre sí utilizando un contrato dúplex.  
  
 El contrato definido es un contrato dúplex con el método `Ping` siendo implementado por el servicio y el método de devolución de llamada`Pong`siendo implementado por el cliente.Un cliente invoca el método del servidor `Ping` con un recuento del paso que inicia así la llamada.El servicio comprueba si el recuento del paso no es igual a 0 y a continuación, invoca las devoluciones de llamada el método `Pong` disminuyendo el recuento del paso.El código siguiente realiza esta operación en el ejemplo.  
  
```  
  
public void Ping(int ticks)  
{  
     Console.WriteLine("Ping: Ticks = " + ticks);  
     //Keep pinging back and forth till Ticks reaches 0.  
     if (ticks != 0)  
     {  
         OperationContext.Current.GetCallbackChannel<IPingPongCallback>().Pong((ticks - 1));  
     }  
}  
  
```  
  
 La implementación `Pong` de la devolución de llamada tiene la misma lógica que la implementación `Ping`.Es decir, comprueba si el contador no es cero y, a continuación, invoca el método `Ping` en el canal de devolución de llamada \(en este caso, es el canal que fue utilizado para enviar el mensaje `Ping` original\) con el contador disminuido en 1.El momento en que el contador llegue a 0, el método vuelve y desempaqueta de nuevo todas las respuestas a la primera llamada realizada por el cliente que inició la llamada.Esto se muestra en la implementación de devolución de llamada.  
  
```  
  
public void Pong(int ticks)  
{  
    Console.WriteLine("Pong: Ticks = " + ticks);  
    if (ticks != 0)  
    {  
        //Retrieve the Callback  Channel (in this case the Channel which was used to send the  
        //original message) and make an outgoing call until ticks reaches 0.  
        IPingPong channel = OperationContext.Current.GetCallbackChannel<IPingPong>();  
        channel.Ping((ticks - 1));  
    }  
}  
  
```  
  
 `Ping` y los métodos `Pong` son solicitud\/respuesta, lo cual significa que la primera llamada a `Ping` no vuelve hasta que la llamada `CallbackChannel<T>.Pong()`se devuelve.En el cliente, el método `Pong` no puede devolverse hasta que la siguiente llamada `Ping` que se realizó se devuelva.Dado que la devolución de llamada y el servicio deben realizar llamadas de salida de solicitud\/respuesta antes de poder responder a la solicitud pendiente, las implementaciones se deben marcar con el comportamiento de ConcurrencyMode.Reentrant.  
  
### Para configurar, compilar y ejecutar el ejemplo  
  
1.  Asegúrese de realizar los [Procedimiento de instalación única para los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar el código C\# o Visual Basic .NET Edition de la solución, siga las instrucciones de [Compilación de los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para ejecutar el ejemplo en una configuración de equipos única o cruzada, siga las instrucciones de [Ejecución de los ejemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## Demostraciones  
 Para ejecutar el ejemplo, compile los proyectos de servidor y cliente.A continuación, abra dos ventanas de comandos y cambie los directorios a los directorios \<sample\>\\CS\\Service\\bin\\debug y \<sample\>\\CS\\Client\\bin\\debug.A continuación, inicie el servicio escribiendo `service.exe` y, a continuación, invoque Client.exe con el valor inicial de pasos pasado como un argumento de entrada.Se muestra un resultado del ejemplo para 10 pasos.  
  
```  
  
Prompt>Service.exe  
ServiceHost Started. Press Enter to terminate service.  
Ping: Ticks = 10  
Ping: Ticks = 8  
Ping: Ticks = 6  
Ping: Ticks = 4  
Ping: Ticks = 2  
Ping: Ticks = 0  
  
Prompt>Client.exe 10  
Pong: Ticks = 9  
Pong: Ticks = 7  
Pong: Ticks = 5  
Pong: Ticks = 3  
Pong: Ticks = 1  
  
```  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo.Compruebe el siguiente directorio \(valor predeterminado\) antes de continuar.  
>   
>  `<>InstallDrive:\WF_WCF_Samples`  
>   
>  Si no existe este directorio, vaya a la página de [ejemplos de Windows Communication Foundation \(WCF\) y Windows Workflow Foundation \(WF\) Samples para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los ejemplos de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] y [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<unidadDeInstalación>:\WF_WCF_Samples\WCF\Basic\Services\Reentrant`  
  
## Vea también