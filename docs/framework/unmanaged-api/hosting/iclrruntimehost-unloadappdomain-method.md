---
title: "ICLRRuntimeHost::UnloadAppDomain メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.UnloadAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec5e32ccc9311f2f89252c0db5849304f2186de2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="0e4fa-102">ICLRRuntimeHost::UnloadAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="0e4fa-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="0e4fa-103">マネージ アンロード<xref:System.AppDomain>指定した数値識別子に対応します。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e4fa-104">構文</span><span class="sxs-lookup"><span data-stu-id="0e4fa-104">Syntax</span></span>  
  
```  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e4fa-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0e4fa-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="0e4fa-106">[in]アプリケーション ドメインをアンロードの数値識別子。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="0e4fa-107">[in]`true`を共通言語ランタイム (CLR) がアプリケーション ドメインをアンロードする前に、アプリケーションの現在のスレッドの実行が終了するまで待機する必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e4fa-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0e4fa-108">Return Value</span></span>  
  
|<span data-ttu-id="0e4fa-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e4fa-109">HRESULT</span></span>|<span data-ttu-id="0e4fa-110">説明</span><span class="sxs-lookup"><span data-stu-id="0e4fa-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e4fa-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e4fa-111">S_OK</span></span>|<span data-ttu-id="0e4fa-112">`UnloadAppDomain`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="0e4fa-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0e4fa-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0e4fa-114">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0e4fa-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0e4fa-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0e4fa-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-116">The call timed out.</span></span>|  
|<span data-ttu-id="0e4fa-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e4fa-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0e4fa-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0e4fa-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0e4fa-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0e4fa-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0e4fa-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e4fa-121">E_FAIL</span></span>|<span data-ttu-id="0e4fa-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0e4fa-123">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0e4fa-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e4fa-125">コメント</span><span class="sxs-lookup"><span data-stu-id="0e4fa-125">Remarks</span></span>  
 <span data-ttu-id="0e4fa-126">呼び出して、現在のスレッドが実行されているアプリケーション ドメインの数値識別子を取得できます[GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="0e4fa-127">この識別子に対応する、<xref:System.AppDomain.Id%2A>マネージ プロパティ<xref:System.AppDomain>型です。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e4fa-128">要件</span><span class="sxs-lookup"><span data-stu-id="0e4fa-128">Requirements</span></span>  
 <span data-ttu-id="0e4fa-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e4fa-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0e4fa-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e4fa-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0e4fa-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e4fa-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e4fa-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e4fa-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e4fa-133">See Also</span></span>  
 [<span data-ttu-id="0e4fa-134">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e4fa-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)