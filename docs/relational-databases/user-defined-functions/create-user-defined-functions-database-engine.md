---
title: ユーザー定義関数の作成 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 11/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: udf
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SCHEMABINDING clause
- schema-bound functions [SQL Server]
- user-defined functions [SQL Server], creating
- CREATE FUNCTION statement
- valid statements [SQL Server]
ms.assetid: f0d5dd10-73fd-4e05-9177-07f56552bdf7
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: cdfdc6fc8e6498a713277dc71d02636782e22f8b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37418141"
---
# <a name="create-user-defined-functions-database-engine"></a>ユーザー定義関数の作成 (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してユーザー定義関数 (UDF) を作成する方法について説明します。  

  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   ユーザー定義関数は、データベースの状態を変更するアクションの実行に使用することはできません。  
  
-   出力先がテーブルである OUTPUT INTO 句をユーザー定義関数に含めることはできません。  
  
-   ユーザー定義関数では複数の結果セットは返せません。 複数の結果セットを返す必要がある場合は、ストアド プロシージャを使用します。  
  
-   エラー処理は、ユーザー定義の関数では制限されます。 UDF では、TRY…CATCH、@ERROR、または RAISERROR をサポートしていません。  
  
-   ユーザー定義関数はストアド プロシージャを呼び出すことができませんが、拡張ストアド プロシージャを呼び出すことはできます。  
  
-   ユーザー定義関数では、動的 SQL または一時テーブルを利用することはできません。 テーブル変数は使用できます。  
  
-   SET ステートメントはユーザー定義関数では使用できません。  
  
-   FOR XML 句は使用できません。  
  
-   ユーザー定義関数は入れ子にすることができます。つまり、1 つのユーザー定義関数で、別のユーザー定義関数を呼び出すことができます。 呼び出された関数が実行を開始すると入れ子レベルが 1 つ上がり、呼び出された関数が実行を終了するとレベルが 1 つ下がります。 ユーザー定義関数は、32 レベルまで入れ子にすることができます。 入れ子レベルが最大値を超えると、関数チェーン全体の呼び出しが失敗します。 Transact-SQL ユーザー定義関数からマネージド コードへの参照は、32 レベルの入れ子制限のうちの 1 レベルとカウントします。 マネージド コード内から呼び出されたメソッドは、この制限としてはカウントされません。  
  
-   以下の Service Broker ステートメントは、Transact-SQL ユーザー定義関数の定義に **含めることができません** 。  
  
    -   BEGIN DIALOG CONVERSATION  
  
    -   END CONVERSATION  
  
    -   GET CONVERSATION GROUP  
  
    -   MOVE CONVERSATION  
  
    -   RECEIVE  
  
    -   SEND  
  
###  <a name="Security"></a> 権限 

データベースの CREATE FUNCTION 権限と、関数を作成するスキーマの ALTER 権限が必要です。 関数でユーザー定義型が指定されている場合は、その型に対する EXECUTE 権限が必要です。  
  
##  <a name="Scalar"></a> スカラー関数  
 次の例では、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースに複数ステートメントのスカラー関数を作成します。 この関数は、1 つの入力値 `ProductID`を受け取り、単一のデータ値 (在庫品目中の指定された製品に関する集計量) を返します。  
  
```sql  
IF OBJECT_ID (N'dbo.ufnGetInventoryStock', N'FN') IS NOT NULL  
    DROP FUNCTION ufnGetInventoryStock;  
GO  
CREATE FUNCTION dbo.ufnGetInventoryStock(@ProductID int)  
RETURNS int   
AS   
-- Returns the stock level for the product.  
BEGIN  
    DECLARE @ret int;  
    SELECT @ret = SUM(p.Quantity)   
    FROM Production.ProductInventory p   
    WHERE p.ProductID = @ProductID   
        AND p.LocationID = '6';  
     IF (@ret IS NULL)   
        SET @ret = 0;  
    RETURN @ret;  
END; 
```  
  
 次に、 `ufnGetInventoryStock` 関数を使用して、 `ProductModelID` が 75 ～ 80 の製品の現在の在庫量を返す例を示します。  
  
