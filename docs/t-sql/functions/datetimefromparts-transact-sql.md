---
title: DATETIMEFROMPARTS (Transact-SQL) | Microsoft Docs
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
- DATETIMEFROMPARTS_TSQL
- DATETIMEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIMEFROMPARTS function
ms.assetid: 6008148b-bf75-4c98-9392-68a89fa0711c
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 754e91dcebdc7d040802de11ba0285f6cf472a4a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38023226"
---
# <a name="datetimefromparts-transact-sql"></a>DATETIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

この関数は、指定された日付引数と時刻引数に対して **datetime** 値を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DATETIMEFROMPARTS ( year, month, day, hour, minute, seconds, milliseconds )  
```  
  
## <a name="arguments"></a>引数  
*year*  
年を指定する整数式。
  
*month*  
月を指定する整数式。
  
*day*  
日を指定する整数式。
  
*hour*  
時を指定する整数式。
  
*minute*  
分を指定する整数式。
  
*seconds*  
秒を指定する整数式。
  
*milliseconds*  
ミリ秒を指定する整数式。
  
## <a name="return-types"></a>戻り値の型
**datetime**
  
## <a name="remarks"></a>Remarks  
`DATETIMEFROMPARTS` は、完全に初期化された **datetime** 値を返します。 `DATETIMEFROMPARTS` は、必須引数に 1 つでも無効な値が含まれている場合、エラーを生成します。 `DATETIMEFROMPARTS` は、必須引数に 1 つでも NULL 値が含まれている場合、NULL を返します。
  
この関数は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] サーバー以降のリモート処理に対応しています。 バージョンが [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] より前の場合、サーバーのリモート処理には対応していません。
  
## <a name="examples"></a>使用例  
  
```sql
SELECT DATETIMEFROMPARTS ( 2010, 12, 31, 23, 59, 59, 0 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
---------------------------  
2010-12-31 23:59:59.000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照
[datetime (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/datetime-transact-sql.md)
  
  

