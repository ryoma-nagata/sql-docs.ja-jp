---
title: sp_syscollector_delete_collection_item は (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syscollector_delete_collection_item
- sp_syscollector_delete_collection_item_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_delete_collecton_item
- data collector [SQL Server], stored procedures
ms.assetid: 9c2b0990-1d3d-4a59-94a0-3cca6fef4681
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 331a5201e4a179427cbe1ec558ff49958eb818aa
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258534"
---
# <a name="spsyscollectordeletecollectionitem-transact-sql"></a>sp_syscollector_delete_collection_item (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コレクション セットからコレクション項目を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syscollector_delete_collection_item [[ @collection_item_id = ] collection_item_id ]  
    , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>引数  
 [ @collection_item_id = ] *collection_item_id*  
 コレクション アイテムの一意な識別子を指定します。 *collection_item_id*は**int**既定値は NULL です。 *collection_item_id*場合、値が必要*名前*は NULL です。  
  
 [ @name =] '*名前*'  
 コレクション アイテムの名前を指定します。 *名前*は**sysname**で、既定値は NULL です。 *名前*場合、値が必要*collection_item_id*は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_syscollector_delete_collection_item は、msdb システム データベースのコンテキストで実行する必要があります。 コレクション アイテムは、システム コレクション セットから削除できません。  
  
 この操作が実行されている間、コレクション アイテムを含むコレクション セットは停止し、再開されます。  
  
## <a name="permissions"></a>権限  
 このプロシージャを実行するには、(EXECUTE 権限を持つ) dc_admin 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、という名前の項目のコレクションを削除`MyCollectionItem1`です。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_delete_collection_item @name = 'MyCollectionItem1';  
```  
  
## <a name="see-also"></a>参照  
 [データ コレクション](../../relational-databases/data-collection/data-collection.md)   
 [sp_syscollector_create_collection_item &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql.md)   
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [syscollector_collection_items &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)  
  
  