```sql  
SELECT ProductModelID, Name, dbo.ufnGetInventoryStock(ProductID)AS CurrentSupply  
FROM Production.Product  
WHERE ProductModelID BETWEEN 75 and 80;  
```  
  
##  <a name="TVF"></a> テーブル値関数  
 次の例では、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースにインライン テーブル値関数を作成します。 この関数は、入力パラメーターとして 1 つの顧客 (商店) ID を受け取り、 `ProductID`列と `Name`列、および過去 1 年間の集計である `YTD Total` を商店に販売した製品ごとに返します。  
  
```sql  
IF OBJECT_ID (N'Sales.ufn_SalesByStore', N'IF') IS NOT NULL  
    DROP FUNCTION Sales.ufn_SalesByStore;  
GO  
CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
RETURNS TABLE  
AS  
RETURN   
(  
    SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
    FROM Production.Product AS P   
    JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
    JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
    JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
    WHERE C.StoreID = @storeid  
    GROUP BY P.ProductID, P.Name  
);  
```  
  
 次の例では、この関数を呼び出して顧客 ID 602 を指定します。  
  
```sql  
SELECT * FROM Sales.ufn_SalesByStore (602);  
```  
  
 次の例では、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースにテーブル値関数を作成します。 この関数は、単一の入力パラメーター `EmployeeID` を受け取り、指定された従業員の直接または間接の部下であるすべての従業員の一覧を返します。 関数が呼び出され、従業員 ID 109 を指定します。  
  
```sql  
IF OBJECT_ID (N'dbo.ufn_FindReports', N'TF') IS NOT NULL  
    DROP FUNCTION dbo.ufn_FindReports;  
GO  
CREATE FUNCTION dbo.ufn_FindReports (@InEmpID INTEGER)  
RETURNS @retFindReports TABLE   
(  
    EmployeeID int primary key NOT NULL,  
    FirstName nvarchar(255) NOT NULL,  
    LastName nvarchar(255) NOT NULL,  
    JobTitle nvarchar(50) NOT NULL,  
    RecursionLevel int NOT NULL  
)  
--Returns a result set that lists all the employees who report to the   
--specific employee directly or indirectly.*/  
AS  
BEGIN  
WITH EMP_cte(EmployeeID, OrganizationNode, FirstName, LastName, JobTitle, RecursionLevel) -- CTE name and columns  
    AS (  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, 0 -- Get the initial list of Employees for Manager n  
        FROM HumanResources.Employee e   
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        WHERE e.BusinessEntityID = @InEmpID  
        UNION ALL  
        SELECT e.BusinessEntityID, e.OrganizationNode, p.FirstName, p.LastName, e.JobTitle, RecursionLevel + 1 -- Join recursive member to anchor  
        FROM HumanResources.Employee e   
            INNER JOIN EMP_cte  
            ON e.OrganizationNode.GetAncestor(1) = EMP_cte.OrganizationNode  
INNER JOIN Person.Person p   
ON p.BusinessEntityID = e.BusinessEntityID  
        )  
-- copy the required columns to the result of the function   
   INSERT @retFindReports  
   SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
   FROM EMP_cte   
   RETURN  
END;  
GO  
-- Example invocation  
SELECT EmployeeID, FirstName, LastName, JobTitle, RecursionLevel  
FROM dbo.ufn_FindReports(1);  
```  
  
## <a name="more-examples"></a>他の例について  
 - [ユーザー定義関数](../../relational-databases/user-defined-functions/user-defined-functions.md)   
 - [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md) 
 - [ALTER FUNCTION (Transact SQL)](../../tools/sql-server-profiler/start-sql-server-profiler.md) 
 - [DROP FUNCTION (Transact SQL)](../../tools/sql-server-profiler/start-sql-server-profiler.md)
 - [DROP PARTITION FUNCTION (Transact SQL)](https://msdn.microsoft.com/library/ms187759(SQL.130).aspx)
 - [コミュニティ](https://www.bing.com/search?q=user%20defined%20function%20%22sql%20server%202016%22%20examples&qs=n&form=QBRE&pq=user%20defined%20function%20%22sql%20server%202016%22%20examples&sc=0-48&sp=-1&sk=&cvid=C3AD337125A840AD9EEFA3AAC36A3712)のその他の例
  
