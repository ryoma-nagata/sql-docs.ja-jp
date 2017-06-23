---
title: "ネイティブ モード レポート サーバー スケール アウト配置の構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- report servers [Reporting Services], deployments
- deploying [Reporting Services], scale-out deployment model
- scale-out deployments [Reporting Services]
ms.assetid: b30d0308-4d9b-4f85-9f83-dece4dcb2775
caps.latest.revision: 13
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6a90a566e3e100fff3bb17e838a368a82ac3f4f5
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---

# <a name="configure-a-native-mode-report-server-scale-out-deployment"></a>ネイティブ モード レポート サーバーのスケールアウト配置の構成

  Reporting Services ネイティブ モードでは、1 つのレポート サーバー データベースを共有する複数のレポート サーバー インスタンスを実行できる、スケールアウト配置モデルがサポートされています。 スケールアウト配置は、レポート サーバーのスケーラビリティを高めて、処理できる同時ユーザー数を増やしたり、より負荷の高いレポート実行に対応できるようにするために使用されます。 また、特定のサーバーを、対話型レポートまたはスケジュールされたレポートの処理専用にする場合にも使用できます。  
  
 SharePoint モードのレポート サーバーは、SharePoint 製品のインフラストラクチャを利用してスケールアウトを行います。 SharePoint モードのスケールアウトは、SharePoint モードのレポート サーバーを SharePoint ファームに追加することによって実行されます。 SharePoint モードでのスケールアウトについては、 「[ファームへのレポート サーバーの追加 &#40;SSRS スケールアウト&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)」を参照してください。  
 
  *スケールアウト配置*は次のシナリオで使用します。  
  
-   サーバー クラスターで複数のレポート サーバーの負荷分散を行うための前提条件として使用されます。 複数のレポート サーバーの負荷分散を行う前に、まず同じレポート サーバー データベースを共有するようにレポート サーバーを構成する必要があります。  
  
-   レポート サーバー アプリケーションを異なるコンピューターに分割するために使用されます。1 つ目のサーバーを対話型のレポート処理に使用し、2 つ目のサーバーをスケジュールされたレポート処理に使用します。 このシナリオでは、各サーバー インスタンスによって、共有レポート サーバー データベースに格納されている同じレポート サーバー コンテンツに対する異なる種類の要求が処理されます。  
  
 **スケールアウト配置は次の要素で構成されます。**  
  
-   1 つのレポート サーバー データベースを共有する複数のレポート サーバー インスタンス。  
  
-   対話型ユーザー ロードを複数のレポート サーバー インスタンス間で分散するネットワーク負荷分散 (NLB) クラスター (オプション)。  
  
 NLB クラスターに Reporting Services を配置する場合は、レポート サーバー URL の構成で NLB 仮想サーバー名を使用し、各サーバーで同じビュー ステートが共有されるように構成する必要があります。  
  
 Reporting Services は Microsoft Cluster Services クラスターには参加しません。 ただし、フェールオーバー クラスターの一部であるデータベース エンジン インスタンス上にレポート サーバー データベースを作成することは可能です。  
  
 **スケールアウト配置を計画、インストール、および構成するには、次の手順を実行します。**  
  
-   レポート サーバー インスタンスをインストールする手順については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「[インストール ウィザードからの SQL Server 2016 のインストール &#40;セットアップ&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)」を参照してください。  
  
-   ネットワーク負荷分散 (NLB) クラスター上でスケールアウト配置をホストする場合は、NLB クラスターを構成してからスケールアウト配置を構成する必要があります。 詳細については、「 [ネットワーク負荷分散クラスターにおけるレポート サーバーの構成](../../reporting-services/report-server/configure-a-report-server-on-a-network-load-balancing-cluster.md)」を参照してください。  
  
-   レポート サーバー データベースを共有してレポート サーバーをスケールアウトに加える方法については、このトピックの手順を確認してください。  
  
     この手順では、2 つのノードから成るレポート サーバーのスケールアウト配置を構成する方法について説明します。 他のレポート サーバー ノードを配置に追加するには、このトピックの手順を繰り返します。  
  
    -   セットアップを使用して、スケールアウト配置に追加する各レポート サーバー インスタンスをインストールします。  
  
         サーバー インスタンスを共有データベースに接続するときにデータベースの互換性エラーが発生しないようにするには、すべてのインスタンスが同じバージョンであることを確認します。 たとえば、SQL Server 2016 レポート サーバー インスタンスを使用して、レポート サーバー データベースを作成する場合、同じデプロイ内の他のすべてのインスタンスもあります SQL Server 2016。  
  
    -   Reporting Services 構成マネージャーを使用して、各レポート サーバーを共有データベースに接続します。 一度に接続および構成できるレポート サーバーは、1 つだけです。  
  
    -   Reporting Services 構成ツールを使用して、レポート サーバー データベースに既に接続されている最初のレポート サーバー インスタンスに新しいレポート サーバー インスタンスを追加してスケールアウトを完了します。  
  
## <a name="to-install-a-sql-server-instance-to-host-the-report-server-databases"></a>SQL Server インスタンスをインストールしてレポート サーバー データベースをホストするには  
  
1.  レポート サーバー データベースをホストするコンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスをインストールします。 少なくとも、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]をインストールします。  
  
2.  必要に応じて、レポート サーバーでリモート接続を有効にします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンの中には、既定で TCP/IP および名前付きパイプのリモート接続が有効になっていないバージョンもあります。 リモート接続が許可されているかどうかを確認するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、対象インスタンスのネットワーク構成設定を確認します。 リモート インスタンスが名前付きインスタンスの場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスが有効になっていることと、対象サーバーで実行されていることを確認します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser によって、名前付きインスタンスへの接続に使用されるポート番号が提供されます。 

## <a name="service-accounts"></a>サービス アカウント

Reporting Services インスタンスで使用するサービス アカウントは、スケール アウト配置を処理するときに重要です。 Reporting Services インスタンスを展開するときに、次のいずれかを行う必要があります。

**オプション 1:**同じドメイン ユーザー アカウントでサービス アカウントのすべての Reporting Services インスタンスを構成する必要があります。

**オプション 2:**各個人アカウント、ドメイン アカウントをサービス、ReportServer カタログ データベースをホストする SQL Server データベース インスタンス内で dbadmin アクセス許可を付与する必要があります。

上記のオプションのいずれかのよりも、別の構成を構成した場合 SQL エージェントを使用してタスクを変更した場合の断続的にエラーが発生する可能性があります。 これと表示されます両方、Reporting Services でのエラー ログとの web ポータルでレポートのサブスクリプションを編集する場合。

```
An error occurred within the report server database.  This may be due to a connection failure, timeout or low disk condition within the database.
``` 

問題断続的なをすることのみを表示する権限も、SQL エージェント タスクを作成したサーバーは、削除するか、項目を編集します。 上記のオプションのいずれかを行わない場合、操作は、ロード バランサーの SQL エージェント タスクを作成したサーバーへのすべてのサブスクリプションのリクエストが送信するときをのみ成功します。 
  
## <a name="to-install-the-first-report-server-instance"></a>最初のレポート サーバー インスタンスをインストールするには  
  
1.  配置の一部になる最初のレポート サーバー インスタンスをインストールします。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]をインストールする際に、[レポート サーバー インストール オプション] ページで **[サーバーを構成せずにインストールする]** オプションを選択します。  
  
