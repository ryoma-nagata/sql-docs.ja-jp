---
title: remote query timeout サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- time limit for remote queries [SQL Server]
- remote query timeout option
ms.assetid: 888c8448-933b-41e3-8aa1-c206bc0cdb78
caps.latest.revision: 25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 715479a8995426645e4faba7b3da1bad8ae1710b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231922"
---
# <a name="configure-the-remote-query-timeout-server-configuration-option"></a>remote query timeout サーバー構成オプションの構成
  このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] remote query timeout [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。 **remote query timeout** オプションは、リモート操作を実行してから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がタイムアウトになるまでの時間 (秒単位) を指定します。このオプションの既定値は 600 で、10 分間の待機時間が見込まれています。 この値は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] によってリモート クエリとして開始された発信接続に適用されます。 この値は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]が受信したクエリには影響を与えません。 タイムアウトを無効にするには、値を 0 に設定します。 クエリは完了するまで待機します。  
  
 異種クエリの場合、 **remote query timeout** は、リモート プロバイダーが結果セットを待機する場合のクエリのタイムアウト時間を秒数で指定します。この値は、DBPROP_COMMANDTIMEOUT 行セット プロパティを使用してコマンド オブジェクトで初期化されます。また、リモート プロバイダーで DBPROP_GENERALTIMEOUT がサポートされている場合、この値は DBPROP_GENERALTIMEOUT の設定にも使用されます。 これによって、他の操作に対しても、指定した秒数の後にタイムアウトが適用されます。  
  
 リモート ストアド プロシージャの場合、 **remote query timeout** は、リモート `EXEC` ステートメントを送信してからリモート ストアド プロシージャがタイムアウトするまでの経過時間を指定します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [前提条件](#Prerequisites)  
  
     [Security](#Security)  
  
-   **以下を使用して remote query timeout オプションを構成するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **補足情報:**  [remote query timeout オプションを構成した後](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   この値を設定するには、あらかじめリモート サーバー接続が許可されている必要があります。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。 両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。 ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-configure-the-remote-query-timeout-option"></a>remote query timeout オプションを構成するには  
  
1.  オブジェクト エクスプローラーで、サーバーを右クリックし、 **[プロパティ]** をクリックします。  
  
2.  **[接続]** ノードをクリックします。  
  
3.  **[リモート サーバー接続]** の **[リモート クエリ タイムアウト]** ボックスで、0 ～ 2,147,483,647 の値を入力するか選択し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がタイムアウトするまでの最大秒数を設定します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-configure-the-remote-query-timeout-option"></a>remote query timeout オプションを構成するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 この例では、 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) を使用して `remote query timeout` オプションの値を `0` に設定し、タイムアウトを無効にする方法を示します。  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'remote query timeout', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)構成オプションを構成する方法について説明します。  
  
##  <a name="FollowUp"></a> 補足情報: remote query timeout オプションを構成した後  
 新しい設定は、サーバーを再起動しなくてもすぐに有効になります。  
  
## <a name="see-also"></a>参照  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [行セットのプロパティと動作](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
