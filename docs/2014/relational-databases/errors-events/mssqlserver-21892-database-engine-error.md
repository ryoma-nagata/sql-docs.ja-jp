---
title: MSSQLSERVER_21892 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 21892 (Database Engine error)
ms.assetid: 199818e8-28f4-440e-ad85-7bea88f51153
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a01f07cdfb20ed88a43dbda2b555e819ca725c0b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414321"
---
# <a name="mssqlserver21892"></a>MSSQLSERVER_21892
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21892|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLErrorNum21892|  
|メッセージ テキスト|仮想ネットワーク名 '%s' にプライマリとして関連付けられた可用性グループにある sys.availability_replicas で、メンバー レプリカのサーバー名をクエリすることができません。エラー = %d、エラー メッセージ = '%s'。|  
  
## <a name="explanation"></a>説明  
 `sp_validate_replica_hosts_as_publishers` は、リダイレクトされたパブリッシャーに関連付けられている可用性グループの現在のプライマリにクエリを実行し、メンバー レプリカをホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを特定します。  このクエリが失敗すると、エラー 21892 が返されます。  
  
 `sp_validate_replica_hosts_as_publishers` は通常、一時リンク サーバーを最初に使用するため、接続の問題がある場合は `sp_validate_replica_hosts_as_publishers` で初めて問題が現れる可能性があります。 `sp_validate_redirected_publisher` と異なり、`sp_validate_replica_hosts_as_publishers` が使用するリンク サーバーは、いずれかの可用性グループ レプリカ ホストに接続するときに常に呼び出し元の資格情報を使用します。  
  
## <a name="user-action"></a>ユーザーの操作  
 このストアド プロシージャを実行する場合は、レプリカのすべてに対して有効なログインから実行してください。 ログインには、可用性グループのメタデータ テーブルにクエリを実行し、パブリッシャー データベース レプリカのサブスクリプション メタデータ データベースにクエリを実行するための十分な権限が必要になります。  
  
 参照される元のエラーを確認し、エラーの原因と適切な修正措置を特定します。  
  
  
