---
title: 計算列での XML の使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- computed columns, XML
- XML [SQL Server], computed columns
ms.assetid: 1313b889-69b4-4018-9868-0496dd83bf44
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f67ecf15309e76b19358964a3ecb286f214cca71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37206682"
---
# <a name="use-xml-in-computed-columns"></a>計算列での XML の使用
  XML インスタンスは、計算列のソースとして、または計算列の一種として使用できます。 このトピックでは、計算列で XML を使用する方法を示す例を紹介します。  
  
## <a name="creating-computed-columns-from-xml-columns"></a>XML 列から計算列を作成する  
 次の `CREATE TABLE` ステートメントでは、 `xml` から`col2`型の列 ( `col1`) を計算しています。  
  
```  
CREATE TABLE T(col1 varchar(max), col2 AS CAST(col1 AS xml) )    
```  
  
 次の `xml` ステートメントで示すように、 `CREATE TABLE` データ型は計算列を作成するときのソースとしても使用できます。  
  
```  
CREATE TABLE T (col1 xml, col2 as cast(col1 as varchar(1000) ))   
```  
  
 次の例に示すように、 `xml` 型の列から値を抽出して計算列を作成できます。 計算列を作成するときは `xml` データ型のメソッドを直接使用できません。そのため、この例では XML インスタンスの値を返す関数 (`my_udf`) をまず定義しています。 この関数には、 `value()` 型の `xml` メソッドがラップされています。 `CREATE TABLE` ステートメントで、この関数名が計算列の代わりに指定されています。  
  
```  
CREATE FUNCTION my_udf(@var xml) returns int  
AS BEGIN   
RETURN @var.value('(/ProductDescription/@ProductModelID)[1]' , 'int')  
END  
GO  
-- Use the function in CREATE TABLE.  
CREATE TABLE T (col1 xml, col2 as dbo.my_udf(col1) )  
GO  
-- Try adding a row.   
INSERT INTO T values('<ProductDescription ProductModelID="1" />')  
GO  
-- Verify results.  
SELECT col2, col1  
FROM T  
  
```  
  
 上記の例と同様に、次の例では計算列用に `xml` 型のインスタンスを返す関数を定義しています。 関数内では、 `query()` データ型の `xml` メソッドにより `xml` 型のパラメーターの値を取得しています。  
  
```  
CREATE FUNCTION my_udf(@var xml)   
  RETURNS xml AS   
BEGIN   
   RETURN @var.query('ProductDescription/Features')  
END  
```  
  
 次の `CREATE TABLE` ステートメントの `Col2` は、関数が返した XML データ (`<Features>` 要素) を使用する計算列です。  
  
```  
CREATE TABLE T (Col1 xml, Col2 as dbo.my_udf(Col1) )  
-- Insert a row in table T.  
INSERT INTO T VALUES('  
<ProductDescription ProductModelID="1" >  
  <Features>  
    <Feature1>description</Feature1>  
    <Feature2>description</Feature2>  
  </Features>  
</ProductDescription>')  
-- Verify the results.  
SELECT *  
FROM T  
```  
  
### <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[計算列を使用した使用頻度の高い XML 値の昇格](promote-frequently-used-xml-values-with-computed-columns.md)|計算列やプロパティ テーブルでプロパティの昇格を使用する方法について説明します。|  
  
  
