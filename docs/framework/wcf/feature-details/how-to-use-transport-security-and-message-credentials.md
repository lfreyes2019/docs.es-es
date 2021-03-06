---
title: Cómo utilizar seguridad de transporte y credenciales de mensajes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f678c4713bff342cb3e788a85d7e58fc6e47820c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187613"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>Cómo utilizar seguridad de transporte y credenciales de mensajes
Protección de un servicio con credenciales de mensajes y transporte usa lo mejor de los modos de seguridad de mensajes y transporte en Windows Communication Foundation (WCF). En suma, la seguridad de la capa de transporte proporciona integridad y confidencialidad, mientras que la seguridad de la capa de mensaje proporciona una variedad de credenciales que no son posibles con mecanismos de seguridad de transporte estrictos. En este tema se muestran los pasos básicos para implementar transporte con credenciales de mensaje usando los enlaces <xref:System.ServiceModel.WSHttpBinding> y <xref:System.ServiceModel.NetTcpBinding>. Para obtener más información acerca de cómo establecer el modo de seguridad, consulte [Cómo: establecer el modo de seguridad](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
 Al establecer el modo de seguridad en `TransportWithMessageCredential`, el transporte determina el mecanismo real que proporciona la seguridad de nivel de transporte. Para HTTP, el mecanismo es Secure Sockets Layer (SSL) sobre HTTP (HTTPS); para TCP, es SSL sobre TCP o Windows.  
  
 Si el transporte es HTTP (utilizando <xref:System.ServiceModel.WSHttpBinding>), SSL sobre HTTP proporciona la seguridad de nivel de transporte. En ese caso, debe configurar el equipo que aloja el servicio con un certificado SSL enlazado a un puerto, tal y como se muestra más adelante en este tema.  
  
 Si el transporte es TCP (utilizando <xref:System.ServiceModel.NetTcpBinding>), la seguridad de nivel de transporte proporcionada es, de forma predeterminada, seguridad de Windows, o SSL sobre TCP. Al utilizar SSL sobre TCP, debe especificar el certificado mediante el método <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>, tal y como se muestra más adelante en este tema.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>Para utilizar WSHttpBinding con un certificado para la seguridad de transporte (en código)  
  
1.  Utilice la herramienta HttpCfg.exe para enlazar un certificado SSL a un puerto en el equipo. Para obtener más información, consulte [Cómo: configurar un puerto con un certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2.  Cree una instancia de la clase <xref:System.ServiceModel.WSHttpBinding> y establezca la propiedad <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> en <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
3.  Establezca la propiedad <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> en un valor apropiado. (Para obtener más información, consulte [seleccionar un tipo de credencial](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) El siguiente código usa el valor <xref:System.ServiceModel.MessageCredentialType.Certificate>.  
  
4.  Cree una instancia de la clase <xref:System.Uri> con una dirección base apropiada. Observe que la dirección debe utilizar el esquema "HTTPS" y contener el nombre real del equipo y el número de puerto al que se enlaza el certificado SSL. (De manera alternativa, puede establecer la dirección base mediante configuración.)  
  
5.  Agregue un punto de conexión de servicio mediante el método <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
6.  Cree la instancia del <xref:System.ServiceModel.ServiceHost> y llame al método <xref:System.ServiceModel.ICommunicationObject.Open%2A>, tal y como se muestra en el código siguiente.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>Para usar el NetTcpBinding con un certificado para la seguridad de transporte (en código)  
  
1.  Cree una instancia de la clase <xref:System.ServiceModel.NetTcpBinding> y establezca la propiedad <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> en <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Establezca un valor adecuado para la propiedad <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A>. El siguiente código usa el valor <xref:System.ServiceModel.MessageCredentialType.Certificate>.  
  
3.  Cree una instancia de la clase <xref:System.Uri> con una dirección base apropiada. Observe que la dirección debe utilizar el esquema "net.tcp." (De manera alternativa, puede establecer la dirección base mediante configuración.)  
  
4.  Cree la instancia de la clase <xref:System.ServiceModel.ServiceHost>.  
  
5.  Utilice el método <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> de la clase <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> para establecer explícitamente el certificado X.509 para el servicio.  
  
6.  Agregue un punto de conexión de servicio mediante el método <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
7.  Llame al método <xref:System.ServiceModel.ICommunicationObject.Open%2A>, como se muestra en el siguiente código.  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>Para utilizar NetTcpBinding con Windows para la seguridad de transporte (en código)  
  
1.  Cree una instancia de la clase <xref:System.ServiceModel.NetTcpBinding> y establezca la propiedad <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> en <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
2.  Establezca la seguridad de transporte para que utilice Windows estableciendo el <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> como <xref:System.ServiceModel.TcpClientCredentialType.Windows>. (Observe que se trata del valor predeterminado).  
  
3.  Establezca un valor adecuado para la propiedad <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A>. El siguiente código usa el valor <xref:System.ServiceModel.MessageCredentialType.Certificate>.  
  
4.  Cree una instancia de la clase <xref:System.Uri> con una dirección base apropiada. Observe que la dirección debe utilizar el esquema "net.tcp." (De manera alternativa, puede establecer la dirección base mediante configuración.)  
  
5.  Cree la instancia de la clase <xref:System.ServiceModel.ServiceHost>.  
  
6.  Utilice el método <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> de la clase <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> para establecer explícitamente el certificado X.509 para el servicio.  
  
7.  Agregue un punto de conexión de servicio mediante el método <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
8.  Llame al método <xref:System.ServiceModel.ICommunicationObject.Open%2A>, como se muestra en el siguiente código.  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>Uso de la configuración  
  
#### <a name="to-use-the-wshttpbinding"></a>Para usar el WSHttpBinding  
  
1.  Configure el equipo con un certificado SSL enlazado a un puerto. (Para obtener más información, consulte [Cómo: configurar un puerto con un certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)). No es necesario establecer una <`transport`> valor del elemento con esta configuración.  
  
2.  Especifique el tipo de credencial de cliente para la seguridad del nivel de mensaje. El ejemplo siguiente se establece la `clientCredentialType` atributo de la <`message`> elemento para `UserName`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>Para usar el NetTcpBinding con un certificado para la seguridad de transporte  
  
1.  Para SSL sobre TCP, debe especificar explícitamente el certificado en el elemento `<behaviors>`. El siguiente ejemplo especifica un certificado por su emisor en la ubicación de almacén predeterminada (equipo local y almacenes personales).  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  Agregar un [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) a la sección de enlaces  
  
3.  Agregue un elemento de enlace y establezca un valor apropiado para el atributo `name`.  
  
4.  Agregar un <`security`> y establezca el `mode` atributo `TransportWithMessageCredential`.  
  
5.  Agregar un <`message>` y establezca el `clientCredentialType` atributo en un valor adecuado.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>Para utilizar NetTcpBinding con Windows para la seguridad de transporte  
  
1.  Agregar un [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) a la sección de enlaces  
  
2.  Agregar un <`binding`> y establezca el `name` atributo en un valor adecuado.  
  
3.  Agregar un <`security`> y establezca el `mode` atributo `TransportWithMessageCredential`.  
  
4.  Agregar un <`transport`> y establezca el `clientCredentialType` atributo `Windows`.  
  
5.  Agregar un <`message`> y establezca el `clientCredentialType` atributo en un valor adecuado. El siguiente código establece el valor para un certificado.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Cómo establecer el modo de seguridad](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [Seguridad de servicios](../../../../docs/framework/wcf/securing-services.md)  
 [Protección de servicios y clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
