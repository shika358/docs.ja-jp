---
title: "IManagedObject::GetObjectIdentity メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IManagedObject.GetObjectIdentity
api_location: mscoree.dll
api_type: COM
f1_keywords: GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c0dabfca147b203c3bcf93a362e6670ae295338
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="4e488-102">IManagedObject::GetObjectIdentity メソッド</span><span class="sxs-lookup"><span data-stu-id="4e488-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="4e488-103">この管理オブジェクトの id を取得します。</span><span class="sxs-lookup"><span data-stu-id="4e488-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e488-104">構文</span><span class="sxs-lookup"><span data-stu-id="4e488-104">Syntax</span></span>  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e488-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4e488-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="4e488-106">[out]オブジェクトが存在するプロセスの GUID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4e488-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="4e488-107">[out]オブジェクトのアプリケーション ドメインの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4e488-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="4e488-108">[out]COM クラシック v-table からのオブジェクトのインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4e488-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e488-109">コメント</span><span class="sxs-lookup"><span data-stu-id="4e488-109">Remarks</span></span>  
 <span data-ttu-id="4e488-110">マネージ オブジェクトの id には、COM クラシック v-テーブル内の GUID のプロセス、アプリケーション ドメイン ID、およびそのオブジェクトのインデックスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4e488-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e488-111">要件</span><span class="sxs-lookup"><span data-stu-id="4e488-111">Requirements</span></span>  
 <span data-ttu-id="4e488-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4e488-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e488-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4e488-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e488-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="4e488-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e488-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e488-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e488-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e488-116">See Also</span></span>  
 [<span data-ttu-id="4e488-117">IManagedObject インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4e488-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)