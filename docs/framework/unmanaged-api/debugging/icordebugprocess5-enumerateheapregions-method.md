---
title: ICorDebugProcess5::EnumerateHeapRegions (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d48d8e7b699f411ec45cf1b5d9810c23583b045e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423122"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>ICorDebugProcess5::EnumerateHeapRegions (Método)
Obtiene un enumerador para los intervalos de memoria del montón administrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppRegions`  
 [out] Un puntero a la dirección de un [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objeto de interfaz que es un enumerador para los intervalos de memoria en el que los objetos residan en el montón administrado.  
  
## <a name="remarks"></a>Comentarios  
 Antes de llamar a la `ICorDebugProcess5::EnumerateHeapRegions` método, debe llamar a la [icordebugprocess5:: Getgcheapinformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) (método) y examine el valor de la `areGCStructuresValid` campo devuelto [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) objeto para asegurarse de que el montón de elementos no utilizados en su estado actual es enumerable. Además, el `ICorDebugProcess5::EnumerateHeapRegions` método `E_FAIL` si adjunta demasiado pronto en la duración del proceso, antes que la memoria se crean las regiones.  
  
 Este método se garantiza para enumerar todas las regiones de memoria que pueden contener objetos administrados, pero no garantiza que los objetos administrados que residen realmente en esas regiones. El [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objeto de colección puede incluir las regiones de memoria reservada o vacío.  
  
 El [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objeto de interfaz es un enumerador estándar que se deriva de la interfaz de ICorDebugEnum que permite enumerar [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objetos. Cada [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objeto proporciona información acerca del intervalo de memoria de un segmento en particular, junto con la generación de los objetos de ese segmento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ICorDebugProcess5 (interfaz)](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Interfaces de depuración](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
