---
title: データベース (SSRS ネイティブ モード) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.databasesetup.F1
ms.assetid: 8c9bb3b3-ea77-4a5b-ba35-7451ed11083d
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7bce0a9aa3adcddb7363224138a7ec3f51a47622
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37183939"
---
# <a name="database-ssrs-native-mode"></a>データベース (SSRS ネイティブ モード)
  [データベース] ページを使用すると、1 つまたは複数のレポート サーバー インスタンスに対して内部記憶域を提供するレポート サーバー データベースの作成や構成を行うことができます。 使用する必要があるリモート レポート サーバー データベースを使用するレポート サーバーを構成する場合、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager データベースを作成します。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード。  
  
 レポート サーバー データベースの作成と接続の構成は複数の手順から成る作業です。 このページには、タスクごとに各手順を示すウィザードが用意されています。 権限およびログインの作成または更新も行えます。 [進行状況] ページでは、各手順の状態を監視できます。 エラーが発生した場合は、そのエラーをクリックすることで、エラーの解決方法に関する情報を表示できます。  
  
 レポート サーバー データベースでは、特定のサーバー モードをサポートする必要があります。 既定のモードはネイティブ モードですが、SharePoint の製品またはテクノロジの大規模な配置でレポート サーバーを実行している場合は、SharePoint 統合モード用のレポート サーバー データベースを作成することもできます。 詳細については、「[ネイティブ モードのレポート サーバー データベースの作成 (SSRS 構成マネージャー)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)」を参照してください。  
  
 このページを開くには、開始、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager とクリック**データベース**ナビゲーション ウィンドウで。 詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。  
  
## <a name="options"></a>および  
 **SQL Server 名**  
 現在のレポート サーバー データベースに**SQL Server 名**の名前を指定します、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]レポート サーバー データベースを実行します。 ローカルまたはリモートのコンピューターの、既定または名前付きのインスタンスを使用できます。  
  
 **データベース名**  
 サーバー データを格納するレポート サーバー データベースの名前を指定します。  
  
 **レポート サーバー モード**  
 レポート サーバー データベースでネイティブ モードと SharePoint 統合モードのどちらをサポートするかを示します。 詳細については、次を参照してください。 [Reporting Services レポート サーバー](../../../2014/reporting-services/reporting-services-report-server.md)します。  
  
 **データベースの変更**  
 レポート サーバー データベースの作成または選択に必要なすべての手順を示すウィザードを起動します。  
  
 **資格情報の種類**  
 レポート サーバーがレポート サーバー データベースへの接続に使用する資格情報を指定します。 資格情報の種類を指定できますが、サービス アカウント、Windows ドメイン ユーザー、Windows のローカル ユーザーを含めるまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース ログインします。 資格情報の選択の詳細については、次を参照してください。[レポート サーバー データベース接続の構成&#40;SSRS 構成マネージャー&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)します。  
  
 **[ユーザー名]**  
 Windows 資格情報を使用している場合は、ドメイン ユーザー アカウントを指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用する場合、ログイン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資格情報。 Windows 資格情報を使用している場合、この形式でそれらを指定: *\<ドメイン >\\< アカウント\>* します。  
  
 **Password**  
 アカウントのパスワードを指定します。  
  
 **資格情報の変更**  
 別のアカウントを選択したり、レポート サーバー データベースへの接続に使用するアカウントのパスワードを更新するのに必要なすべての手順を示すウィザードを起動します。  
  
## <a name="see-also"></a>参照  
 [ネイティブ モード レポート サーバー データベースの作成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Reporting Services 構成マネージャーの F1 ヘルプ トピック&#40;SSRS ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [レポート サーバー データベース &#40;SSRS ネイティブ モード&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [レポート サーバー データベース接続の構成&#40;SSRS 構成マネージャー&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
