---
title: '&lt;endpointExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: 3883a23c679abc83d7cfe9011b7cdb7e4154adfe
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146451"
---
# <a name="ltendpointextensionsgt"></a>&lt;endpointExtensions&gt;
En esta sección se registra un nuevo punto de conexión estándar en la sección de extensiones en un archivo de configuración de un equipo o aplicación. Puede agregar un extremo estándar a esta colección usando la palabra clave `add` y estableciendo el atributo `type` del elemento en el tipo de extremo, así como el atributo `name` en el nombre del extremo estándar.  
  
 El ejemplo siguiente usa el elemento `add`, así como el atributo `name` para agregar un extremo estándar a la sección `<endpointExtensions>` del archivo de configuración.  
  
```xml  
<system.serviceModel>
  <extensions>
    <endpointExtensions>
      <add name="udpDiscoveryEndpoint"
           type="System.Discovery.UdpEndpointCollectionElement, System.Discovery.dll, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Una vez registrado el punto de conexión estándar, puede usarlo como se muestra en el siguiente ejemplo. En el [ \<punto de conexión >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elemento, el `kind` atributo especifica el tipo de punto de conexión estándar que se ha registrado en el `<endpointExtensions>` sección. El `endpointConfiguration` atributo será idéntico a la `name` atributo del elemento de configuración del punto de conexión estándar en el `<standardEndpoints>` sección.  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Service1">
      <endpoint kind="udpDiscoveryEndpoint"
                endpointConfiguration="udpConfig" />
    </service>
  </services>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="udpConfig"
                        multicastAddress="soap.udp://239.255.255.250:3703"
                        ... />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
