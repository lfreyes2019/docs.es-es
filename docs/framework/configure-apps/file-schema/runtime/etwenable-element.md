---
title: '&lt;etwEnable&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6ea2f8a32a18dfce6be54ce52ce8fef4abf92ce
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610780"
---
# <a name="ltetwenablegt-element"></a>&lt;etwEnable&gt; elemento
Especifica si se debe habilitar Seguimiento de eventos para Windows (ETW) para los eventos de Common Language Runtime.  
  
 \<Configuración > elemento  
\<en tiempo de ejecución > elemento  
\<etwEnabled >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|enabled|Atributo necesario.<br /><br /> Especifica si se debe habilitar ETW.|  
  
## <a name="enabled-attribute"></a>Atributo enabled  
  
|Valor|Descripción|  
|-----------|-----------------|  
|true|Habilitar ETW. Este es el valor predeterminado para las versiones de Windows empezando con los sistemas operativos Windows Vista y Windows Server 2008.|  
|False|Deshabilitar ETW. Este es el valor predeterminado para las versiones anteriores de Windows.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`configuration`|Elemento raíz de cada archivo de configuración usado por las aplicaciones de Common Language Runtime y .NET Framework.|  
|`runtime`|Contiene información del enlace del ensamblado y de la recolección de elementos no utilizados.|  
  
## <a name="remarks"></a>Comentarios  
 Comenzando con Windows Vista, ETW está habilitado de forma predeterminada. Utilice este elemento para deshabilitar ETW para una aplicación. En versiones anteriores de Windows, use este elemento para habilitar ETW para una aplicación.  
  
> [!NOTE]
>  Puede ser habilitado o deshabilitado globalmente en un servidor mediante una configuración del registro ETW. Consulte [controlar el registro de .NET Framework](../../../../../docs/framework/performance/controlling-logging.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo habilitar el seguimiento de ETW para una aplicación.  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Vea también  
- [Esquema de la configuración de Common Language Runtime](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Esquema de los archivos de configuración](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [Controlar el registro de .NET Framework](../../../../../docs/framework/performance/controlling-logging.md)
