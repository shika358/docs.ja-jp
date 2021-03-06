---
title: "連続するキーで結果をグループ化する"
description: "連続するキーで結果をグループ化する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: cdd06a6fad037291bbc5aa011b47bb668fa2f062
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="group-results-by-contiguous-keys"></a>連続するキーで結果をグループ化する

要素をグループ化し、連続するキーのサブシーケンスを表すチャンクにする方法を次の例に示します。 たとえば、次の一連のキーと値のペアがあるとします。  
  
|キー|値|  
|---------|-----------|  
|A|水|  
|A|think|  
|A|that|  
|B|Linq|  
|C|is|  
|A|really|  
|B|cool|  
|B|!|  
  
 次のグループがこの順序で作成されます。  
  
1.  We, think, that  
  
2.  Linq  
  
3.  is  
  
4.  really  
  
5.  cool, !  
  
 ソリューションは、結果をストリーミングで返すスレッド セーフな拡張メソッドとして実装されます。 つまり、ソース シーケンス内を移動するときにグループが作成されます。 `group` 演算子や `orderby` 演算子とは異なり、すべてのシーケンスの読み取りが終わる前に、呼び出し元にグループを返し始めることができます。  
  
 ソース コードのコメントで説明されているように、ソース シーケンスが反復処理されるときに各グループまたはチャンクのコピーを作成することで、スレッド セーフが実現されます。 ソース シーケンスに連続するアイテムの大きなシーケンスがある場合、共通言語ランタイムにより <xref:System.OutOfMemoryException> がスローされる可能性があります。  
  
## <a name="example"></a>例  
 拡張メソッドと、それを使用するクライアント コードを次の例に示します。  
  
 [!code-csharp[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 プロジェクトで拡張メソッドを使用するには、`MyExtensions` 静的クラスを新規または既存のソース コード ファイルにコピーし、必要に応じて、配置されている名前空間の `using` ディレクティブを追加します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ クエリ式](index.md)  
 
