---
title: DATEDIFF (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATEDIFF_TSQL
- DATEDIFF
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- DATEDIFF function [SQL Server]
- time [SQL Server], crossed boundaries
- differences in date and time [SQL Server]
- counting crossed date time boundaries [SQL Server]
- date and time [SQL Server], DATEDIFF
- dates [SQL Server], crossed boundaries
- boundary differences date and time [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- interval dates [SQL Server]
- time [SQL Server], functions
- crossing date time boundaries [SQL Server]
- calculating dates times [SQL Server]
ms.assetid: eba979f2-1a8d-4cce-9d75-b74f9b519b37
caps.latest.revision: 52
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 73175b2174c03ed917d4eaa5ab87403827e89ea0
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37784343"
---
# <a name="datediff-transact-sql"></a>DATEDIFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

この関数は、*startdate* と *enddate* で指定された 2 つの日付間の差を、指定された datepart 境界の数で (符号付き整数値として) で返します。
  
*startdate* 値と *enddate* 値の間のより大きな差を処理する関数については、「[DATEDIFF_BIG &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-big-transact-sql.md)」を参照してください。 [!INCLUDE[tsql](../../includes/tsql-md.md)] の日付と時刻のあらゆるデータ型と関数に関する概要については、「[日付と時刻のデータ型および関数 &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)」を参照してください。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DATEDIFF ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>引数  
*datepart*  
*startdate* と *enddate* の差を求めるときの単位に使用する要素を指定します。 `DATEDIFF` では、ユーザー定義変数に相当するものは受け入れられません。 この表には、有効な *datepart* 引数をすべて一覧表示しています。
  
|*datepart*|省略形|  
|---|---|
|**year**|**yy、yyyy**|  
|**quarter**|**qq, q**|  
|**month**|**mm, m**|  
|**dayofyear**|**dy、y**|  
|**day**|**dd, d**|  
|**week**|**wk, ww**|  
|**hour**|**mm**|  
|**minute**|**mi、n**|  
|**second**|**ss, s**|  
|**millisecond**|**ms**|  
|**microsecond**|**mcs**|  
|**nanosecond**|**ns**|  
  
*startdate*  
次のいずれかの値に解決できる式。

+ **date**
+ **datetime**
+ **datetimeoffset**
+ **datetime2** 
+ **smalldatetime**
+ **time**
  
4 桁の西暦を使用して、あいまいさを排除します。 2 桁の西暦値については、「[two digit year cutoff サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md)」を参照してください。
  
*enddate*  
「*startdate*」をご覧ください。
  
## <a name="return-type"></a>戻り値の型  
 **int**  
  
## <a name="return-value"></a>戻り値  
  
-   特定の各 *datepart* と、その *datepart* の省略形では、同じ値が返されます。  
  
**int** の範囲 (-2,147,483,648 から +2,147,483,647) を超える戻り値の場合、`DATEDIFF` はエラーを返します。  **millisecond** の場合、*startdate* と *enddate* の差の最大値は 24 日 20 時間 31 分 23.647 秒です。 **second** の場合、差の最大値は 68 年です。
  
*startdate* と *enddate* の両方に時刻値のみが割り当てられており、*datepart* が時刻の *datepart* でない場合、`DATEDIFF` は 0 を返します。
  
`DATEDIFF` では、戻り値を計算する際に、*startdate* または *enddate* のタイム ゾーン オフセット要素を使用しません。
  
[smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) の精度は分単位までなので、*startdate* または **enddate** に *smalldatetime* 値を使用した場合、戻り値では秒とミリ秒が常に 0 に設定されます。
  
日付データ型の変数に時刻値のみが割り当てられている場合、`DATEDIFF` では、欠落している日付要素の値が既定値である 1900-01-01 に設定されます。 時刻データ型または日付データ型の変数に日付値のみが割り当てられている場合、`DATEDIFF` では、欠落している時刻要素の値が既定値である 00:00:00 に設定されます。 *startdate* または *enddate* のいずれか一方が時刻要素のみで、もう一方が日付要素のみであった場合、`DATEDIFF` では、欠落している時刻要素と日付要素がそれぞれの既定値に設定されます。
  
*startdate* と *enddate* で異なる日付データ型が使用されており、一方の時刻要素の数または秒の小数部の有効桁数が、もう一方のデータ型を超えている場合、`DATEDIFF` では、欠落している要素が 0 に設定されます。
  
## <a name="datepart-boundaries"></a>datepart の差  
次の各ステートメントには、すべて同じ *startdate* と *enddate* の値が指定されています。 これらの日付は隣接しており、時間的な差は .0000001 秒です。 各ステートメントにおける *startdate* と *enddate* の差は、どの要素をとっても、*datepart* の 1 単位分となるように配慮されています。 いずれのステートメントも戻り値は 1 です。 *startdate* と *enddate* の年の値は異なるが、カレンダー週の値が同じである場合、`DATEDIFF` では、*datepart* **week** に対して 0 を返します。
  
```sql
SELECT DATEDIFF(year,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(quarter,     '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(month,       '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(dayofyear,   '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(day,         '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(week,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(hour,        '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(minute,      '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(second,      '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Remarks  
`DATEDIFF` は、SELECT <list>、WHERE、HAVING、GROUP BY、および ORDER BY 句で使用します。
  
`DATEDIFF` は、文字列リテラルを **datetime2** 型として暗黙的にキャストします。 つまり、`DATEDIFF` では、日付が文字列として渡される場合、YDM 形式がサポートされません。 文字列を明示的にキャストする必要があります、 **datetime** または **smalldatetime** YDM 形式を使用する型。
  
SET DATEFIRST を指定しても `DATEDIFF` に影響はありません。 `DATEDIFF` では、週の最初の曜日として常に日曜日を使用し、関数が決定的な方法で動作するようにします。
  
## <a name="examples"></a>使用例  
次の例では、*startdate* パラメーターと *enddate* パラメーターの引数として、各種の式を使用しています。
  
### <a name="a-specifying-columns-for-startdate-and-enddate"></a>A. startdate と enddate に列を指定する  
この例では、テーブルの 2 つの列に日付を格納し、両者の差を日単位で計算しています。
  
```sql
CREATE TABLE dbo.Duration  
    (startDate datetime2, endDate datetime2);  
    
INSERT INTO dbo.Duration(startDate, endDate)  
    VALUES ('2007-05-06 12:10:09', '2007-05-07 12:10:09');  
    
SELECT DATEDIFF(day, startDate, endDate) AS 'Duration'  
    FROM dbo.Duration;  
-- Returns: 1  
```  
  
### <a name="b-specifying-user-defined-variables-for-startdate-and-enddate"></a>B. startdate と enddate にユーザー定義変数を指定する  
この例では、ユーザー定義変数が *startdate* と *enddate* の引数として機能します。
  
```sql
DECLARE @startdate datetime2 = '2007-05-05 12:10:09.3312722';  
DECLARE @enddate   datetime2 = '2007-05-04 12:10:09.3312722';   
SELECT DATEDIFF(day, @startdate, @enddate);  
```  
  
### <a name="c-specifying-scalar-system-functions-for-startdate-and-enddate"></a>C. startdate と enddate にスカラー システム関数を指定する  
この例では、*startdate* と *enddate* の引数としてスカラー システム関数を使用しています。
  
```sql
SELECT DATEDIFF(millisecond, GETDATE(), SYSDATETIME());  
```  
  
### <a name="d-specifying-scalar-subqueries-and-scalar-functions-for-startdate-and-enddate"></a>D. startdate と enddate にスカラー サブクエリおよびスカラー関数を指定する  
この例では、*startdate* と *enddate* の引数として、サブクエリとスカラー関数を使用しています。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day,
    (SELECT MIN(OrderDate) FROM Sales.SalesOrderHeader),  
    (SELECT MAX(OrderDate) FROM Sales.SalesOrderHeader));  
```  
  
### <a name="e-specifying-constants-for-startdate-and-enddate"></a>E. startdate と enddate に定数を指定する  
この例では、*startdate* と *enddate* の引数として文字定数を使用しています。
  
```sql
SELECT DATEDIFF(day,
   '2007-05-07 09:53:01.0376635',
   '2007-05-08 09:53:01.0376635');  
```  
  
### <a name="f-specifying-numeric-expressions-and-scalar-system-functions-for-enddate"></a>F. enddate に数値式およびスカラー システム関数を指定する  
この例では、*enddate* の引数として、数値式 `(GETDATE() + 1)` のほか、スカラー システム関数 `GETDATE` および `SYSDATETIME` を使用しています。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635', GETDATE() + 1)   
    AS NumberOfDays  
    FROM Sales.SalesOrderHeader;  
GO  
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635', DATEADD(day, 1, SYSDATETIME())) AS NumberOfDays  
    FROM Sales.SalesOrderHeader;  
GO  
```  
  
### <a name="g-specifying-ranking-functions-for-startdate"></a>G. startdate に順位付け関数を指定する  
この例では、*startdate* の引数として順位付け関数を使用しています。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName  
    ,DATEDIFF(day, ROW_NUMBER() OVER (ORDER BY   
        a.PostalCode), SYSDATETIME()) AS 'Row Number'  
FROM Sales.SalesPerson s   
    INNER JOIN Person.Person p   
        ON s.BusinessEntityID = p.BusinessEntityID  
    INNER JOIN Person.Address a   
        ON a.AddressID = p.BusinessEntityID  
WHERE TerritoryID IS NOT NULL   
    AND SalesYTD <> 0;  
```  
  
### <a name="h-specifying-an-aggregate-window-function-for-startdate"></a>H. startdate に集計関数を指定する  
この例では、*startdate* の引数として集計関数を使用しています。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT soh.SalesOrderID, sod.ProductID, sod.OrderQty, soh.OrderDate,
    DATEDIFF(day, MIN(soh.OrderDate)   
        OVER(PARTITION BY soh.SalesOrderID), SYSDATETIME()) AS 'Total'  
FROM Sales.SalesOrderDetail sod  
    INNER JOIN Sales.SalesOrderHeader soh  
        ON sod.SalesOrderID = soh.SalesOrderID  
WHERE soh.SalesOrderID IN(43659, 58918);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
次の例では、*startdate* パラメーターと *enddate* パラメーターの引数として、各種の式を使用しています。
  
### <a name="i-specifying-columns-for-startdate-and-enddate"></a>I. startdate と enddate に列を指定する  
この例では、テーブルの 2 つの列に日付を格納し、両者の差を日単位で計算しています。
  
```sql
CREATE TABLE dbo.Duration 
    (startDate datetime2, endDate datetime2);
    
INSERT INTO dbo.Duration (startDate, endDate)  
    VALUES ('2007-05-06 12:10:09', '2007-05-07 12:10:09');  
    
SELECT TOP(1) DATEDIFF(day, startDate, endDate) AS Duration  
    FROM dbo.Duration;  
-- Returns: 1  
```  
  
### <a name="j-specifying-scalar-subqueries-and-scalar-functions-for-startdate-and-enddate"></a>J. startdate と enddate にスカラー サブクエリおよびスカラー関数を指定する  
この例では、*startdate* と *enddate* の引数として、サブクエリとスカラー関数を使用しています。
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEDIFF(day, (SELECT MIN(HireDate) FROM dbo.DimEmployee),  
    (SELECT MAX(HireDate) FROM dbo.DimEmployee))   
FROM dbo.DimEmployee;  
  
```  
  
### <a name="k-specifying-constants-for-startdate-and-enddate"></a>K. startdate と enddate に定数を指定する  
この例では、*startdate* と *enddate* の引数として文字定数を使用しています。
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEDIFF(day,
    '2007-05-07 09:53:01.0376635',
    '2007-05-08 09:53:01.0376635') FROM DimCustomer;  
```  
  
### <a name="l-specifying-ranking-functions-for-startdate"></a>L. startdate に順位付け関数を指定する  
この例では、*startdate* の引数として順位付け関数を使用しています。
  
```sql
-- Uses AdventureWorks  
  
SELECT FirstName, LastName,
    DATEDIFF(day, ROW_NUMBER() OVER (ORDER BY   
        DepartmentName), SYSDATETIME()) AS RowNumber  
FROM dbo.DimEmployee;  
```  
  
### <a name="m-specifying-an-aggregate-window-function-for-startdate"></a>M. startdate に集計関数を指定する  
この例では、*startdate* の引数として集計関数を使用しています。
  
```sql
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, DepartmentName,
    DATEDIFF(year, MAX(HireDate)  
        OVER (PARTITION BY DepartmentName), SYSDATETIME()) AS SomeValue  
FROM dbo.DimEmployee  
```  
  
## <a name="see-also"></a>参照
[DATEDIFF_BIG &#40;Transact-SQL&#41;](../../t-sql/functions/datediff-big-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