2.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを起動します。  
  
3.  レポート サーバー Web サービス URL、Web ポータルの URL、およびレポート サーバー データベースを構成します。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「[レポート サーバーの構成 &#40;Reporting Services ネイティブ モード&#41;](../../reporting-services/report-server/configure-a-report-server-reporting-services-native-mode.md)」を参照してください。  
  
4.  レポート サーバーが稼働することを確認します。 詳細については、 [オンライン ブックの「](../../reporting-services/install-windows/verify-a-reporting-services-installation.md) Reporting Services のインストール状態の検証 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。  
  
## <a name="to-install-and-configure-the-second-report-server-instance"></a>2 番目のレポート サーバー インスタンスをインストールして構成するには  
  
1.  セットアップを実行し、2 番目の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスを別のコンピューターにインストールするか、同じコンピューターに名前付きインスタンスとしてインストールします。 Reporting Services をインストールする際に、[レポート サーバー インストール オプション] ページで **[サーバーを構成せずにインストールする]** オプションを選択します。  
  
2.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを起動し、インストールした新しいインスタンスに接続します。  
  
3.  最初のレポート サーバー インスタンスのときに使用したデータベースにレポート サーバーを接続します。  
  
    1.  **[データベース]** をクリックして、[データベース] ページを開きます。  
  
    2.  **[データベースの変更]**をクリックします。  
  
    3.  **[既存のレポート サーバー データベースを選択する]**をクリックします。  
  
    4.  使用するレポート サーバー データベースをホストする SQL Server データベース エンジン インスタンスのサーバー名を入力します。 前の作業で接続したサーバーの名前を入力する必要があります。  
  
    5.  **[接続テスト]**をクリックし、 **[次へ]**をクリックします。  
  
    6.  **[レポート サーバー データベース]**で、最初のレポート サーバー用に作成したデータベースを選択し、 **[次へ]**をクリックします。 既定の名前は ReportServer です。 ReportServerTempDB は選択しないでください。ReportServerTempDB は、レポート処理時に一時データを格納するためにのみ使用されます。 データベースの一覧が空の場合は、前の 4 つの手順を繰り返してサーバーへの接続を確立します。  
  
    7.  [資格情報] ページで、レポート サーバーがレポート サーバー データベースに接続する際に使用するアカウントと資格情報の種類を選択します。 最初のレポート サーバー インスタンスと同一の資格情報、または別の資格情報を使用できます。 [ **次へ**] を選択します。  
  
    8.  **[概要]** をクリックし、 **[完了]**をクリックします。  
  
4.  レポート サーバー **Web サービスの URL**を構成します。 URL のテストはまだ行わないでください。 URL は、レポート サーバーがスケールアウト配置に参加するまで解決されません。  
  
5.  **Web ポータルの URL**を構成します。 URL のテストや配置の確認はまだ行わないでください。 レポート サーバーは、スケールアウト配置に参加するまで使用できません。  
  
## <a name="to-join-the-second-report-server-instance-to-the-scale-out-deployment"></a>2 番目のレポート サーバー インスタンスをスケールアウト配置に追加するには  
  
1.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを開き、最初のレポート サーバー インスタンスに再接続します。 最初のレポート サーバーは、暗号化と暗号化解除の操作に対する初期化が既に行われています。そのため、このレポート サーバーを使用して、他のレポート サーバー インスタンスをスケールアウト配置に追加できます。  
  
2.  **[スケールアウト配置]** をクリックして、[スケールアウト配置] ページを開きます。 レポート サーバー データベースに接続されている各レポート サーバーに対応する 2 つのエントリが表示されます。 最初のレポート サーバー インスタンスは既に参加済みで、 2 番目のレポート サーバー インスタンスは "参加を待っています" になっているはずです。 このようなエントリが表示されない場合は、レポート サーバー データベースを使用するように構成および初期化されている最初のレポート サーバーに接続していることを確認してください。  
  
     ![スケール アウト配置 ページの部分のスクリーン ショット](../../reporting-services/install-windows/media/scaloutscreen.gif "スケール アウト配置 ページの部分のスクリーン ショット")  
  
3.  [スケールアウト配置] ページで、配置への参加を待機しているレポート サーバー インスタンスを選択し、 **[サーバーの追加]**をクリックします。  
  
    > [!NOTE]  
    >  **問題:** Reporting Services レポート サーバー インスタンスをスケールアウト配置に追加しようとすると、アクセス拒否のようなエラー メッセージが表示される場合があります。  
    >   
    >  **回避策:** 最初の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスからの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 暗号化キーをバックアップして、このキーを 2 番目の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーに復元します。 その後、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のスケールアウト配置に 2 番目のサーバーの追加を試行します。  
  
4.  これで、両方のレポート サーバー インスタンスが動作していることを確認できるようになります。 2 番目のインスタンスを確認するには、Reporting Services 構成ツールを使用してレポート サーバーに接続し、 **Web サービスの URL** または **Web ポータルの URL**をクリックします。  
  
 負荷分散されたサーバー クラスター内でレポート サーバーを実行する場合、追加の構成が必要です。 詳細については、「 [ネットワーク負荷分散クラスターにおけるレポート サーバーの構成](../../reporting-services/report-server/configure-a-report-server-on-a-network-load-balancing-cluster.md)」を参照してください。  

## <a name="next-steps"></a>次の手順

[サービス アカウントを構成します。](http://msdn.microsoft.com/library/25000ad5-3f80-4210-8331-d4754dc217e0)   
[URL を構成します。](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
[ネイティブ モード レポート サーバー データベースを作成します。](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
[レポート サーバー Url を構成します。](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
[レポート サーバー データベース接続を構成します。](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
[追加およびスケール アウト配置に対する暗号化キーを削除します。](../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md)   
[Reporting Services ネイティブ モードのレポート サーバーの管理](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)