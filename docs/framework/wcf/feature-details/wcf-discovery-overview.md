---
title: "WCF Discovery の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28bf67b3840cb37c918198dd0910db9d592a6823
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-discovery-overview"></a>WCF Discovery の概要
Discovery API は、WS-Discovery プロトコルを使用した Web サービスの動的公開と探索の統合プログラミング モデルを提供します。 これらの API は、サービスがサービス自体を公開し、クライアントが公開されたサービスを発見できるようにします。 サービスを探索可能にした後は、サービスでアナウンス メッセージを送信できるほか、探索要求のリッスンと応答もできるようになります。 探索可能なサービスは、ネットワークに接続されたことをアナウンスする Hello メッセージ、およびネットワークから切断されたことをアナウンスする Bye メッセージを送信できます。 サービスを検索するために、クライアントは、サービス コントラクト型、キーワード、ネットワークのスコープなど、特定の条件が設定された `Probe` 要求を送信します。 サービスはこの `Probe` 要求を受信し、条件に一致するかどうかを判断します。 サービスが条件に一致した場合は、サービスへの接続に必要な情報と併せて `ProbeMatch` メッセージをクライアントに送り返すことで応答します。 クライアントは `Resolve` 要求を送信することもできます。この要求では、エンドポイント アドレスが変更されている可能性があるサービスを発見できます。 条件に一致したサービスは、`Resolve` メッセージをクライアントに送り返すことで、`ResolveMatch` 要求に応答します。  
  
## <a name="ad-hoc-and-managed-modes"></a>アドホック モードとマネージ モード  
 Discovery API は、マネージとアドホックという 2 種類のモードをサポートします。 マネージ モードでは、使用可能なサービスについての情報を管理する探索プロキシと呼ばれる集中サーバーがあります。 探索プロキシには、さまざまな方法でサービスについての情報を設定できます。 たとえば、サービスから起動中にアナウンス メッセージを探索プロキシに送信することも、探索プロキシがデータベースや構成ファイルからデータを読み取って、使用可能なサービスを特定することもできます。 探索プロキシへの情報の設定方法は、開発者が決定します。 クライアントは、探索プロキシを使用して、使用可能なサービスについての情報を取得します。 クライアントは、サービスを検索するときに `Probe` メッセージを探索プロキシに送信します。探索プロキシは、認識しているサービスのうち、クライアントが検索しているサービスに一致するものがあるかどうかを判断します。 一致するものがあった場合、探索プロキシは `ProbeMatch` 応答をクライアントに返します。 クライアントは、プロキシから返されたサービスの情報を使用して、直接サービスにアクセスします。 マネージ モードの基盤である最大の原則は、探索要求がユニキャストで 1 つの機構、つまり、探索プロキシに送信されることです。 .NET Framework には、開発者が独自のプロキシを作成できる主要コンポーネントがあります。 クライアントとサービスは、次のような複数の方法でプロキシを見つけることができます。  
  
-   プロキシがアドホック メッセージに応答する。  
  
-   プロキシが起動中にアナウンス メッセージを送信する。  
  
-   特定の既知のエンドポイントを検索するように、クライアントとサービスを作成する。  
  
 アドホック モードには、集中サーバーはありません。 サービス アナウンスやクライアント要求など、すべての探索メッセージは、マルチキャストで送信されます。 既定では、.NET Framework に、UDP プロトコルを利用したアドホック探索のサポートが含まれています。 たとえば、起動時に Hello アナウンスを送信するようにサービスが構成されている場合、サービスは、UDP プロトコルを使用して既知のマルチキャスト アドレスからアナウンスを送信します。 クライアントは、これらのアナウンスをアクティブにリッスンし、適宜処理する必要があります。 クライアントが、ある特定のサービスを検索するための `Probe` メッセージを送信すると、このメッセージは、マルチキャスト プロトコルを使用してネットワーク上で送信されます。 要求を受信した各サービスは、`Probe` メッセージの条件に一致するかどうかを判断し、`ProbeMatch` メッセージに指定されている条件に一致する場合は、`Probe` メッセージを使用して直接クライアントに応答します。  
  
## <a name="benefits-of-using-wcf-discovery"></a>WCF Discovery を使用する利点  
 WCF Discovery は WS-Discovery プロトコルを使用して実装されるため、WS-Discovery を実装するその他のクライアント、サービス、およびプロキシと相互運用可能です。 WCF Discovery は既存の WCF API を基盤にしているため、既存のサービスやクライアントに簡単に探索機能を追加できます。 サービスは、アプリケーション構成設定を使用して、簡単に探索可能にできます。 また、WCF Discovery では、ピア ネットワーク、名前付けオーバーレイ、HTTP など、その他のトランスポートでの探索プロトコルの使用もサポートされます。 WCF Discovery は、探索プロキシが使用されるマネージ モードの運用をサポートします。 これにより、ネットワーク全体にマルチキャスト メッセージが送信されずに、探索プロキシに直接メッセージが送信されるため、ネットワーク トラフィックが軽減されます。 WCF Discovery では、Web サービスをより柔軟に操作することもできます。 たとえば、クライアントやサービスを再構成することなく、サービスのアドレスを変更できます。 クライアントがサービスにアクセスする必要がある場合、`Probe` 要求により `Find` メッセージを発行すると、サービスの現在のアドレスがサービスから返されます。 WCF Discovery では、クライアントは、コントラクトの種類、バインド要素、名前空間、スコープ、キーワードやバージョン番号など、異なる条件を基に特定のサービスを検索できます。 WCF Discovery では、実行時および設計時にも探索が可能です。 アプリケーションに探索を追加することで、フォールト トレランスや自動構成など、その他のシナリオを実現することもできます。  
  
