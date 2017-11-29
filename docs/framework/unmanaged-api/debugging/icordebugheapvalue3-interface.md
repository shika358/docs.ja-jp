---
title: "ICorDebugHeapValue3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3
helpviewer_keywords: ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5531689a3a4ba66fddfc98cadec7dc8d51c8629a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="fed6b-102">ICorDebugHeapValue3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fed6b-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="fed6b-103">オブジェクトのモニター ロック プロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="fed6b-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="fed6b-104">このインターフェイスは、ICorDebugHeapValue および ICorDebugHeapValue2 インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="fed6b-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fed6b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="fed6b-105">Methods</span></span>  
  
|<span data-ttu-id="fed6b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="fed6b-106">Method</span></span>|<span data-ttu-id="fed6b-107">説明</span><span class="sxs-lookup"><span data-stu-id="fed6b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fed6b-108">GetThreadOwningMonitorLock メソッド</span><span class="sxs-lookup"><span data-stu-id="fed6b-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="fed6b-109">このオブジェクトのモニター ロックを所有するマネージ スレッドを返します。</span><span class="sxs-lookup"><span data-stu-id="fed6b-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="fed6b-110">GetMonitorEventWaitList メソッド</span><span class="sxs-lookup"><span data-stu-id="fed6b-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="fed6b-111">モニター ロックに関連付けられているイベントでは、キュー内のスレッドの順序付きリストを提供します。</span><span class="sxs-lookup"><span data-stu-id="fed6b-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fed6b-112">コメント</span><span class="sxs-lookup"><span data-stu-id="fed6b-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fed6b-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="fed6b-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fed6b-114">要件</span><span class="sxs-lookup"><span data-stu-id="fed6b-114">Requirements</span></span>  
 <span data-ttu-id="fed6b-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fed6b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fed6b-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fed6b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fed6b-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fed6b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fed6b-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fed6b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fed6b-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="fed6b-119">See Also</span></span>  
 [<span data-ttu-id="fed6b-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fed6b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fed6b-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="fed6b-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)