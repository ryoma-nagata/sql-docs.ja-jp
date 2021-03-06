---
title: XPath ノード テストの名前が付いた列 | Microsoft Docs
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
- names [SQL Server], columns with
- XPath node test
ms.assetid: b48adccd-3b6b-486a-b326-20f57170186f
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fc0491b334b8a4010800b37e952c26bfcd465229
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37288358"
---
# <a name="columns-with-the-name-of-an-xpath-node-test"></a>XPath ノード テストの名前が付いた列
  XPath ノード テストのいずれかが列名である場合、内容は次の表に示すようにマップされます。 列名がいずれかの XPath ノード テストであれば、対応するノードに内容がマップされます。 列の SQL 型が場合`xml`エラーが返されます。  
  
|列名|動作|  
|-----------------|--------------|  
|text()|text() という名前の列では、列内の文字列値がテキスト ノードとして追加されます。|  
|comment()|comment() という名前の列では、列内の文字列値が XML のコメントとして追加されます。|  
|node()|node() という名前の列では、列名がワイルドカード文字 (*) の場合と同じ結果が返されます。|  
|processing-instruction(name)|処理命令を名前とする列では、列内の文字列値が、処理命令ターゲット名に対応する PI 値として追加されます。|  
  
 次のクエリでは、列名としてノード テストを使用しています。 結果の XML では、テキスト ノードとコメントが追加されます。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
        'Example of using node tests such as text(), comment(), processing-instruction()'                as "comment()",  
        'Some PI'                   as "processing-instruction(PI)",  
        'Employee name and address data' as "text()",  
        'middle name is optional'        as "EmpName/text()",  
        FirstName                        as "EmpName/First",   
        MiddleName                       as "EmpName/Middle",   
        LastName                         as "EmpName/Last",  
        AddressLine1                     as "Address/AddrLine1",  
        AddressLine2                     as "Address/AddrLIne2",  
        City                             as "Address/City"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P   
    ON P.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS BAE  
    ON BAE.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BAE.AddressID = A.AddressID  
WHERE  E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 結果を次に示します。  
  
 `<row EmpID="1">`  
  
 `<!--Example of using node tests such as text(), comment(), processing-instruction() -->`  
  
 `<?PI Some PI?>`  
  
 `Employee name and address data`  
  
 `<EmpName>middle name is optional`  
  
 `<First>Ken</First>`  
  
 `<Last>Sánchez</Last>`  
  
 `</EmpName>`  
  
 `<Address>`  
  
 `<AddrLine1>4350 Minute Dr.</AddrLine1>`  
  
 `<City>Minneapolis</City>`  
  
 `</Address>`  
  
 `</row>`  
  
## <a name="see-also"></a>参照  
 [FOR XML での PATH モードの使用](use-path-mode-with-for-xml.md)  
  
  
