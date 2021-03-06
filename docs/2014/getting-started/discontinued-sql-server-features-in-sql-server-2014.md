---
title: 廃止された SQL Server 2014 における SQL Server 機能 |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0678bfbc-5d3f-44f4-89c0-13e8e52404da
caps.latest.revision: 28
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 99223e87f7d4488783ad76b355f38249d51a82af
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37322752"
---
# <a name="discontinued-sql-server-features-in-sql-server-2014"></a>SQL Server 2014 で提供が中止された機能
  このトピックでは、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] にアップグレードした後で使用できなくなる機能について説明します。  
  
## <a name="discontinued-features-in-includesssql14includessssql14-mdmd"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] で提供が中止された機能はありません。  
  
## <a name="discontinued-features-in-includesssql11includessssql11-mdmd"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="discontinued-active-directory-helper-service"></a>Active Directory Helper サービスの提供中止  
 Active Directory Helper サービスおよびその関連コンポーネントは、削除されました。 次の表は、削除された関連コンポーネントの一覧を示しています。  
  
|カテゴリ|提供が中止された機能|代替|  
|--------------|--------------------------|-----------------|  
|システム ストアド プロシージャ|sp_ActiveDirectory_Obj<br /><br /> sp_ActiveDirectory_SCP<br /><br /> sp_ActiveDirectory_Start|使用可能な交換はありません。|  
  
## <a name="discontinued-features-in-sql-server-2008-r2"></a>SQL Server 2008 R2 で提供が中止された機能  
  
### <a name="64-bit-platform-support-in-reporting-services"></a>Reporting Services での 64 ビット プラットフォームのサポート  
 以降では[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]コンポーネントは、Windows Server 2003 または Windows Server 2003 R2 を実行している Itanium ベースのサーバーをサポートしていません。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、Itanium ベース システム用の Windows Server 2008 や Itanium ベース システム用の Windows Server 2008 R2 などの他の 64 ビット オペレーティング システムは引き続きサポートされます。 Windows Server 2003 または Windows Server 2003 R2 の Itanium ベース システム エディションにインストールされた [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] を [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] にアップグレードするには、まずオペレーティング システムをアップグレードする必要があります。  
  
## <a name="discontinued-features-in-sql-server-2008"></a>SQL Server 2008 で提供が中止された機能  
  
### <a name="discontinued-sql-dmo-from-sql-server-express-installation"></a>SQL Server Express で提供が中止された SQL-DMO  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の SQL-DMO が [!INCLUDE[ssExpressEd10](../includes/ssexpressed10-md.md)] から削除されました。 この機能を現在使用しているアプリケーションはできるだけ早く変更することをお勧めします。 SQL-DMO をサポートする必要がある場合[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]から旧バージョンとの互換性コンポーネントを Express をインストール、 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] feature pack から、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=51230)します。 新しい開発作業では、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) を使用してください。  
  
### <a name="discontinued-option-for-web-assistant"></a>廃止された Web Assistant オプション  
 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] では、Web Assistant を有効にする `sp_configure` オプションが削除されました。 代わりに [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] を使用することをお勧めします。  
  
### <a name="surface-area-configuration-tool"></a>Surface Area Configuration ツール  
 セキュリティ構成ツールが廃止されました[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]します。 以下の表に、このリリースの設定、オプション、およびコンポーネントの機能を構成する際に使用できる方法を示します。  
  
|置換の設定とコンポーネントの機能|構成方法|  
|-------------------------------------------------|----------------------|  
|プロトコル、接続、およびスタートアップ オプション|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーを使用します。|  
|[!INCLUDE[ssDE](../includes/ssde-md.md)] 機能|ポリシー ベースの管理、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のプロパティ設定、または sp_configure を使用します。|  
|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 機能|[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のプロパティ設定を使用します。|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Enableintegratedsecurity プロパティ|[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のプロパティ設定を使用します。|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -「定期的なイベントおよびレポート配信」および"Web サービスおよび HTTP アクセス"|RSReportServer.config 構成ファイルを編集します。|  
|コマンド ライン オプション|このリリースではサポートされません。|  
|SOAP および [!INCLUDE[ssSB](../includes/sssb-md.md)] のエンドポイント|使用[CREATE ENDPOINT](/sql/t-sql/statements/create-endpoint-transact-sql)と[ALTER ENDPOINT](/sql/t-sql/statements/alter-endpoint-transact-sql)します。|  
  
### <a name="discontinued-command-prompt-parameters-for-sql-server-setup"></a>SQL Server のセットアップで廃止されたコマンド プロンプト パラメーター  
 次の表に、以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のセットアップ コマンド プロンプト パラメーターのうち、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] でサポートされていないものを示します。  
  
|廃止されたパラメーター|新しいパラメーター|  
|----------------------------|---------------------------|  
|ADDLOCAL|/ACTION=Uninstall および /FEATURES|  
|DISABLENETWORKPROTOCOLS|TCP/IP の場合は/TCPENABLED<sup>1</sup>|  
|DISABLENETWORKPROTOCOLS|名前付きパイプの場合は/NPENABLED<sup>1</sup>|  
|INSTALLSQLDATADIR|/SQLUSERDBDIR<br /><br /> /SQLUSERDBLOGDIR<br /><br /> /SQLBACKUPDIR<br /><br /> /SQLTEMPDBDIR<br /><br /> /SQLTEMPDBLOGDIR|  
|REINSTALL|このリリースに該当する機能はありません。|  
|REINSTALLMODE|このリリースに該当する機能はありません。|  
|REMOVE|/ACTION=Uninstall および /FEATURES|  
|SAMPLEDATABASE|このリリースに該当する機能はありません。|  
|SAVESYSDB|このリリースに該当する機能はありません。|  
|SKUUPGRADE<sup>2</sup>|このリリースに該当する機能はありません。|  
|UPGRADE|/ACTION=Upgrade および /FEATURES|  
|USESYSDB|このリリースに該当する機能はありません。|  
  
 <sup>1</sup>これらのパラメーターはインストールでのみ有効です。  
  
 <sup>2</sup>開始[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]、/Action を指定の既存のエディションをアップグレードする、EditionUpgrade =[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に元のインストール メディアを使用せず、いつでも別のエディション。 サポートされるバージョンとエディションのアップグレードについては、「 [Supported Version and Edition Upgrades](../database-engine/install-windows/supported-version-and-edition-upgrades.md)」を参照してください。  
  
 詳細については、「[コマンド プロンプトからの SQL Server 2014 のインストール](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)」を参照してください。  
  
  
