---
title: ".NET Framework Performance | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "performance [.NET Framework]"
  - "reliability [.NET Framework]"
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
caps.latest.revision: 20
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 20
---
# .NET Framework Performance
優れたパフォーマンスのアプリを作成する場合は、アプリのその他の機能を設計する場合と同様に、パフォーマンスについて設計および計画する必要があります。  Microsoft が提供するツールを使用して、アプリのパフォーマンスを測定し、必要に応じて、メモリの使用、コードのスループット コード、および応答性を向上させることができます。  ここでは、Microsoft が提供するパフォーマンス分析ツールの一覧と、アプリ開発の特定の領域のパフォーマンスに関する他のトピックへのリンクを示します。  
  
## パフォーマンスのための設計と計画  
 優れたパフォーマンスのアプリが必要な場合は、他の機能を設計する場合と同様に、パフォーマンスの設計をアプリに組み込む必要があります。  アプリのパフォーマンスが重要なシナリオを決定し、パフォーマンスの目標を設定して、それらのアプリのシナリオのパフォーマンスを早い段階から頻繁に計測する必要があります。  アプリはそれぞれ異なり、パフォーマンスが重要な実行パスも異なるため、このようなパスを早期に特定し、労力を集中させることによって生産性を最大化できます。  
  
 高いパフォーマンスのアプリを作成するために、ターゲット プラットフォームを完全に理解する必要はありません。  ただし、ターゲット プラットフォームのどの部分が、パフォーマンスの面で大きな負担が生じるのかを理解しておく必要があります。  開発プロセスの早い段階でパフォーマンスの計測することで、これを実現できます。  
  
 パフォーマンスにとって重要な領域を特定し、パフォーマンスの目標を確立するには、ユーザー エクスペリエンスを常に検討します。  起動時間と応答性は、ユーザーのアプリに対する認識に影響する 2 つの重要な部分です。  アプリが多くのメモリを使用する場合、ユーザーにとっては動作が遅いように見えたり、システムで実行中の他のアプリに影響を与える可能性があります。また、Windows ストアや Windows Phone ストアの送信プロセスでエラーとなる可能性もあります。  また、コードのどの部分を頻繁に実行するかを判断すると、コード内でこれらの部分が適切に最適化されていることを確認できます。  
  
## パフォーマンスを分析する  
 全体的な開発計画の一部として、開発中にアプリのパフォーマンスを計測し、その結果を以前に設定した目標と比較するポイントを設定します。  ユーザーが使用すると想定している環境およびハードウェアでアプリを計測します。  アプリのパフォーマンスを早い段階で頻繁に分析することによって、開発サイクルの後半ではコストがかかり、負担の大きいアーキテクチャの決定を変更できます。  次のセクションでは、アプリの分析に使用できるパフォーマンス ツールと、これらのツールによって使用さえるイベント トレーシングについて説明します。  
  
### パフォーマンス ツール  
 .NET Framework アプリで使用できるパフォーマンス ツールの一部を次に示します。  
  
