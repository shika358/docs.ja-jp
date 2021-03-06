---
title: /verbose
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5480f828fa1f0b6d71fa649bf44513ce806bb440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="verbose"></a>/verbose
詳細なステータスとエラー メッセージを生成するためにコンパイラ ボックスをオンにします。  
  
## <a name="syntax"></a>構文  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 省略可能です。 指定する`/verbose`を指定することと同じ`/verbose+`、詳細メッセージを出力するようコンパイラを停止します。 このオプションの既定値は`/verbose-`します。  
  
## <a name="remarks"></a>コメント  
 `/verbose`オプション、コンパイラによって生成したエラーの合計数に関する情報を表示対象のアセンブリ、モジュールから読み込んでいる、現在コンパイルされているどのファイルが表示されます。  
  
> [!NOTE]
>  `/verbose`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`In.vb`し、詳細なステータス情報を表示することをコンパイラに指示します。  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
