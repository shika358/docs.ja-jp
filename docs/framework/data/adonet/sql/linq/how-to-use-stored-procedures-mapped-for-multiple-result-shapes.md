---
title: "方法 : 複数の結果形状が割り当てられたストアド プロシージャを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fde4dd9044ff2bc6d781d7ceafec2bde3df7e14d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>方法 : 複数の結果形状が割り当てられたストアド プロシージャを使用する
複数の結果形状を返すことができるストアド プロシージャの場合、戻り値の型を単一の射影形状として厳密に型指定することはできません。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]すべての可能性のある射影型を生成することができます、戻されます順序を知ることはできません。  
  
 このシナリオと対照的なのが、複数の結果形状をシーケンシャルに生成するストアド プロシージャです。 詳細については、次を参照してください。[する方法: を使用してストアド プロシージャ用にマップ結果形状をシーケンシャル](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)です。  
  
 複数の結果型を返すストアド プロシージャには、プロシージャが返す可能性のある一連の型を示す <xref:System.Data.Linq.Mapping.ResultTypeAttribute> 属性を適用します。  
  
## <a name="example"></a>例  
 次の SQL コードの例では、結果形状は入力値 (`shape =1` または `shape = 2`) に応じて変わります。 どちらの射影が先に返されるかはわかりません。  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a>例  
 このストアド プロシージャを実行するには、次のようなコードを使用します。  
  
> [!NOTE]
>  ストアド プロシージャに対する知識に基づいて、<xref:System.Data.Linq.IMultipleResults.GetResult%2A> パターンを使用し、正しい型の列挙子を取得する必要があります。  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャ](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