|ツール|説明|  
|---------|--------|  
|Visual Studio パフォーマンス分析|Windows オペレーティング システムを実行しているコンピューターに配置されている .NET Framework アプリの CPU 使用量の分析に使用します。<br /><br /> このツールは、Visual Studio でプロジェクトを開いた後、**\[デバッグ\]** メニューから使用できます。  詳細については、「[プロファイリング ツールの使用](../Topic/Performance%20Explorer.md)」を参照してください。 **Note:**  Windows Phone を対象とする場合は、Windows Phone アプリケーション分析を使用します \(次の行を参照してください\)。|  
|Windows Phone アプリケーション分析|Windows Phone アプリの CPU やメモリ、ネットワーク データ転送率、アプリの応答性、バッテリの使用量の分析に使用します。<br /><br /> このツールは、[Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=265773) のインストール後に、 WIndows Phone プロジェクトの **\[デバッグ\]** メニューから使用できます。  詳細については、「[Windows Phone のアプリのプロファイリング](http://msdn.microsoft.com/library/windowsphone/develop/jj215908\(v=vs.105\).aspx)」を参照してください。|  
|[PerfView](http://www.microsoft.com/download/details.aspx?id=28567)|CPU とメモリ関連のパフォーマンスの問題を識別するために使用します。  このツールは、Windows イベント トレーシング \(ETW\) と CLR プロファイル API を使用して、メモリと CPU の高度な調査およびガベージ コレクションや JIT コンパイルに関する情報を提供します。  PerfView を使用する方法の詳細については、アプリに含まれるチュートリアルやヘルプ ファイル、[Channel 9 のビデオ チュートリアル](http://channel9.msdn.com/Series/PerfView-Tutorial)、および[ブログの投稿](http://blogs.msdn.com/b/vancem/archive/tags/perfview/) を参照してください。<br /><br /> メモリ固有の問題については、「[Using PerfView for Memory Investigations \(PerfView を使用したメモリの調査\)](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots)」を参照してください。|  
|[Windows Performance Analyzer](http://www.microsoft.com/download/details.aspx?id=30652)|複数のアプリが同じコンピューターで実行されているときに、アプリのメモリやストレージの使用量などの全体的なシステム パフォーマンスを特定するために使用します。  このツールは、[!INCLUDE[win8](../../../includes/win8-md.md)] 用の Windows アセスメント & デプロイメント キット \(ADK\) の一部としてダウンロード センターから使用できます。  詳細については、「[Windows Performance Analyzer](http://msdn.microsoft.com/library/windows/desktop/hh448170.aspx)」を参照してください。|  
  
### Windows イベント トレーシング \(ETW\)  
 ETW は、実行中のコードに関する診断情報を取得できるようにする手法であり、前に説明したパフォーマンス ツールの多くで必要なテクノロジです。  ETW は、特定のイベントが .NET Framework アプリおよび Windows によって発生したときにログを作成します。  ETW を使用すると、ログの記録を動的に有効または無効にすることができ、稼動環境でアプリを再起動せずに詳細なトレースを実行できます。  .NET Framework は ETW イベントをサポートしており、ETW はパフォーマンス データを生成する多くのプロファイル ツールやパフォーマンス ツールで使用されます。  これらのツールは、ETW イベントを有効または無効にするため、ETW イベントの知識が役立ちます。  アプリの特定のコンポーネントに関するパフォーマンス情報を収集するために、特定の ETW イベントを使用できます。  .NET Framework での ETW のサポートの詳細については、「[共通言語ランタイムの ETW イベント](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)」と「[タスク並列ライブラリおよび PLINQ での ETW イベント](../../../docs/framework/performance/etw-events-in-task-parallel-library-and-plinq.md)」を参照してください。  
  
## アプリの種類別のパフォーマンス  
 .NET Framework アプリの種類ごとに、パフォーマンスを評価するためのベスト プラクティス、考慮事項、およびツールがあります。  次の表では、特定の種類の .NET Framework アプリのパフォーマンスに関するトピックへのリンクを示します。  
  
|アプリの種類|参照トピック|  
|------------|------------|  
|すべてのプラットフォームに対応した .NET Framework アプリ|[Garbage Collection and Performance](../../../docs/standard/garbage-collection/performance.md)<br /><br /> [パフォーマンスに関するヒント](../../../docs/framework/performance/performance-tips.md)|  
|C\+\+、C\#、および Visual Basic で記述された [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリ|[C\+\+、C\#、または Visual Basic を使った Windows ストア アプリのパフォーマンスのベスト プラクティス](http://msdn.microsoft.com/library/windows/apps/hh750313.aspx)|  
|Windows Phone|[Windows Phone 用アプリのパフォーマンス上の考慮事項](http://msdn.microsoft.com/library/windowsphone/develop/ff967560\(v=vs.105\).aspx)<br /><br /> [Windows Phone アプリケーションの分析](http://msdn.microsoft.com/library/windowsphone/develop/hh202934\(v=vs.105\).aspx)<br /><br /> [Windows Phone アプリケーションを Marketplace にいち早く公開する](http://msdn.microsoft.com/magazine/hh781024.aspx)|  
|Windows Presentation Foundation \(WPF\)|[WPF Performance Suite](../Topic/WPF%20Performance%20Suite.md)|  
|Silverlight|[パフォーマンスに関するヒント](http://msdn.microsoft.com/library/cc189071\(v=vs.95\).aspx)|  
|ASP.NET|[ASP.NET Performance Overview](../Topic/ASP.NET%20Performance%20Overview.md)|  
|Windows フォーム|[Practical Tips for Boosting the Performance of Windows Forms Apps \(Windows フォーム アプリのパフォーマンスを向上させるための実践的なヒント\)](http://msdn.microsoft.com/magazine/cc163630.aspx)|  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[.NET Framework アプリケーションでのキャッシュ](../../../docs/framework/performance/caching-in-net-framework-applications.md)|データをキャッシュしてアプリケーションのパフォーマンスを向上させる手法について説明します。|  
|[限定的な初期化](../../../docs/framework/performance/lazy-initialization.md)|特にアプリの起動時にパフォーマンスを向上させるために、必要に応じてオブジェクトを初期化する方法について説明します。|  
|[信頼性](../../../docs/framework/performance/reliability.md)|サーバー環境での非同期例外の発生防止について説明します。|  
|[規模が大きく、応答性の高い .NET Framework アプリの作成](../../../docs/framework/performance/writing-large-responsive-apps.md)|マネージ コードで C\# および Visual Basic コンパイラを再作成する際に得られたパフォーマンスに関するヒントを説明し、C\# コンパイラでの実際の例をいくつか紹介します。|