---
title: レポート サーバーと SharePoint の Power View の統合機能のアクティブ化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
caps.latest.revision: 5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 45266427e7946e62a758ce994531126324dca39d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155853"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>SharePoint でのレポート サーバーと Power View の統合機能のアクティブ化
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のサイト コレクション機能は、通常、SharePoint 製品用の [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] アドインをインストールすると、既定でアクティブ化されます。 場合によっては、この機能を手動でアクティブ化する必要があります。  
  
 SharePoint 製品のインストール後に SharePoint 2010 製品用の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインをインストールした場合、レポート サーバーの統合機能と Power View の統合機能はルート サイト コレクションでのみアクティブ化されます。 他のサイト コレクションについては、この機能を手動でアクティブ化する必要があります。 たとえば、サイト コレクションがある場合**http://[my サーバー名]/sites/[サイト コレクション名]** を手動でアクティブ化する必要があります、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]サイト コレクションの機能です。  
  
 ルート サイト コレクションが存在しない場合、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]アドインで、次のようなメッセージが記録されます。  
  
 "SharePoint Web アプリケーション 80 にはルート サイト コレクションがありません"  
  
 メッセージは、"RS_SP_#.log" (# は増加する値) という名前のアドイン インストール ログに記録されます。 ログ ファイルは、現在のユーザーの Temp フォルダー (例: C:\Users\\[user name]\AppData\Local\Temp) にあります。追加のログ オプションの詳細については、次を参照してください。[インストールまたは SharePoint 用 Reporting Services アドインのアンインストール&#40;SharePoint 2010 および SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)します。  
  
 このトピックの内容  
  
-   [レポート サーバーと Power View の統合サイト コレクション機能をアクティブ化するには](#bkmk_features)  
  
-   [Reporting Services の全体管理のサイト コレクション機能をアクティブ化または非アクティブ化するには](#bkmk_centraladmin)  
  
##  <a name="bkmk_features"></a> レポート サーバーと Power View の統合サイト コレクション機能をアクティブ化するには  
  
1.  ブラウザーで、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の機能をアクティブ化するサイトを開きます。  
  
2.  **[サイトの操作]** をクリックします。  
  
3.  **[サイトの設定]** をクリックします。  
  
4.  [サイト コレクションの管理] グループで **[サイト コレクションの機能]** をクリックします。  
  
5.  一覧で **[レポート サーバーの統合機能]** または **[Power View 統合機能]** を見つけます。  
  
6.  **[アクティブ化]** をクリックします。  
  
 機能を非アクティブ化するには、 **[アクティブ化]** ではなく **[非アクティブ化]** をクリックする点を除き、同じ手順を実行します。  
  
##  <a name="bkmk_centraladmin"></a> Reporting Services の全体管理のサイト コレクション機能をアクティブ化または非アクティブ化するには  
  
1.  ブラウザーで SharePoint サーバーの全体管理を開きます。  
  
2.  **[サイトの操作]** をクリックします。  
  
3.  **[サイトの設定]** をクリックします。  
  
4.  [サイト コレクションの管理] グループで **[サイト コレクションの機能]** をクリックします。  
  
5.  一覧で **[レポート サーバーの全体管理機能]** を見つけます。  
  
6.  **[アクティブ化]** をクリックします。  
  
 機能を非アクティブ化するには、 **[アクティブ化]** ではなく **[非アクティブ化]** をクリックする点を除き、同じ手順を実行します。  
  
## <a name="next-steps"></a>次の手順  
 機能をアクティブ化した後、サーバーの統合を続行できます。  
  
## <a name="see-also"></a>参照  
 [インストールまたはアンインストール、Reporting Services アドイン、SharePoint の&#40;SharePoint 2010 および SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
