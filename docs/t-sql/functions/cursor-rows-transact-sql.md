---
title: '@@CURSOR_ROWS (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@CURSOR_ROWS'
- '@@CURSOR_ROWS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@CURSOR_ROWS function'
- cursors [SQL Server], last-opened
- last-opened cursor
- asynchronous cursors [SQL Server]
ms.assetid: 31bd7a97-7f28-42a8-ba24-24d16d22973d
caps.latest.revision: 36
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9e7ea135967049f5ab6c09d35fdb52e07216ea57
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37785323"
---
# <a name="x40x40cursorrows-transact-sql"></a>&#x40;&#x40;CURSOR_ROWS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

接続で開いた最後のカーソルで現在登録されている行数を返します。 パフォーマンスを向上させるために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、大きなキーセットと静的カーソルを非同期に作成できます。 あるカーソルに登録されている行数が @@CURSOR_ROWS の呼び出し時に取得されることは、`@@CURSOR_ROWS` を呼び出すことで決定できます。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```
@@CURSOR_ROWS  
```  
  
## <a name="return-types"></a>戻り値の型
**整数 (integer)**
  
## <a name="return-value"></a>戻り値  
  
|戻り値|[説明]|  
|---|---|
|-*m*|カーソルは非同期で作成されます。 返される値 (-*m*) は、現在キーセットにある行数です。|  
|-1|カーソルが動的な場合に返されます。 動的カーソルはすべての変更を反映するので、そのカーソルに登録されている行数は常に変化します。 登録されているすべての行がカーソルによって取得されるとは限りません。|  
|0|オープンされているカーソルがない場合、最後にオープンされたカーソルに行が登録されていない場合、または最後にオープンされたカーソルがクローズまたは割り当てを解除されている場合に返されます。|  
|*n*|カーソルに行がすべて完全に登録されている場合に返されます。 返される値 (*n*) には、カーソル内の行の合計数。|  
  
## <a name="remarks"></a>Remarks  
`@@CURSOR_ROWS` は、最後のカーソルが非同期で開いた場合、負の数を返します。 sp_configure カーソルしきい値が 0 を超える場合か、カーソル結果セットの行数がカーソルしきい値を超える場合、キーセットドライバー カーソルまたは静的カーソルが非同期で開きます。
  
## <a name="examples"></a>使用例  
この例では、最初にカーソルを宣言し、`SELECT` を使用して `@@CURSOR_ROWS` の値を表示します。 カーソルが開く前は値 `0` が設定され、その後、値 `-1` が設定されることで、カーソル キーセットが非同期で作成されることを示します。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT @@CURSOR_ROWS;  
DECLARE Name_Cursor CURSOR FOR  
SELECT LastName ,@@CURSOR_ROWS FROM Person.Person;  
OPEN Name_Cursor;  
FETCH NEXT FROM Name_Cursor;  
SELECT @@CURSOR_ROWS;  
CLOSE Name_Cursor;  
DEALLOCATE Name_Cursor;  
GO             
```  
  
以下に結果セットを示します。
  
```
-----------
0  
```

```
LastName
---------------
Sanchez
```

```
-----------
-1
```  
  
## <a name="see-also"></a>参照
[カーソル関数 &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-functions-transact-sql.md)  
[開く (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/open-transact-sql.md)
  
  
