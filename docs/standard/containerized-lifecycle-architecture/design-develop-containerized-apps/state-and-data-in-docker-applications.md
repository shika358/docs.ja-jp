---
title: "状態と Docker のアプリケーションでのデータ"
description: "Microsoft プラットフォームとツールが、Docker のコンテナー化アプリケーションのライフ サイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 61cd88ca8dd7e51759111d6a9357c008458ee41a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="state-and-data-in-docker-applications"></a><span data-ttu-id="ae4ab-104">状態と Docker のアプリケーションでのデータ</span><span class="sxs-lookup"><span data-stu-id="ae4ab-104">State and data in Docker applications</span></span>

<span data-ttu-id="ae4ab-105">コンテナーのプリミティブ型は不変です。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-105">A primitive of containers is immutability.</span></span> <span data-ttu-id="ae4ab-106">VM を比較すると、コンテナーはない共通の出現と表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-106">When compared to a VM, containers don't disappear as a common occurrence.</span></span> <span data-ttu-id="ae4ab-107">VM が停止しているプロセス、CPU の過負荷、または完全または障害が発生したディスクからのさまざまな形式で失敗します。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-107">A VM might fail in various forms from dead processes, overloaded CPU, or a full or failed disk.</span></span> <span data-ttu-id="ae4ab-108">まだ、使用する VM を考えて、RAID ドライブ ドライブ エラーのデータの管理を確保するための一般的です。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-108">Yet, we expect the VM to be available and RAID drives are commonplace to assure drive failures maintain data.</span></span>

<span data-ttu-id="ae4ab-109">ただし、コンテナーはプロセスのインスタンスにするものです。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-109">However, containers are thought to be instances of processes.</span></span> <span data-ttu-id="ae4ab-110">プロセスでは、持続性のある状態を維持しません。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-110">A process doesn't maintain durable state.</span></span> <span data-ttu-id="ae4ab-111">場合でも、コンテナーは、そのローカル ストレージに書き込むことができます、そのインスタンスがなるを無期限と仮定した場合は、メモリの単一コピーが持続的にすると仮定した場合と同じなります。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-111">Even though a container can write to its local storage, assuming that that instance will be around indefinitely would be equivalent to assuming a single-copy memory will be durable.</span></span> <span data-ttu-id="ae4ab-112">プロセスと同様に、コンテナーが重複しています、強制終了、または、それらを移動する可能性がありますコンテナー オーケストレータで管理されている、ときにことを想定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-112">You should assume that containers, like processes, are duplicated, killed, or, when managed with a container orchestrator, they might be moved.</span></span>

<span data-ttu-id="ae4ab-113">Docker と呼ばれる機能を使用して、*ファイル システムをオーバーレイ*いずれかを格納する書き込み時コピー処理を実装するには、基になる元のイメージと比較して、コンテナーのルート ファイル システムに情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-113">Docker uses a feature known as an *overlay file system* to implement a copy-on-write process that stores any updated information to the root file system of a container, compared to the original image on which it is based.</span></span> <span data-ttu-id="ae4ab-114">コンテナーはその後、システムから削除する場合、これらの変更は失われます。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-114">These changes are lost if the container is subsequently deleted from the system.</span></span> <span data-ttu-id="ae4ab-115">コンテナー、そのため、ありません永続的ストレージ既定では。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-115">A container, therefore, does not have persistent storage by default.</span></span> <span data-ttu-id="ae4ab-116">コンテナーの状態を保存することはできますが、この問題を回避システムの設計になりますコンテナー アーキテクチャの原則と競合しています。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-116">Although it's possible to save the state of a container, designing a system around this would be in conflict with the principle of container architecture.</span></span>

<span data-ttu-id="ae4ab-117">Docker のアプリケーションで永続的なデータを管理するには、一般的な解決方法があります。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-117">To manage persistent data in Docker applications, there are common solutions:</span></span>

