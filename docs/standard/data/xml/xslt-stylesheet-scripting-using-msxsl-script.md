---
title: "XSLT スタイル シートのスクリプトを使用して&lt;msxsl:script&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 35f24c0a033748917b465510d4f70b75946a0a74
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="xslt-stylesheet-scripting-using-ltmsxslscriptgt"></a>XSLT スタイル シートのスクリプトを使用して&lt;msxsl:script&gt;
<xref:System.Xml.Xsl.XslTransform> クラスは、`script` 要素を使用した埋め込みスクリプトをサポートしています。  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> では、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] クラスが廃止されています。 <xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT (Extensible Stylesheet Language for Transformations) 変換を実行できます。 参照してください[XslCompiledTransform クラスを使用して](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)と[XslTransform クラスからの移行](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)詳細についてはします。  
  
 <xref:System.Xml.Xsl.XslTransform> クラスは、`script` 要素を使用した埋め込みスクリプトをサポートしています。 スタイル シートが読み込まれると、定義されているすべての関数がクラス定義でラップされることによって Microsoft Intermediate Language (MSIL) にコンパイルされるため、パフォーマンスが低下しません。  
  
 `<msxsl:script>` 要素は、次のように定義されます。  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 `msxsl` は、名前空間 `urn:schemas-microsoft-com:xslt` に関連付けられたプレフィックスです。  
  
 `language` 属性は必須ではありませんが、指定する場合は、値を C#、VB、JScript、JavaScript、VisualBasic、または CSharp のいずれかにする必要があります。 language 属性を指定しない場合、既定の言語は JScript です。 `language-name` では大文字小文字が区別されないため、"JavaScript" と "javascript" は同じものと見なされます。  
  
 `implements-prefix` 属性は必須です。 この属性は、名前空間を宣言し、それをスクリプト ブロックに関連付けるために使用されます。 この属性の値は、名前空間を表すプレフィックスです。 この名前空間は、スタイル シート内の任意の場所で定義できます。  
  
 `msxsl:script` 要素は名前空間 `urn:schemas-microsoft-com:xslt` に属しているため、スタイル シートには、名前空間宣言 `xmlns:msxsl=urn:schemas-microsoft-com:xslt` が含まれている必要があります。  
  
 スクリプトの呼び出し元がない場合<xref:System.Security.Permissions.SecurityPermissionFlag>へのアクセス許可、スクリプト、スタイル シートがコンパイルされずを呼び出すと<xref:System.Xml.Xsl.XslTransform.Load%2A>は失敗します。  
  
 呼び出し元が `UnmanagedCode` へのアクセス許可を持っている場合、スクリプトはコンパイルされますが、許可される操作は、読み込み時に指定される証拠によって異なります。  
  
 <xref:System.Xml.Xsl.XslTransform.Load%2A> または <xref:System.Xml.XmlReader> を受け取る <xref:System.Xml.XPath.XPathNavigator> メソッドを使用してスタイル シートを読み込む場合は、<xref:System.Xml.Xsl.XslTransform.Load%2A> パラメーターを引数として受け取る <xref:System.Security.Policy.Evidence> オーバーロードを使用する必要があります。 証拠を指定する、呼び出し元がいる必要があります<xref:System.Security.Permissions.SecurityPermissionFlag>へのアクセス許可`Evidence`スクリプト アセンブリ。 呼び出し元がこのアクセス許可を持っていない場合は、`Evidence` パラメーターが `null` に設定されることがあります。 その場合は、<xref:System.Xml.Xsl.XslTransform.Load%2A> 関数がスクリプトを見つけると、処理が失敗します。 `ControlEvidence` へのアクセス許可は、非常に強力なアクセス権であるため、信頼性の高いコード以外に与えてはいけません。  
  
 アセンブリから証拠を取得するには、`this.GetType().Assembly.Evidence` を使用します。 URI (Uniform Resource Identifier) から証拠を取得するには、`Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)` を使用します。  
  
 <xref:System.Xml.Xsl.XslTransform.Load%2A> を受け取り、<xref:System.Xml.XmlResolver> を受け取らない `Evidence` メソッドを使う場合、アセンブリのセキュリティ ゾーンは既定で Full Trust に設定されます。 詳細については、次を参照してください。<xref:System.Security.SecurityZone>と[名前付き権限セット](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3)です。  
  
 関数は、`msxsl:script` 要素内で宣言できます。 既定でサポートされる名前空間を次の表に示します。 表に示す名前空間の外側でもクラスを使用できます。 ただし、これらのクラスには、完全修飾名が指定されている必要があります。  
  
