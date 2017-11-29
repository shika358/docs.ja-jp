---
title: "ISymUnmanagedWriter2::DefineLocalVariable2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2.DefineLocalVariable2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 595cc3d8c503a5a6b2cbcb6665f7ff8aff5044d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="267f8-102">ISymUnmanagedWriter2::DefineLocalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="267f8-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="267f8-103">現在の構文のスコープの変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="267f8-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="267f8-104">このメソッドをスコープ全体で複数のホームを持つものと同じ名前の変数に対して複数回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="267f8-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="267f8-105">ここでは、ただしの値、`startOffset`と`endOffset`パラメーターと重なってはなりません。</span><span class="sxs-lookup"><span data-stu-id="267f8-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="267f8-106">構文</span><span class="sxs-lookup"><span data-stu-id="267f8-106">Syntax</span></span>  
  
```  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="267f8-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="267f8-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="267f8-108">[in]ローカル変数の名前。</span><span class="sxs-lookup"><span data-stu-id="267f8-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="267f8-109">[in]ローカル変数の属性。</span><span class="sxs-lookup"><span data-stu-id="267f8-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="267f8-110">[in]署名のメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="267f8-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="267f8-111">[in]アドレスの種類。</span><span class="sxs-lookup"><span data-stu-id="267f8-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="267f8-112">[in]パラメーター指定の最初のアドレス。</span><span class="sxs-lookup"><span data-stu-id="267f8-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="267f8-113">[in]パラメーター指定の 2 番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="267f8-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="267f8-114">[in]パラメーター指定の 3 番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="267f8-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="267f8-115">[in]変数の開始オフセット。</span><span class="sxs-lookup"><span data-stu-id="267f8-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="267f8-116">このパラメーターは省略できます。</span><span class="sxs-lookup"><span data-stu-id="267f8-116">This parameter is optional.</span></span> <span data-ttu-id="267f8-117">0 の場合、このパラメーターは無視され、スコープ全体で変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="267f8-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="267f8-118">を 0 以外の値がある場合、変数は、現在のスコープのオフセット内にあります。</span><span class="sxs-lookup"><span data-stu-id="267f8-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="267f8-119">[in]変数の終了オフセット。</span><span class="sxs-lookup"><span data-stu-id="267f8-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="267f8-120">このパラメーターは省略できます。</span><span class="sxs-lookup"><span data-stu-id="267f8-120">This parameter is optional.</span></span> <span data-ttu-id="267f8-121">0 の場合、このパラメーターは無視され、スコープ全体で変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="267f8-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="267f8-122">を 0 以外の値がある場合、変数は、現在のスコープのオフセット内にあります。</span><span class="sxs-lookup"><span data-stu-id="267f8-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="267f8-123">戻り値</span><span class="sxs-lookup"><span data-stu-id="267f8-123">Return Value</span></span>  
 <span data-ttu-id="267f8-124">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="267f8-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="267f8-125">要件</span><span class="sxs-lookup"><span data-stu-id="267f8-125">Requirements</span></span>  
 <span data-ttu-id="267f8-126">**ヘッダー:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="267f8-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="267f8-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="267f8-127">See Also</span></span>  
 [<span data-ttu-id="267f8-128">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="267f8-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="267f8-129">DefineLocalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="267f8-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)