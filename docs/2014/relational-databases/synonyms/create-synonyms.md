---
title: シノニムの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.synonym.general.f1
helpviewer_keywords:
- creating synonyms
- synonyms [SQL Server], creating
ms.assetid: fedfa7a5-d0b6-4e2b-90f4-a08122958e33
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6c99c9687205e04005756bd0946d1657d712a6dc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240472"
---
# <a name="create-synonyms"></a>シノニムの作成
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、シノニムを作成する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **次を使用してシノニムを作成するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
 ユーザーが特定のスキーマ内にシノニムを作成するには、CREATE SYNONYM 権限が必要であり、さらにスキーマを所有しているか ALTER SCHEMA 権限が与えられている必要があります。 CREATE SYNONYM 権限は、譲与可能な権限です。  
  
####  <a name="Permissions"></a> Permissions  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-create-a-synonym"></a>シノニムを作成するには  
  
1.  **オブジェクト エクスプローラー**で、新しいビューを作成するデータベースを展開します。  
  
2.  **[シノニム]** フォルダーを右クリックし、 **[新しいシノニム]** をクリックします。  
  
3.  **[シノニムの追加]** ダイアログ ボックスで、次の情報を入力します。  
  
     **[シノニム名]**  
     このオブジェクトに対して使用する新しい名前を入力します。  
  
     **[シノニム スキーマ]**  
     このオブジェクトに対して使用する新しい名前のスキーマを入力します。  
  
     **サーバー名**  
     接続するサーバー インスタンスを入力します。  
  
     **データベース名**  
     オブジェクトを含んでいるデータベースを入力または選択します。  
  
     **[スキーマ]**  
     オブジェクトを所有しているスキーマを入力または選択します。  
  
     **オブジェクトの種類**  
     オブジェクトの型を選択します。  
  
     **オブジェクト名です。**  
     シノニムで参照するオブジェクトの名前を入力します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-create-a-synonym"></a>シノニムを作成するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース内の既存のテーブルに対してシノニムを作成します。 このシノニムは、その後の例で使用されます。  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyAddressType  
FOR AdventureWorks2012.Person.AddressType;  
GO  
```  
  
 次の例では、 `MyAddressType` シノニムの参照先のベース テーブルに行を挿入しています。  
  
```  
USE tempdb;  
GO  
INSERT INTO MyAddressType (Name)  
VALUES ('Test');  
GO  
```  
  
 次の例では、動的 SQL でのシノニムの参照方法を示しています。  
  
```  
USE tempdb;  
GO  
EXECUTE ('SELECT Name FROM MyAddressType');  
GO  
```  
  
  
