---
title: ICorDebugILCode2::GetLocalVarSigToken (Método)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e02f44e4f581170a842a1c103ed069cb90cde79c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412303"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a>ICorDebugILCode2::GetLocalVarSigToken (Método)
[Compatible con .NET Framework 4.5.2 y versiones posteriores]  
  
 Obtiene el token de metadatos de la firma de variable local para la función que esta instancia representa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pmdSig`  
 [out] Puntero al token `mdSignature` de la firma de variable local para esta función, o `mdSignatureNil` si no hay ninguna firma (es decir, si la función no tiene variables locales).  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ICorDebugILCode2 (interfaz)](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [Interfaces de depuración](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