## <a name="service-publication"></a>サービスの公開  
 サービスを探索可能にするには、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> をサービス ホストに追加し、探索エンドポイントを追加して探索メッセージをリッスンする場所を指定する必要があります。 次のコード例は、自己ホスト型サービスを変更して探索可能にする方法を示しています。  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",  
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 サービスを探索可能にするには、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> のインスタンスをサービスの説明に追加する必要があります。 探索要求をリッスンするサービスを指定するには、<xref:System.ServiceModel.Discovery.DiscoveryEndpoint> のインスタンスをサービス ホストに追加する必要があります。 この例では、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (<xref:System.ServiceModel.Discovery.DiscoveryEndpoint> から派生した) を追加して、サービスが UDP マルチキャスト トランスポートを利用して探索要求をリッスンするように指定しています。 すべてのメッセージがマルチキャストで送信されるため、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> を使用してアドホック探索が実行されるようにしています。  
  
## <a name="announcement"></a>アナウンス  
 既定では、サービスを公開しても、アナウンス メッセージは送信されません。 アナウンス メッセージを送信するように、サービスを構成する必要があります。 このため、探索メッセージのリッスンとは別に、サービスをアナウンスできるため、より柔軟にサービスを作成できます。 サービス アナウンスは、探索プロキシまたはその他のサービス レジストリにサービスを登録するメカニズムとしても使用できます。 次のコード例は、UDP バインドを利用してアナウンス メッセージを送信するようにサービスを構成する方法を示しています。  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a>サービス探索  
 クライアント アプリケーションは、<xref:System.ServiceModel.Discovery.DiscoveryClient> クラスを使用してサービスを検索できます。 開発者は、<xref:System.ServiceModel.Discovery.DiscoveryClient> メッセージまたは `Probe` メッセージの送信先を指定する探索エンドポイントに渡す `Resolve` クラスのインスタンスを作成します。 クライアントは、次に、<xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> インスタンス内に検索条件を指定する <xref:System.ServiceModel.Discovery.FindCriteria> を呼び出します。 一致するサービスが見つかった場合、<xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> は <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> のコレクションを返します。 次のコードは、`Find` メソッドを呼び出して、検索されたサービスに接続する方法を示しています。  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService()) 
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =   
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =   
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a>探索およびメッセージ レベルのセキュリティ  
 メッセージ レベルのセキュリティを使用する場合は、<xref:System.ServiceModel.EndpointIdentity> をサービスの探索エンドポイントに指定し、対応する <xref:System.ServiceModel.EndpointIdentity> をクライアントの探索エンドポイントに指定する必要があります。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]メッセージ レベル セキュリティを参照してください[メッセージ セキュリティ](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)です。  
  
## <a name="discovery-and-web-hosted-services"></a>探索および Web ホスト サービス  
 WCF サービスが探索可能であるためには、このサービスが実行されている必要があります。 IIS または WAS でホストされている WCF サービスは、IIS/WAS がサービスにバインドされているメッセージを受信するまで実行されないため、既定では探索できません。  Web ホスト サービスを探索可能にするには、次の 2 つのオプションがあります。  
  
1.  Windows Server AppFabric の自動開始機能の使用  
  
2.  サービスに代わって通信を行う探索プロキシの使用  
  
 Windows Server AppFabric には、メッセージを受信する前にサービスを開始できる自動開始機能が備わっています。 この自動開始セットで、IIS/WAS でホストされるサービスを探索できるように構成できます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Auto-start 機能を参照してください[Windows Server AppFabric Auto-start 機能](http://go.microsoft.com/fwlink/?LinkId=205545)します。 自動開始機能をオンにすると共に、探索サービスを構成する必要があります。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][する方法: WCF サービスとクライアントを探索可能性をプログラミングで追加](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[構成ファイルにおける探索の構成](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)です。  
  
 探索プロキシはサービスが実行されていないときに WCF サービスの代わりに通信に使用できます。 このプロキシはプローブをリッスンするか、メッセージを解決して、クライアントに応答できます。 これで、クライアントはメッセージをサービスに直接送信できます。 クライアントがサービスにメッセージを送信する場合、インスタンス化されてメッセージに応答します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]探索プロキシの実装を参照してください、 [、探索プロキシを実装する](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)です。  
  
> [!NOTE]
>  WCF 探索が正常に動作するには、すべての Nic (ネットワーク インターフェイス コント ローラー) は 1 個の IP アドレスをのみが必要です。
