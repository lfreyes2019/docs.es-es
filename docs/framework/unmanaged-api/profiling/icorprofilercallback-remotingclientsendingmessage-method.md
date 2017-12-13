---
title: "ICorProfilerCallback::RemotingClientSendingMessage (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientSendingMessage
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a77acb736cec02da6839335e981016469eeb42b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="7361d-102">ICorProfilerCallback::RemotingClientSendingMessage (Método)</span><span class="sxs-lookup"><span data-stu-id="7361d-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="7361d-103">Notifica al generador de perfiles que el cliente envía una solicitud al servidor.</span><span class="sxs-lookup"><span data-stu-id="7361d-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7361d-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7361d-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7361d-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7361d-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="7361d-106">[in] Un valor que se corresponde con el valor proporcionado en [ICorProfilerCallback:: RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) en estas condiciones:</span><span class="sxs-lookup"><span data-stu-id="7361d-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="7361d-107">Las cookies GUID de comunicación remota están activas.</span><span class="sxs-lookup"><span data-stu-id="7361d-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="7361d-108">El canal consigue transmitir el mensaje.</span><span class="sxs-lookup"><span data-stu-id="7361d-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="7361d-109">Las cookies de GUID están activas en el proceso de servidor.</span><span class="sxs-lookup"><span data-stu-id="7361d-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="7361d-110">Esto permite la fácil emparejamiento de las llamadas remotas y la creación de una pila de llamadas lógica.</span><span class="sxs-lookup"><span data-stu-id="7361d-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="7361d-111">[in] Un valor que es `true` si la llamada es asincrónica; en caso contrario, `false`.</span><span class="sxs-lookup"><span data-stu-id="7361d-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7361d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7361d-112">Requirements</span></span>  
 <span data-ttu-id="7361d-113">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7361d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7361d-114">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7361d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7361d-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7361d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7361d-116">**Versiones de .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7361d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7361d-117">Vea también</span><span class="sxs-lookup"><span data-stu-id="7361d-117">See Also</span></span>  
 [<span data-ttu-id="7361d-118">ICorProfilerCallback (interfaz)</span><span class="sxs-lookup"><span data-stu-id="7361d-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)