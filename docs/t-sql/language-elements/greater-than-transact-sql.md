---
title: '&gt; (より大きい) (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Greater
- Than
- '> (Greater Than)'
- '>_TSQL'
- Greater Than
- '>'
dev_langs:
- TSQL
helpviewer_keywords:
- greater than operator (>)
- '> (greater than operator)'
ms.assetid: 50a7b098-a3fb-4df6-ae42-1272d6346338
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 156fd81188d646d761df17704f56a3237ef70de3
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36259204"
---
# <a name="gt-greater-than-transact-sql"></a>&gt; (より大きい) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で 2 つの式を比較します (比較演算子)。 NULL でない式を比較したときに、左側のオペランドの値が右側のオペランドの値よりも大きい場合、結果は TRUE です。それ以外の場合、結果は FALSE です。 どちらか一方、または両方のオペランドが NULL の場合は、トピック「[SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 任意の有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)を指定します。 両方の式とも、暗黙的に変換可能なデータ型でなければなりません。 変換は、[データ型の優先順位](../../t-sql/data-types/data-type-precedence-transact-sql.md)のルールに依存します。  
  
## <a name="result-types"></a>戻り値の型  
 **ブール値**  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using--in-a-simple-query"></a>A. 簡単なクエリで > を使用する  
 次の例では、`HumanResources.Department` テーブル内で、`DepartmentID` の値が値 13 を超えるすべての行を返します。  
  
```  
--Uses AdventureWorks  
  
SELECT DepartmentID, Name  
FROM HumanResources.Department  
WHERE DepartmentID > 13  
ORDER BY DepartmentID;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DepartmentID Name  
------------ --------------------------------------------------  
14           Facilities and Maintenance  
15           Shipping and Receiving  
16           Executive  
  
(3 row(s) affected)  
  
```  
  
### <a name="b-using--to-compare-two-variables"></a>B. > を使用して 2 つの変数を比較する  
  
```  
DECLARE @a int = 45, @b int = 40;  
SELECT IIF ( @a > @b, 'TRUE', 'FALSE' ) AS Result;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------  
TRUE  
  
(1 row(s) affected)  
  
```  
  
## <a name="see-also"></a>参照  
 [IIF &#40;Transact-SQL&#41;](../../t-sql/functions/logical-functions-iif-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [演算子 (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
