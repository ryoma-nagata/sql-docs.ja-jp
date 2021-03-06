---
title: '[ログ配布モニターの設定] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.monitor.f1
ms.assetid: 45e2ba7d-b3aa-4643-9451-bcb991572314
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8485174c8880e90ac609cef9060bb194aae875c5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311852"
---
# <a name="log-shipping-monitor-settings"></a>[ログ配布モニターの設定]
  このページを使用すると、ログ配布監視サーバーのプロパティを構成および変更できます。  
  
 ログ配布の概念については、「[ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[監視サーバー インスタンス]**  
 ログ配布構成の監視サーバーとして現在構成されているサーバー インスタンスの名前を表示します。  
  
 **Connect**  
 監視サーバーとして使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを選択して接続します。 接続に使用するアカウントは、セカンダリ サーバーのインスタンスの sysadmin 固定サーバー ロールのメンバーである必要があります。  
  
 **[ジョブのプロキシ アカウントを借用する]**  
 監視サーバー インスタンスに接続するときに、ログ配布で SQL Server エージェントのプロキシ アカウントを借用します。 バックアップ、コピー、および復元プロセスでは、監視サーバーに接続してログ配布操作の状態を更新できなければなりません。  
  
 **[次の SQL Server ログインを使用する]**  
 監視サーバー インスタンスに接続するときに、ログ配布で特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを使用できるようにします。 バックアップ、コピー、および復元プロセスでは、監視サーバーに接続してログ配布操作の状態を更新できなければなりません。 ログ配布で特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを使用する場合にこのオプションを選択し、ログインおよびパスワードを指定します。  
  
 **[次の期間以後の履歴を削除する]**  
 ログ配布履歴情報を削除する前に、監視サーバー上に保持する期間を指定します。  
  
 **ジョブ名**  
 バックアップまたは復元しきい値が超過したときに、警告を発行するためにログ配布によって使用される SQL Server エージェントの警告ジョブの名前を示します。 このジョブを作成しているときは、ボックスに入力することで名前を変更できます。  
  
 **[スケジュール]**  
 SQL Server エージェントの警告ジョブの現在のスケジュールを示します。  
  
 **[編集]**  
 SQL Server エージェントの警告ジョブのパラメーターを変更します。  
  
 **[このジョブを無効にする]**  
 SQL Server エージェントの警告ジョブを中断します。  
  
  
