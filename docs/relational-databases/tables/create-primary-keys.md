---
title: 主キーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- primary keys [SQL Server], creating
ms.assetid: 85c623ca-4656-4d70-a9db-ee4d897cd214
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c25dc5d5d45b713f284cd6505db71320c0cf3234
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38980205"
---
# <a name="create-primary-keys"></a>主キーの作成
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 > 以前のバージョンの SQL Server に関連するコンテンツについては、「[主キーの作成](https://msdn.microsoft.com/library/ms189039(SQL.120).aspx)」を参照してください。

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して主キーを定義できます。 主キーを作成すると、指定に従って対応する一意なクラスター化または非クラスター化インデックスが自動的に作成されます。  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   テーブルに含めることができる PRIMARY KEY 制約は 1 つだけです。  
  
-   PRIMARY KEY 制約中で定義する列はすべて、NOT NULL として定義する必要があります。 NULL 値を許容するかどうかを指定しない場合、PRIMARY KEY 制約の影響を受けるすべての列は NOT NULL に設定されます。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 主キーが設定された、新しいテーブルを作成するには、データベースの CREATE TABLE 権限と、テーブルを作成するスキーマの ALTER 権限が必要です。  
  
 既存のテーブルに主キーを作成するには、テーブルに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-create-a-primary-key"></a>主キーを作成するには  
  
1.  オブジェクト エクスプローラーで、UNIQUE 制約を追加するテーブルを右クリックし **、[デザイン]** をクリックします。  
  
2.  **テーブル デザイナー**で、主キーとして定義するデータベース列の行セレクターをクリックします。 複数列を選択する場合は、Ctrl キーを押しながら、他の列の行セレクターをクリックします。  
  
3.  列の行セレクターを右クリックし、 **[主キーの設定]** をクリックします。  
  
> [!CAUTION]  
>  主キーを再定義する場合は、新しい主キーを作成する前に、既存の主キーに対するリレーションシップをすべて削除する必要があります。 再定義中に、既存のリレーションシップが自動的に削除されることを警告するメッセージが表示されます。  
  
 主キー列は、行セレクターに主キーの記号で示されます。  
  
 主キーが複数の列で構成される場合、1 つの列では重複した値が許可されますが、主キーのすべての列の値の組み合わせは一意である必要があります。  
  
 複合キーを定義する場合は、主キーの列の順序が、テーブルに表示される列の順序と同じになります。 ただし、主キー作成後に列の順序を変更することもできます。 詳細については、「 [主キーの変更](../../relational-databases/tables/modify-primary-keys.md)」を参照してください。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  

### <a name="to-create-a-primary-key-in-an-existing-table"></a>既存のテーブルに主キーを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 この例では、 `TransactionID`列で主キーを作成します。  
  
    ```sql  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Production.TransactionHistoryArchive   
    ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID);  
    GO  
    ```  
  
### <a name="to-create-a-primary-key-in-a-new-table"></a>新しいテーブルに主キーを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 次の例では、テーブルを作成して `TransactionID`列に主キーを定義します。  
  
    ```sql  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       TransactionID int IDENTITY (1,1) NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
    );  
    GO  
    ```  

### <a name="to-create-a-primary-key-with-nonclustered-index-in-a-new-table"></a>新しいテーブルに非クラスター化インデックスの主キーを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 次の例では、テーブルを作成して `CustomerID` 列に主キーを、`TransactionID` にクラスター化インデックスを定義します。  
  
    ```sql  
    -- Select appropriate database
    USE AdventureWorks2012;  
    GO  
    -- Create table to add the clustered index
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       CustomerID uniqueidentifier DEFAULT NEWSEQUENTIALID(),
       TransactionID int IDENTITY (1,1) NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY NONCLUSTERED (uniqueidentifier)  
    );  
    GO  

    -- Now add the clustered index
    CREATE CLUSTERED INDEX CIX_TransactionID ON Production.TransactionHistoryArchive1 (TransactionID);
    GO
    ```  

## <a name="see-also"></a>参照    
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)    
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)     
[table_constraint &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-table-constraint-transact-sql.md)    