-   <span data-ttu-id="ae4ab-118">[**データ ボリューム**](https://docs.docker.com/engine/tutorials/dockervolumes/) これらのホストだけに述べたようにマウントします。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-118">[**Data volumes**](https://docs.docker.com/engine/tutorials/dockervolumes/) These mount to the host, as just noted.</span></span>

-   <span data-ttu-id="ae4ab-119">[**データ ボリューム コンテナー**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) 順番に表示することができますを外部のコンテナーを使用して、コンテナー間で共有記憶域を提供します。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-119">[**Data volume containers**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) These provide shared storage across containers, using an external container that can cycle.</span></span>

-   <span data-ttu-id="ae4ab-120">[**ボリューム プラグイン**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) これら長期的な永続化を提供するリモートの場所へのボリュームのマウントします。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-120">[**Volume Plugins**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) These mount volumes to remote locations, providing long-term persistence.</span></span>

-   <span data-ttu-id="ae4ab-121">**リモート データ ソース** 例 SQL および NO SQL データベースを含めたり、Redis のようなサービスをキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-121">**Remote data sources** Examples include SQL and NO-SQL databases or cache services like Redis.</span></span>

-   <span data-ttu-id="ae4ab-122">[**Azure ストレージ**](https://docs.microsoft.com/azure/storage/) これにより、コンテナーの最適な長期的な永続化を提供するサービス (PaaS) 記憶域として geo 配布可能なプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-122">[**Azure Storage**](https://docs.microsoft.com/azure/storage/) This provides geo distributable platform as a service (PaaS) storage, providing the best of containers as long-term persistence.</span></span>

<span data-ttu-id="ae4ab-123">バイパスする 1 つまたは複数のコンテナー内のディレクトリを特別に指定されたデータ ボリューム、[共用体のファイル システム](https://docs.docker.com/v1.8/reference/glossary#union-file-system)です。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-123">Data volumes are specially designated directories within one or more containers that bypass the [Union File System](https://docs.docker.com/v1.8/reference/glossary#union-file-system).</span></span> <span data-ttu-id="ae4ab-124">データ ボリュームは、コンテナーのライフ サイクルに関係なく、データを維持するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-124">Data volumes are designed to maintain data, independent of the container's life cycle.</span></span> <span data-ttu-id="ae4ab-125">Docker したがってしないと自動的に削除ボリューム コンテナーによって参照されなく「ガベージ コレクションを」ボリュームも、コンテナーは削除します。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-125">Docker therefore never automatically deletes volumes when you remove a container, nor will it "garbage collect" volumes that are no longer referenced by a container.</span></span> <span data-ttu-id="ae4ab-126">ホスト オペレーティング システムでは、参照でき、任意のボリュームのデータを自由に編集データ ボリュームを慎重に使用する 1 つの理由はすることができます。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-126">The host operating system can browse and edit the data in any volume freely, which is just another reason to use data volumes sparingly.</span></span>

<span data-ttu-id="ae4ab-127">A[データ ボリューム コンテナー](https://docs.docker.com/v1.8/userguide/dockervolumes/)通常のデータ ボリュームより強化されています。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-127">A [data volume container](https://docs.docker.com/v1.8/userguide/dockervolumes/) is an improvement over regular data volumes.</span></span> <span data-ttu-id="ae4ab-128">基本的に休止しているコンテナー (前述のとおり) 内に作成された 1 つまたは複数のデータ ボリュームを持つことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-128">It is essentially a dormant container that has one or more data volumes created within it (as described earlier).</span></span> <span data-ttu-id="ae4ab-129">データ ボリューム コンテナーは、中央のマウント ポイントから、コンテナーにアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-129">The data volume container provides access to containers from a central mount point.</span></span> <span data-ttu-id="ae4ab-130">このアクセス方法の利点は、論理マウント ポイントのデータ コンテナーを作成元のデータの場所を分離することです。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-130">The benefit of this method of access is that it abstracts the location of the original data, making the data container a logical mount point.</span></span> <span data-ttu-id="ae4ab-131">また、"application"コンテナーを作成して、データを専用のコンテナー内で永続的に維持しながら破棄するデータ コンテナーのボリュームにアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-131">It also allows "application" containers accessing the data container volumes to be created and destroyed while keeping the data persistent in a dedicated container.</span></span>

<span data-ttu-id="ae4ab-132">図 4-5 は、正規の Docker ボリュームをストレージ コンテナー自体オブはホスト サーバーまたは VM の物理的な境界内に配置できることを示します。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-132">Figure 4-5 shows that regular Docker volumes can be placed on storage out of the containers themselves but within the host server/VM physical boundaries.</span></span> <span data-ttu-id="ae4ab-133">*Docker ボリュームは、1 つのホスト サーバー/VM から別のボリュームを使用する機能がない*です。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-133">*Docker volumes don't have the ability to use a volume from one host server/VM to another*.</span></span>

![](./media/image5.png)

<span data-ttu-id="ae4ab-134">図 4-5: データのボリュームとコンテナー/コンテナー アプリケーションの外部データ ソース</span><span class="sxs-lookup"><span data-stu-id="ae4ab-134">Figure 4-5: Data volumes and external data sources for containers apps/containers</span></span>

<span data-ttu-id="ae4ab-135">別々 の物理ホスト上で実行されるコンテナー間で共有データを管理することができない、ためお勧めしていないボリュームを使用するビジネス データの Docker ホストに固定ホスト/VM、しない限り、ために、orchestrator では、Docker コンテナーを使用する場合コンテナーは、クラスターで実行する最適化に応じて、別のホストを 1 つから移動するが必要です。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-135">Due to the inability to manage data shared between containers that run on separate physical hosts, it is recommended that you not use volumes for business data unless the Docker host is a fixed host/VM, because when using Docker containers in an orchestrator, containers are expected to be moved from one to another host, depending on the optimizations to be performed by the cluster.</span></span>

<span data-ttu-id="ae4ab-136">したがって、通常のデータ ボリュームは、トレース ファイル、テンポラル ファイル、または場合、または、コンテナーが複数のホスト間で移動されたときに、ビジネス データの整合性には影響しません、同様の考え方を使用する適切なメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-136">Therefore, regular data volumes are a good mechanism to work with trace files, temporal files, or any similar concept that won't affect the business data consistency if or when your containers are moved across multiple hosts.</span></span>

<span data-ttu-id="ae4ab-137">ボリュームのプラグインと同様に[Flocker](https://clusterhq.com/flocker/)クラスター内のすべてのホスト間でデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-137">Volume plug-ins like [Flocker](https://clusterhq.com/flocker/) provide data across all hosts in a cluster.</span></span> <span data-ttu-id="ae4ab-138">すべてのボリューム プラグインは均等に作成されますが、ボリュームのプラグインは通常外部化された永続的な信頼性の高い記憶域の変更できないコンテナーを提供します。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-138">Although not all volume plug-ins are created equally, volume plug-ins typically provide externalized persistent reliable storage from the immutable containers.</span></span>

<span data-ttu-id="ae4ab-139">リモート データ ソースと SQL データベース、DocumentDB の場合、Redis のようにリモートのキャッシュなどのキャッシュは、コンテナーなしの開発と同じではなります。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-139">Remote data sources and caches like SQL Database, DocumentDB, or a remote cache like Redis would be the same as developing without containers.</span></span> <span data-ttu-id="ae4ab-140">これは、ビジネス アプリケーションのデータを格納する、推奨されると、実績のある方法のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="ae4ab-140">This is one of the preferred, and proven, ways to store business application data.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="ae4ab-141">[前](モノリシック-applications.md) [次へ] (soa applications.md)</span><span class="sxs-lookup"><span data-stu-id="ae4ab-141">[Previous] (monolithic-applications.md) [Next] (soa-applications.md)</span></span>