---
title: MSSQLSERVER_2530 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dc84999be0485c9b6aa03875d0e96978b0531f0b
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver2530"></a>MSSQLSERVER_2530
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2530|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_INDEX_IS_OFFLINE|  
|メッセージ テキスト|テーブル "%.\*ls" のインデックス "%.*ls" は無効です。|  
  
## <a name="explanation"></a>説明  
指定されたインデックスが無効になっているため、DBCC ステートメントを実行できません。 インデックスを無効にすると、そのインデックスは再構築、または削除されて再作成されるまで無効になります。  
  
## <a name="user-action"></a>ユーザーの操作  
  
1.  次のいずれかの方法を使用して、無効になっているインデックスを有効にします。  
  
    -   REBUILD 句を指定した ALTER INDEX ステートメント  
  
    -   DROP_EXISTING 句を指定した CREATE INDEX  
  
    -   DBCC DBREINDEX  
  
2.  DBCC ステートメントを再実行します。  
  
## <a name="see-also"></a>参照  
[インデックスと制約の有効化](~/relational-databases/indexes/enable-indexes-and-constraints.md)  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/create-index-transact-sql.md)  
[DBCC DBREINDEX &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md)  
  
