---
title: "CorLaunchApplication 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type: COM
f1_keywords: CorLaunchApplication
helpviewer_keywords: CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d6246ab600438e2237dcbe531d9d7641c0897d81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="ff993-102">CorLaunchApplication 関数</span><span class="sxs-lookup"><span data-stu-id="ff993-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="ff993-103">指定したネットワーク パスのアプリケーションを、指定したマニフェストとその他のアプリケーション データを使用して起動します。</span><span class="sxs-lookup"><span data-stu-id="ff993-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="ff993-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="ff993-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff993-105">構文</span><span class="sxs-lookup"><span data-stu-id="ff993-105">Syntax</span></span>  
  
```  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff993-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff993-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="ff993-107">[in]値、 [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md)アプリケーションの起動は、ホストの種類を指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="ff993-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="ff993-108">[in]起動されるアプリケーションの完全名。</span><span class="sxs-lookup"><span data-stu-id="ff993-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="ff993-109">[in]アプリケーションのマニフェストのパスの数。</span><span class="sxs-lookup"><span data-stu-id="ff993-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="ff993-110">[in]それぞれを指定しますが起動されるアプリケーションのマニフェストへのパス、文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="ff993-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="ff993-111">[in]起動されるアプリケーションのライセンス認証データ項目の数。</span><span class="sxs-lookup"><span data-stu-id="ff993-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="ff993-112">[in]起動されるアプリケーションのライセンス認証データ項目は、それぞれが、文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="ff993-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="ff993-113">[out]アプリケーションが読み込まれているプロセスに関する情報へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ff993-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff993-114">要件</span><span class="sxs-lookup"><span data-stu-id="ff993-114">Requirements</span></span>  
 <span data-ttu-id="ff993-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ff993-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff993-116">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ff993-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff993-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff993-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff993-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff993-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff993-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff993-119">See Also</span></span>  
 [<span data-ttu-id="ff993-120">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="ff993-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)