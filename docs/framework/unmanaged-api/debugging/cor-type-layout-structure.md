---
title: COR_TYPE_LAYOUT (Estructura)
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b88a7b0672e15097c60afbe069ce5b78bd5c38d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408149"
---
# <a name="cortypelayout-structure"></a>COR_TYPE_LAYOUT (Estructura)
Proporciona información sobre la distribución de un objeto en la memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|`parentID`|El identificador del tipo primario para este tipo. Se usará el identificador de tipo NULL (símbolo1 = 0, símbolo2 = 0) si el identificador de tipo corresponde a <xref:System.Object?displayProperty=nameWithType>.|  
|`objectSize`|El tamaño de la base de un objeto de este tipo. Este es el tamaño total para los objetos de tamaño no variable.|  
|`numFields`|El número de campos que se incluyen en los objetos de este tipo.|  
|`boxOffset`|Si este tipo es una conversión boxing, el principio de desplazamiento de campos de un objeto. Este campo es válida únicamente para los tipos de valor como tipos primitivos y las estructuras.|  
|`type`|CorElementType al que pertenece este tipo.|  
  
## <a name="remarks"></a>Comentarios  
 Si `numFields` es mayor que cero, se puede llamar a la [icordebugprocess5:: Gettypefields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) método para obtener información sobre los campos de este tipo. Si `type` es `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, o `ELEMENT_TYPE_SZARRAY`, el tamaño de los objetos de este tipo es variable y se puede pasar el [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) estructura especificada en el [icordebugprocess5:: Getarraylayout ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) (método).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Estructuras de depuración](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Depuración](../../../../docs/framework/unmanaged-api/debugging/index.md)