|既定の名前空間|説明|  
|------------------------|-----------------|  
|システム|システム クラス|  
|System.Collection|コレクション クラス|  
|System.Text|テキスト クラス|  
|System.Text.RegularExpressions|正規表現クラス|  
|System.Xml|コア XML クラス|  
|System.Xml.Xsl|XSLT クラス|  
|System.Xml.XPath|XPath (XML Path Language) クラス|  
|Microsoft.VisualBasic|Microsoft Visual Basic スクリプト クラスです。|  
  
 関数が宣言されると、その関数はスクリプト ブロックに含まれます。 スタイル シートには、相互に独立して機能する複数のスクリプト ブロックを含めることができます。 このため、1 つのスクリプト ブロック内で実行しているときに、別のスクリプト ブロックで定義した関数を呼び出すことはできません。ただし、そのブロックが同じ名前空間とスクリプト言語を持つように宣言されている場合は例外です。 各スクリプト ブロックは独自の言語で記述でき、ブロックはその言語に対応するパーサーの文法規則に従って解析されるため、使われている言語の正しい構文を使用する必要があります。 たとえば、C# スクリプト ブロック内で XML コメント ノード `<!-- an XML comment -->` を使用すると、エラーが発生します。  
  
 スクリプト関数で定義されている引数および戻り値は、W3C (World Wide Web Consortium) XPath 型または XSLT 型のいずれかである必要があります。 次の表に、対応する W3C 型、それと同等の .NET Framework のクラス (型)、および、XPath 型または XSLT 型には、W3C が入力するかどうか。  
  
|型|対応する .NET Framework クラス (型)|XPath 型または XSLT 型|  
|----------|----------------------------------------------|-----------------------------|  
|String|System.String|XPath|  
|Boolean|System.Boolean|XPath|  
|Number|System.Double|XPath|  
|Result Tree Fragment|System.Xml.XPath.XPathNavigator|XSLT|  
|Node Set|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 スクリプト関数が数値型 Int16、UInt16、Int32、UInt32、Int64、UInt64、Single、または Decimal を使用する場合、これらの数値型は、W3C XPath 数値型に対応する Double に強制的に変換されます。 その他の型はすべて、`ToString` メソッドを呼び出して強制的に文字列に変換されます。  
  
 スクリプト関数が上記以外の型を使用したり、スタイル シートが <xref:System.Xml.Xsl.XslTransform> オブジェクトに読み込まれるときにスクリプト関数がコンパイルを実行しなかったりすると、例外がスローされます。  
  
 使用する場合、`msxsl:script`要素、強くお勧め、言語に関係なく、スクリプトを CDATA セクション内に配置することです。 コードが配置されている CDATA セクションのテンプレートを示す XML の例を次に示します。  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 特定の言語の演算子、識別子、または区切り記号が誤って XML として解釈される可能性があるため、スクリプトのすべての内容を CDATA セクション内に配置することをお勧めします。 スクリプトで論理 AND 演算子を使用する例を次に示します。  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp>  
    public string book(string abc, string xyz)  
    {  if ((abc== abc)&&(abc== xyz)) return bar+xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 この例では、アンパサンドがエスケープされないため、結果として例外がスローされます。 ドキュメントは、XML として読み込まれ、テキストの間に特別な処理は適用されません、`msxsl:script`要素タグ。  
  
## <a name="example"></a>例  
 埋め込みスクリプトを使用して、半径が指定された円の円周を算出する例を次に示します。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.               
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
    writer.Close()  
  End Sub   
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.               
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }   
}  
```  
  
## <a name="input"></a>入力  
 number.xml  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>  
```  
  
 calc.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius){  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">    
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>   
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a>出力  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>    
```  
  
## <a name="see-also"></a>関連項目  
 [XslTransform クラスによる XSLT プロセッサ](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
