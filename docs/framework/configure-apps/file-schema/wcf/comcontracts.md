---
title: '&lt;comContracts&gt;'
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 26f17a331d69c38d720fcafe65c76f50c67def09
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150791"
---
# <a name="ltcomcontractsgt"></a>&lt;comContracts&gt;
La sección de configuración `comContracts` contiene elementos que le permiten especificar varias propiedades de un contrato de servicios de la integración de COM+.  
  
## <a name="specifying-namespace-and-contract"></a>Especificar espacio de nombres y contrato  
 Contratos de servicio de integración de COM + están restringidos actualmente a la `http://tempuri.org` espacio de nombres y nombre de contrato se deriva de la interfaz COM de apoyo. Puede, sin embargo, especificar alternativas mediante la sección `comContracts` en el archivo de configuración.  
  
 Por ejemplo, puede utilizar la configuración siguiente para especificar el espacio de nombres y nombre del contrato del contrato de servicios, así como una opción para exigir el uso en enlaces con sesión.  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 Cuando se inicializa el servicio, los espacios de nombres y nombres del contrato especificados se aplican a las descripciones de servicio generadas.  
  
 Cuando esta sección está vacía, la inicialización del servicio aplica un espacio de nombres y un nombre de contrato predeterminados tomados del identificador de la interfaz COM de apoyo.  
  
 Además, puede usar el [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elemento para especificar los métodos COM + que se exponen cuando la interfaz en un componente COM + se expone como un servicio Web. También puede usar el [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) para especificar tipos con persistencia utilizados en integración. Por último, puede usar el [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) elemento para incluir define tipos usuario (UDT) que deben incluirse en el contrato de servicio.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [\<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [\<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [\<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [\<comContract >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [Integración en aplicaciones COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Cómo: Configurar el servicio COM +](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
