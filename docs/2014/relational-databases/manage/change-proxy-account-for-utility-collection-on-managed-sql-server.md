---
title: SQL Server (SQL Server ユーティリティ) のマネージ インスタンスでユーティリティ コレクションのプロキシ アカウントの設定の変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d41abfdc155288e8140f0a69911829d33a891223
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37248402"
---
# <a name="change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server-sql-server-utility"></a>SQL Server のマネージド インスタンスにおけるユーティリティ コレクション セットのプロキシ アカウントの変更 (SQL Server ユーティリティ)
  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のマネージド インスタンスでユーティリティ コレクション セットのプロキシ アカウントを変更する方法について説明します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server"></a>SQL Server のマネージド インスタンスにおけるユーティリティ コレクション セットのプロキシ アカウントを変更するには  
  
1.  ph x="1" /&gt; のマネージド インスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティから削除します。  
  
    -   SSMS の **ユーティリティ エクスプローラー** で **[マネージド インスタンス]** ノードをクリックします。  
  
    -   
  **ユーティリティ エクスプローラー** のリスト ビューで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前を右クリックし、 **[マネージド インスタンスの削除]** をクリックします。 詳細については、「 [SQL Server ユーティリティからの SQL Server のインスタンスの削除](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)」を参照してください。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに再度登録します。  
  
    -   SSMS の **ユーティリティ エクスプローラー** で、 **[マネージド インスタンス]** ノードを右クリックし、 **[マネージド インスタンスの追加]** をクリックします。  
  
    -   新しいプロキシ アカウントを指定して、画面の指示に従ってウィザードを完了します。  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md)   
 [SQL Server ユーティリティのトラブルシューティング](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
