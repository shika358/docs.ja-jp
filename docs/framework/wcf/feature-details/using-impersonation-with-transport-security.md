---
title: "トランスポート セキュリティでの偽装の使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
caps.latest.revision: 12
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 12
---
# トランスポート セキュリティでの偽装の使用
*偽装*とは、サーバー アプリケーションがクライアントの ID を獲得する機能です。リソースへのアクセスを検証するときに、サービスでは偽装が広く使用されます。サーバー アプリケーションはサービス アカウントを使用して実行されますが、クライアントの接続を受け入れたサーバーは、クライアントの資格情報を使用してアクセス チェックが実行できるようにクライアントを偽装します。トランスポート セキュリティは、資格情報を渡すこと、および渡された資格情報を使用して通信をセキュリティで保護することの 2 つの機構から成ります。このトピックでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のトランスポート セキュリティと共に偽装機能を使用する方法について説明します。メッセージ セキュリティを使用した偽装[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)」を参照してください。  
  
## 5 つの偽装レベル  
 トランスポート セキュリティでは、次の表で説明するように 5 つの偽装レベルを使用します。  
  
|偽装レベル|説明|  
|-----------|--------|  
|None|サーバー アプリケーションは、クライアントの偽装を試みません。|  
|Anonymous|サーバー アプリケーションはクライアントの資格情報に対してアクセス チェックを実行できますが、クライアントの ID に関する情報は一切受け取りません。この偽装レベルは、名前付きパイプなど、コンピューター上での通信にのみ意味があります。リモート接続で `Anonymous` レベルを使用すると、Identify レベルの偽装に昇格されます。|  
|Identify|サーバー アプリケーションは、クライアントの ID を認識し、クライアントの資格情報に対するアクセスの検証を実行できますが、クライアントを偽装することはできません。トークン プロバイダーによって別の偽装レベルが提供されない限り、Identify レベルは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の SSPI 資格情報で使用される既定の偽装レベルになります。|  
|Impersonate|サーバー アプリケーションは、アクセス チェックを実行できるだけでなく、クライアントとしてサーバー コンピューターのリソースにアクセスできます。偽装されたトークンにはネットワーク資格情報が含まれないため、サーバー アプリケーションはクライアントの ID を使用してリモート コンピューター上のリソースにアクセスできません。|  
|Delegate|`Impersonate` と同じ機能に加えて、Delegate レベルの偽装では、サーバー アプリケーションがクライアントの ID を使用してリモート コンピューターのリソースにアクセスし、この ID を他のアプリケーションに渡すことができます。<br /><br /> **重要** これらの追加の機能を使用するには、ドメイン コントローラー上でそのサーバーのドメイン アカウントが委任先として信頼できるものとしてマークされている必要があります。このレベルの偽装は、機密としてマークされているクライアント ドメイン アカウントでは使用できません。|  
  
 トランスポート セキュリティで最も多く使用されるレベルは、`Identify` および `Impersonate` です。`None` および `Anonymous` レベルは、通常の使用にはお勧めしません。トランスポートの多くでは認証でこのレベルの使用をサポートしていません。`Delegate` レベルの機能は強力であり、使用に際しては注意が必要です。資格情報を委任するアクセス許可は、信頼できるサーバー アプリケーションにのみ与える必要があります。  
  
 `Impersonate` または `Delegate` レベルで偽装を使用するには、サーバー アプリケーションが `SeImpersonatePrivilege` 特権を持っている必要があります。管理者グループのアカウントまたはサービス SID \(Network Service、Local Service、または Local System\) を持つアカウントでアプリケーションを実行している場合は、アプリケーションに既定でこの特権があります。偽装ではクライアントとサーバーの相互認証は必要ありません。NTLM など、偽装をサポートする認証方式の中には、相互認証を使用できないものもあります。  
  
## 偽装でのトランスポート固有の問題  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] におけるトランスポートの選択は、選択できる偽装のレベルに影響を与えます。ここでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の標準 HTTP トランスポートと名前付きパイプ トランスポートに影響する問題について説明します。カスタム トランスポートには、偽装のサポートに関して独自の制限があります。  
  
### 名前付きパイプ トランスポート  
 次の項目が名前付きパイプ トランスポートと共に使用されます。  
  
-   名前付きパイプ トランスポートはローカル コンピューター上のみで使用します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の名前付きパイプでは、コンピューター間の接続が明示的に禁止されています。  
  
-   名前付きパイプは、`Impersonate` または `Delegate` 偽装レベルでは使用できません。これらの偽装レベルでは、名前付きパイプはコンピューター上で保障されません。  
  
 名前付きパイプ[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[トランスポートの選択](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)」を参照してください。  
  
### HTTP トランスポート  
 HTTP トランスポートを使用するバインディング \(<xref:System.ServiceModel.WSHttpBinding> と <xref:System.ServiceModel.BasicHttpBinding>\) では、「[HTTP 認証の理解](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)」で説明するように、いくつかの認証方式がサポートされます。サポートされる偽装レベルは、認証方式によって異なります。次の項目が HTTP トランスポートと共に使用されます。  
  
-   `Anonymous` 認証方式は偽装を無視します。  
  
-   `Basic` 認証方式は `Delegate` レベルのみをサポートします。これより低い偽装レベルは、アップグレードされます。  
  
-   `Digest` 認証方式では、`Impersonate` レベルと `Delegate` レベルのみをサポートします。  
  
-   `NTLM` 認証方式は、直接またはネゴシエーション経由で選択可能で、ローカル コンピューターで `Delegate` レベルのみをサポートします。  
  
-   Kerberos 認証方式は、ネゴシエーション経由でのみ選択可能で、サポートされるすべての偽装レベルで使用できます。  
  
 HTTP トランスポート[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[トランスポートの選択](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)」を参照してください。  
  
## 参照  
 [委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)   
 [承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)   
 [方法 : サービスでクライアントに偽装する](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)   
 [HTTP 認証の理解](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)