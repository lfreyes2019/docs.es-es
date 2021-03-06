---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 84e304f3dedcbd785d6238e6cb5eb142c288b995
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149710"
---
# <a name="binding"></a>Enlaces
Enlace wmi  
  
## <a name="syntax"></a>Sintaxis  
  
```csharp
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a>Métodos  
 La clase Binding no define ningún método.  
  
## <a name="properties"></a>Propiedades  
 La clase Binding tiene las propiedades siguientes.  
  
### <a name="bindingelements"></a>BindingElements  
 Tipo de datos: Matriz de BindingElement  
  
 Tipo de acceso: De sólo lectura  
  
 La colección de elementos de enlace implementada por el enlace.  
  
### <a name="closetimeout"></a>CloseTimeout  
 Tipo de datos: datetime  
  
 Tipo de acceso: De sólo lectura  
  
 El intervalo de tiempo proporcionado para que se complete una operación de cierre.  
  
### <a name="name"></a>nombre  
 Tipo de datos: cadena  
  
 Tipo de acceso: De sólo lectura  
  
 Nombre del enlace.  
  
### <a name="namespace"></a>Espacio de nombres  
 Tipo de datos: cadena  
  
 Tipo de acceso: De sólo lectura  
  
 Espacio de nombres XML del enlace.  
  
### <a name="opentimeout"></a>OpenTimeout  
 Tipo de datos: datetime  
  
 Tipo de acceso: De sólo lectura  
  
 El intervalo de tiempo proporcionado para que se complete una operación de apertura.  
  
### <a name="receivetimeout"></a>ReceiveTimeout  
 Tipo de datos: datetime  
  
 Tipo de acceso: De sólo lectura  
  
 El intervalo de tiempo proporcionado para que se complete una operación de recepción.  
  
### <a name="scheme"></a>Scheme  
 Tipo de datos: cadena  
  
 Tipo de acceso: De sólo lectura  
  
 El esquema de transporte de URI utilizado por los generadores de canales y de agentes de escucha creados por el enlace.  
  
### <a name="sendtimeout"></a>SendTimeout  
 Tipo de datos: datetime  
  
 Tipo de acceso: De sólo lectura  
  
 El intervalo de tiempo proporcionado para que se complete una operación de envío.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Se declara en Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espacio de nombres|Se define en root\ServiceModel|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Channels.Binding>
