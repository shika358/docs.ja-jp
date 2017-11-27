---
title: "ICorDebugGenericValue::GetValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGenericValue.GetValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2432d79c6f17c7374d2beb400e93ae4088a8b1ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="03a81-102">ICorDebugGenericValue::GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="03a81-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="03a81-103">指定されたバッファーには、このジェネリックの値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="03a81-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03a81-104">構文</span><span class="sxs-lookup"><span data-stu-id="03a81-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03a81-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="03a81-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="03a81-106">[out]ICorDebugGenericValue オブジェクトによって表される値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="03a81-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="03a81-107">値には、単純型または参照型 (つまり、ポインター) があります。</span><span class="sxs-lookup"><span data-stu-id="03a81-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03a81-108">要件</span><span class="sxs-lookup"><span data-stu-id="03a81-108">Requirements</span></span>  
 <span data-ttu-id="03a81-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="03a81-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03a81-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03a81-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03a81-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03a81-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03a81-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03a81-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>