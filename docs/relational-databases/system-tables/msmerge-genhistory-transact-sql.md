---
title: MSmerge_genhistory (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_genhistory_TSQL
- MSmerge_genhistory
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_genhistory system table
ms.assetid: 475d08ae-eb8b-49de-afd6-33c96ab8004d
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cabcaca806b2a09617e417542b8b6440280a5016
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101690"
---
# <a name="msmergegenhistory-transact-sql"></a>MSmerge_genhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_genhistory**テーブルには、サブスクライバーが保有期間) 以内について認識している各ジェネレーションの 1 つの行が含まれます。 これは、変換中に共通する generation 値を送信することを防ぎ、バックアップから復元するサブスクライバーを再同期するために使用されます。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**guidsrc**|**uniqueidentifier**|サブスクライバーの generation 値によって識別される変更のグローバル識別子です。|  
|**pubid**|**uniqueidentifier**|パブリケーション識別子です。|  
|**生成**|**bigint**|generation 値です。|  
|**art_nick**|**int**|アーティクルのニックネームです。|  
|**ニックネーム**|**varbinary(1001)**|この generation 値を持っていることが既に認識されている他のサブスクライバーのニックネームの一覧です。 その変更を既に認識しているサブスクライバーに、generation 値を送信することを防ぐために使用します。 ニックネーム一覧内のニックネームは、検索をより効率化するために並べ替えて管理されます。 このフィールドの範囲を超えるニックネームがある場合、この最適化による恩恵を受けることはありません。|  
|**coldate**|**datetime**|現在の generation 値がテーブルに追加された日付です。|  
|**genstatus**|**tinyint**|generation の状態です。次のいずれかの値をとります。<br /><br /> **0**開くを = です。<br /><br /> **1** = 終了します。<br /><br /> **2** = クローズし、別のサブスクライバーで発生します。|  
|**これは changecount**|**int**|指定の generation に反映された変更の数です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
