---
title: core.sp_add_collector_type (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_collector_type
- sp_add_collector_type_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- core.sp_add_collector_type stored procedure
- management data warehouse, data collector stored procedures
- sp_add_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 1d981037-2147-464e-a456-7d8e479bce89
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 486a51f5f521c0a3af647bc4d7242f3696727789
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33238369"
---
# <a name="corespaddcollectortype-transact-sql"></a>core.sp_add_collector_type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  管理データ ウェアハウス データベースの core.supported_collector_types ビューに新しいエントリを追加します。 このプロシージャは、管理データ ウェアハウス データベースのコンテキストで実行してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
core.sp_add_collector_type [ @collector_type_uid = ] 'collector_type_uid'  
```  
  
## <a name="arguments"></a>引数  
 [ @collector_type_uid =] '*collector_type_uid*'  
 コレクター型の GUID を指定します。 *collector_type_uid*は**uniqueidentifier**既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="permissions"></a>権限  
 メンバーシップが必要、 **mdw_admin** (EXECUTE 権限) を持つ固定データベース ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、core.supported_collector_types ビューにジェネリック T-SQL Query コレクター型を追加します。 既定では、ジェネリック T-SQL Query コレクター型は既に存在します。 したがって、既定のインストールでこのコードを実行すると、コレクター型が既に存在していることを示すメッセージが表示されます。  
  
 sp_remove_collector_type ストアド プロシージャを使用してジェネリック T-SQL Query コレクター型を削除してから、管理データ ウェアハウスにデータをアップロードできる登録済みのコレクター型としてジェネリック T-SQL Query コレクター型を再度追加すると、このコードは正常に動作します。  
  
```  
USE <management_data_warehouse>;  
GO  
DECLARE @RC int;  
DECLARE @collector_type_uid uniqueidentifier;  
SELECT @collector_type_uid = (SELECT collector_type_uid FROM msdb.dbo.syscollector_collector_types WHERE name = N'Generic T-SQL Query Collector Type');  
EXECUTE @RC = core.sp_add_collector_type @collector_type_uid;  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [管理データ ウェアハウス](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
