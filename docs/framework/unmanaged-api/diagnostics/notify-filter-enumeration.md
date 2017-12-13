---
title: "NOTIFY_FILTER (Enumeración)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: NOTIFY_FILTER
api_location: diasymreader.dll
api_type: COM
f1_keywords: NOTIFY_FILTER
helpviewer_keywords: NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9db03458aab60d28efe52edfd9830da7862fcb8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="notifyfilter-enumeration"></a><span data-ttu-id="9b870-102">NOTIFY_FILTER (Enumeración)</span><span class="sxs-lookup"><span data-stu-id="9b870-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="9b870-103">Identifica las devoluciones de llamada para las funciones del depurador.</span><span class="sxs-lookup"><span data-stu-id="9b870-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="9b870-104">Para obtener más información, consulte el [INotifySource2:: SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="9b870-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b870-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9b870-105">Syntax</span></span>  
  
```  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a><span data-ttu-id="9b870-106">Miembros</span><span class="sxs-lookup"><span data-stu-id="9b870-106">Members</span></span>  
  
|<span data-ttu-id="9b870-107">Miembro</span><span class="sxs-lookup"><span data-stu-id="9b870-107">Member</span></span>|<span data-ttu-id="9b870-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="9b870-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="9b870-109">Indica que la [INotifySink2:: OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) debe invocar el método.</span><span class="sxs-lookup"><span data-stu-id="9b870-109">Indicates that the [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="9b870-110">Indica que la [INotifySink2:: OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) debe invocar el método.</span><span class="sxs-lookup"><span data-stu-id="9b870-110">Indicates that the [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="9b870-111">Indica que la [INotifySink2:: OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) debe invocar el método.</span><span class="sxs-lookup"><span data-stu-id="9b870-111">Indicates that the [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="9b870-112">Indica que la [INotifySink2:: OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) debe invocar el método.</span><span class="sxs-lookup"><span data-stu-id="9b870-112">Indicates that the [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="9b870-113">Indica que todos los [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) se deben invocar métodos.</span><span class="sxs-lookup"><span data-stu-id="9b870-113">Indicates that all of the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="9b870-114">Activa todas las notificaciones existentes y futuras.</span><span class="sxs-lookup"><span data-stu-id="9b870-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="9b870-115">Indica que no se debe invocar ningún método de notificación.</span><span class="sxs-lookup"><span data-stu-id="9b870-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b870-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b870-116">Requirements</span></span>  
 <span data-ttu-id="9b870-117">**Encabezado:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="9b870-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b870-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="9b870-118">See Also</span></span>  
 [<span data-ttu-id="9b870-119">Enumeraciones de almacén de símbolos de diagnósticos</span><span class="sxs-lookup"><span data-stu-id="9b870-119">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)