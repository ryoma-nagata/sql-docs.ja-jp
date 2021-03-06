---
title: レポート サーバーのコマンド プロンプト ユーティリティ (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- rsconfig utility
- components [Reporting Services], command line utilities
- rs utility
- command prompt utilities [Reporting Services]
- rskeymgmt utility
ms.assetid: 68f2f9f4-f894-40ff-a71c-f9756bf4b68c
caps.latest.revision: 48
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 637b1a53587f8b0405842a7f228ba7a380a1621f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265738"
---
# <a name="report-server-command-prompt-utilities-ssrs"></a>レポート サーバーのコマンド プロンプト ユーティリティ (SSRS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、レポート サーバーの管理に使用できるいくつかのコマンド ライン ユーティリティがあります。 これらのユーティリティは、レポート サーバーをインストールする際に自動的にインストールされます。  
  
|名前|コマンド ファイル|サポートされる配置モード|説明|  
|----------|------------------|-------------------------------|-----------------|  
|RSS ユーティリティ|rs.exe (rs.exe)|ネイティブ モードと SharePoint モード。 SharePoint モードのサポートは [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] リリースで導入されました。|[rs ユーティリティ](rs-exe-utility-ssrs.md) は、スクリプト操作の実行に使用できるスクリプト ホストです。 このツールを使用して、レポート サーバー データベース間でのデータのコピー、レポートのパブリッシュ、レポート サーバー データベースでのアイテムの作成などを行う [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] スクリプトを実行します。 スクリプトを使用してサーバーを管理する方法の詳細については、「 [配置タスクおよび管理タスクのスクリプト作成](script-deployment-and-administrative-tasks.md)」を参照してください。|  
|PowerShell コマンドレット||SharePoint のみ|一覧については、powershell コマンドレットでは、次を参照してください。 [Reporting Services SharePoint モード用の PowerShell コマンドレット](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md)します。|  
|rsconfig ユーティリティ (rsconfig utility)|rsconfig.exe (rsconfig.exe)|ネイティブのみ|[Rsconfig ユーティリティ](rsconfig-utility-ssrs.md)構成およびレポート サーバー データベースへのレポート サーバー接続を管理するために使用します。 これを使用して、自動レポート処理に使用するユーザー アカウントを指定することもできます。 詳細については、「[Reporting Services レポート サーバー &#40;ネイティブ モード&#41;](../report-server/reporting-services-report-server-native-mode.md)」を参照してください。 接続の構成の詳細については、「[レポート サーバー データベース接続の構成 &#40;SSRS 構成マネージャー&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)」を参照してください。|  
|Rskeymgmt ユーティリティ|rskeymgmt.exe|ネイティブのみ|[Rskeymgmt ユーティリティ](rskeymgmt-utility-ssrs.md)は、暗号化キーの管理ツールです。 このツールを使用して、対称キーのバックアップ、適用、再作成、および削除を行うことができます。 このツールを使用して、レポート サーバー インスタンスを共有レポート サーバー データベースにアタッチすることもできます。 Rskeymgmt は、データベース復旧操作で使用できます。 対称キーのバックアップ コピーを適用すると、新しいインストールで既存のデータベースを再利用できます。 キーを復元できない場合、使用しなくなった暗号化された内容を削除できます。 キーの管理と機密データの保存に関する詳細については、「[暗号化されたレポート サーバー データの格納 &#40;SSRS 構成マネージャー&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)」と「[暗号化キーの構成と管理 &#40;SSRS 構成マネージャー&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md)」を参照してください。|  
  
> [!NOTE]  
>  代わりに、Reporting Services 構成マネージャーを使用することができますグラフィカル ユーザー インターフェイスを持つツールを使用する場合は、`rsconfig`と`rskeymgmt`します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成マネージャー&#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services ツール](reporting-services-tools.md)   
 [Reporting Services レポート サーバー &#40;ネイティブ モード&#41;](../report-server/reporting-services-report-server-native-mode.md)  
  
  
