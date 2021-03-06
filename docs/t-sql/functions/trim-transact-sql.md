---
title: TRIM (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- TRIM
- TRIM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- TRIM function
ms.assetid: a00245aa-32c7-4ad4-a0d1-64f3d6841153
caps.latest.revision: 4
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: a880c9de5b763386504a4163ffe44aaf62c136b4
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37981381"
---
# <a name="trim-transact-sql"></a>TRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

文字列の先頭または末尾にあるスペース文字 `char(32)` または他の指定した文字を削除します。  
 
## <a name="syntax"></a>構文   
```
TRIM ( [ characters FROM ] string ) 
```
[//]: # "[ BOTH | LEADING | TRAILING ] はまだ使用できません。"

## <a name="arguments"></a>引数   

characters   
削除する必要がある文字を含む LOB 以外の任意の文字型 (`nvarchar`、`varchar`、`nchar`、または`char`) のリテラル、変数、または関数呼び出しです。 `nvarchar(max)` 型と `varchar(max)` 型は使用できません。

string   
文字を削除する必要がある任意の文字型 (`nvarchar`、`varchar`、`nchar`、または`char`) の式です。

## <a name="return-types"></a>戻り値の型   
空白文字 `char(32)` または他の指定した文字が両側から削除される、文字列引数の型を持つ文字式を返します。 入力文字列が `NULL` の場合は `NULL` を返します。

## <a name="remarks"></a>Remarks   
`TRIM` 関数は、既定で、両側からスペース文字 `char(32)` を削除します。 これは、`LTRIM(RTRIM(@string))` と同じです。 文字が指定された `TRIM ` 関数の動作は、`REPLACE` 関数の動作 (先頭または末尾の文字が空白の文字列で置き換えられる) と同じです。


## <a name="examples"></a>使用例
### <a name="a--removes-the-space-character-from-both-sides-of-string"></a>A.  文字列の先頭と末尾からスペース文字を削除します。   
次の例では、単語 `test` の前後からスペースを削除します。   
```sql
SELECT TRIM( '     test    ') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

`test`


### <a name="b--removes-specified-characters-from-both-sides-of-string"></a>B.  指定した文字を文字列の両側から削除します。   
次の例では、末尾のピリオドと末尾のスペースを削除します。
```sql
SELECT TRIM( '.,! ' FROM  '#     test    .') AS Result;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   
`#     test`


## <a name="see-also"></a>参照
 [LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)  
 [LTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/ltrim-transact-sql.md)  
 [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40;Transact-SQL&#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)  
 [文字列関数 &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)   
