---
title: Procedimiento Especificar un enlace de servicio en la configuración
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 1d9a6d0a556613576a14c600aa72d3f4524cdc3e
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029637"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Procedimiento Especificar un enlace de servicio en la configuración
En este ejemplo, se define un contrato `ICalculator` para un servicio de calculadora básico; el servicio se implementa en la clase `CalculatorService` y, después, su punto de conexión se configura en el archivo Web.config, donde se especifica que el servicio usa <xref:System.ServiceModel.BasicHttpBinding>. Para obtener una descripción de cómo configurar este servicio mediante código en lugar de una configuración, vea [Cómo: Especificar un enlace de servicio en el código](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).  
  
 Normalmente es el mejor procedimiento para especificar el enlace y la información de dirección de forma declarativa en configuración en lugar de hacerlo de forma imperativa en código. Normalmente, no resulta muy práctico definir los extremos en el código ya que los enlaces y las direcciones de un servicio implementado son, por lo general, diferentes de los utilizados durante el desarrollo del servicio. Más generalmente, manteniendo el enlace y la información de dirección fuera del código permite cambiarlos sin tener que recompilar o implementar la aplicación.  
  
 Todos los pasos de configuración siguientes se pueden realizar utilizando el [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Para la copia de origen de este ejemplo, vea [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Para especificar BasicHttpBinding para utilizarlo para configurar el servicio  
  
1.  Defina un contrato de servicios para el tipo de servicio.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2.  Implemente el contrato de servicios en una clase de servicio.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    >  La información de dirección o enlace no se especifica dentro de la implementación del servicio. Por lo tanto, el código no tiene que escribirse para recuperar esa información del archivo de configuración.  
  
3.  Cree un archivo Web.config para configurar un punto de conexión para `CalculatorService` que utiliza <xref:System.ServiceModel.WSHttpBinding>.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <!-- Leave the address blank to be populated by default -->  
            <!-- from the hosting environment,in this case IIS, so -->  
            <!-- the address will just be that of the IIS Virtual -->  
            <!-- Directory. -->  
                address=""   
            <!-- Specify the binding type -->  
                binding="wsHttpBinding"  
            <!-- Specify the binding configuration name for that -->  
            <!-- binding type. This is optional but useful if you -->  
            <!-- want to modify the properties of the binding. -->  
            <!-- The bindingConfiguration name Binding1 is defined -->  
            <!-- below in the bindings element. -->  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <!-- Binding property values can be modified here. -->  
              <!-- See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  Cree un archivo Service.svc que contenga la línea siguiente y colóquelo en su directorio virtual de Internet Information Services (IIS).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Para modificar los valores predeterminados de las propiedades de enlace  
  
1.  Para modificar uno de los valores de propiedad predeterminados de la <xref:System.ServiceModel.WSHttpBinding>, crear un nuevo nombre de configuración de enlace - `<binding name="Binding1">` : dentro del [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento y establezca los nuevos valores para los atributos de la enlace en este elemento de enlace. Por ejemplo, para cambiar los valores predeterminados de abrir y cerrar el tiempo de espera de 1 minuto a 2 minutos, agregue el siguiente al archivo de configuración.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Utilización de enlaces para configurar servicios y clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Especificación de una dirección de punto de conexión](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
