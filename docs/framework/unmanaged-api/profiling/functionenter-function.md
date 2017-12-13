---
title: "FunctionEnter (Función)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter
helpviewer_keywords: FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0cd98e6db0f400d022fe0af4e96336616cbb7183
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter-function"></a><span data-ttu-id="54ecd-102">FunctionEnter (Función)</span><span class="sxs-lookup"><span data-stu-id="54ecd-102">FunctionEnter Function</span></span>
<span data-ttu-id="54ecd-103">Notifica al generador de perfiles que se pasan a una función de control.</span><span class="sxs-lookup"><span data-stu-id="54ecd-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54ecd-104">El `FunctionEnter` función está desusada en la versión 2.0 de .NET Framework y su uso, le cobrará una reducción del rendimiento.</span><span class="sxs-lookup"><span data-stu-id="54ecd-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="54ecd-105">Use la [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) funcione en su lugar.</span><span class="sxs-lookup"><span data-stu-id="54ecd-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54ecd-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="54ecd-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54ecd-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="54ecd-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="54ecd-108">[in] El identificador de la función a la que se pasa el control.</span><span class="sxs-lookup"><span data-stu-id="54ecd-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54ecd-109">Comentarios</span><span class="sxs-lookup"><span data-stu-id="54ecd-109">Remarks</span></span>  
 <span data-ttu-id="54ecd-110">El `FunctionEnter` función es una devolución de llamada; debe implementar.</span><span class="sxs-lookup"><span data-stu-id="54ecd-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="54ecd-111">La implementación debe utilizar el `__declspec`(`naked`) el atributo de clase de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="54ecd-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="54ecd-112">El motor de ejecución no guardan los registros antes de llamar a esta función.</span><span class="sxs-lookup"><span data-stu-id="54ecd-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="54ecd-113">En la entrada, debe guardar todos los registros que utilice, incluidos los de la unidad de punto flotante (FPU).</span><span class="sxs-lookup"><span data-stu-id="54ecd-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="54ecd-114">Al salir, debe restablecer la pila desactivando todos los parámetros que se han insertados por el llamador.</span><span class="sxs-lookup"><span data-stu-id="54ecd-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="54ecd-115">La implementación de `FunctionEnter` no debe bloquearse porque retrasará la recolección de elementos.</span><span class="sxs-lookup"><span data-stu-id="54ecd-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="54ecd-116">La implementación no debería intentar una recolección porque la pila no puede estar en un estado compatible con la colección de elementos no utilizados.</span><span class="sxs-lookup"><span data-stu-id="54ecd-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="54ecd-117">Si se intenta realizar una recolección, el tiempo de ejecución se bloqueará hasta que `FunctionEnter` devuelve.</span><span class="sxs-lookup"><span data-stu-id="54ecd-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="54ecd-118">Además, la `FunctionEnter` función no debe llamar a código administrado o en modo alguno provocar una asignación de memoria administrada.</span><span class="sxs-lookup"><span data-stu-id="54ecd-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54ecd-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="54ecd-119">Requirements</span></span>  
 <span data-ttu-id="54ecd-120">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54ecd-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54ecd-121">**Encabezado:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="54ecd-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="54ecd-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54ecd-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54ecd-123">**Versiones de .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="54ecd-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54ecd-124">Vea también</span><span class="sxs-lookup"><span data-stu-id="54ecd-124">See Also</span></span>  
 [<span data-ttu-id="54ecd-125">FunctionEnter2 (función)</span><span class="sxs-lookup"><span data-stu-id="54ecd-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="54ecd-126">FunctionLeave2 (función)</span><span class="sxs-lookup"><span data-stu-id="54ecd-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="54ecd-127">FunctionTailcall2 (función)</span><span class="sxs-lookup"><span data-stu-id="54ecd-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="54ecd-128">SetEnterLeaveFunctionHooks2 (método)</span><span class="sxs-lookup"><span data-stu-id="54ecd-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="54ecd-129">Funciones estáticas globales de generación de perfiles</span><span class="sxs-lookup"><span data-stu-id="54ecd-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)