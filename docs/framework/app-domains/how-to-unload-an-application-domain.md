---
title: "方法 : アプリケーション ドメインをアンロードする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 741ddf7c394e1c310e368fe338f71d02a0d4736d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-unload-an-application-domain"></a>方法 : アプリケーション ドメインをアンロードする
アプリケーション ドメインの使用が完了したら、<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> メソッドを使用してアプリケーション ドメインをアンロードします。 **Unload** メソッドは、指定したアプリケーション ドメインを正常にシャットダウンします。 アンロード プロセス中は、新たなスレッドがアプリケーション ドメインにアクセスすることはできません。また、アプリケーション ドメイン固有のデータ構造はすべて解放されます。  
  
 アプリケーション ドメインに読み込まれたアセンブリは、削除され、以後は使用できません。 アプリケーション ドメイン内のアセンブリが、ドメインに中立である場合、アセンブリのデータは、プロセス全体がシャットダウンされるまでメモリに残ります。 プロセス全体をシャットダウンする以外に、ドメインに中立なアセンブリをアンロードする機構はありません。 アプリケーション ドメインのアンロード要求が機能しない場合は、<xref:System.CannotUnloadAppDomainException> が生成されます。  
  
 次の例では、`MyDomain` という新しいアプリケーション ドメインを作成し、情報をコンソールに出力してから、アプリケーション ドメインをアンロードします。 このコードは、アンロードされたアプリケーション ドメインのフレンドリ名をコンソールに出力しようとすることに注意してください。 このアクションでは、例外が生成されます。この例外は、プログラムの最後の try ステートメントまたは catch ステートメントで処理されます。  
  
## <a name="example"></a>例  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>参照  
 [アプリケーション ドメインを使用したプログラミング](http://msdn.microsoft.com/library/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [方法: アプリケーション ドメインを作成する](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 [アプリケーション ドメインの使用](../../../docs/framework/app-domains/use.md)
