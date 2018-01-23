---
title: ".NET Core の追加ツール"
description: ".NET Core 機能を支援し、拡張する追加ツールの概要。"
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: article
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: eac67285500e62501f3bb552deaf5b07db609d4e
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2018
---
# <a name="net-core-additional-tools"></a><span data-ttu-id="9fff1-103">.NET Core の追加ツール</span><span class="sxs-lookup"><span data-stu-id="9fff1-103">.NET Core additional tools</span></span>
<span data-ttu-id="9fff1-104">このセクションでは、[.NET Core コマンドライン インターフェイス (CLI)](..\tools\index.md) ツールに加え、.NET Core 機能を支援し、拡張するツールを一覧で紹介します。</span><span class="sxs-lookup"><span data-stu-id="9fff1-104">This section compiles a list of tools that support and extend the .NET Core functionality, in addition to the [.NET Core command-line interface (CLI)](..\tools\index.md) tools.</span></span>

### <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[<span data-ttu-id="9fff1-105">WCF Web サービス リファレンス</span><span class="sxs-lookup"><span data-stu-id="9fff1-105">WCF Web Service Reference Tool</span></span>](wcf-web-service-reference-guide.md)
<span data-ttu-id="9fff1-106">WCF Web サービス リファレンスは Visual Studio に接続されているサービス プロバイダーです。[Visual Studio 2017 バージョン 15.5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools) から導入されました。</span><span class="sxs-lookup"><span data-stu-id="9fff1-106">The WCF Web Service Reference is a Visual Studio connected service provider that made its debut in [Visual Studio 2017 version 15.5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools).</span></span> <span data-ttu-id="9fff1-107">このツールは現在のソリューションの Web サービスから、ネットワーク上の場所で、あるいは WSDL ファイルからメタデータを取得し、Web サービスのアクセスに使用できる Windows Communication Foundation (WCF) クライアント プロキシ コードを含む、.NET Core 互換ソース ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="9fff1-107">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

### <a name="xml-serializer-generatorxmlserializergenerator-instructionsmd"></a>[<span data-ttu-id="9fff1-108">XML シリアライザー ジェネレーター</span><span class="sxs-lookup"><span data-stu-id="9fff1-108">XML Serializer Generator</span></span>](xmlserializergenerator-instructions.md)
<span data-ttu-id="9fff1-109">.NET Framework の [Xml シリアライザー ジェネレーター (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) と同様に、[Microsoft.XmlSerializer.Generator NuGet パッケージ](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)は .NET Core および .NET Standard ライブラリのソリューションです。</span><span class="sxs-lookup"><span data-stu-id="9fff1-109">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the solution for .NET Core and .NET Standard libraries.</span></span> <span data-ttu-id="9fff1-110">アセンブリに含まれる型の XML シリアル化アセンブリを作成することで、<xref:System.Xml.Serialization.XmlSerializer> を使用してその型のオブジェクトをシリアル化または逆シリアル化するときの XML シリアル化の起動パフォーマンスを改善します。</span><span class="sxs-lookup"><span data-stu-id="9fff1-110">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>