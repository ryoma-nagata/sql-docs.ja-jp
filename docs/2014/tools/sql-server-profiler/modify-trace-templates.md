---
title: トレース テンプレートの変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- modifying trace templates
- SQL Server Profiler, templates
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 131c10dde4557fd7f462a1dd2324819c58bbf1d0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37200652"
---
# <a name="modify-trace-templates"></a>トレース テンプレートの変更
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を実行しているローカル コンピューター上のファイルに保存されたテンプレートは変更することができます。 また、それらのファイルから派生したテンプレートも変更できます。 既存のテンプレートを変更する場合は、 **[トレースのプロパティ]** ダイアログ ボックスの **[イベントの選択]** タブで、最初にプロパティを設定したときと同じ順序で、イベント クラスやデータ列などのテンプレートのプロパティを編集します。 イベント クラスとデータ列は追加または削除することができ、フィルターは変更することができます。 テンプレートを変更すると、ユーザー固有のテンプレートが作成されます。元のシステム テンプレートは変更されません。 詳細については、「 [トレースとトレース テンプレートの保存](save-traces-and-trace-templates.md)」を参照してください。  
  
 トレースを作成したときに使用した元のテンプレートを覚えていない (または保存していなかった) 場合や、後日同じトレースを実行する場合など、既存のトレース ファイルからテンプレートを派生させる必要が生じることがあります。 既存のトレースを使用する場合、プロパティを参照できますが、変更できません。 プロパティを変更するには、トレースを停止または一時停止する必要があります。 詳細については、「[トレース ファイルまたはトレース テーブルからのテンプレートの作成 &#40;SQL Server Profiler&#41;](sql-server-profiler.md)」および「[実行中のトレースからのテンプレートの作成 &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md)」を参照してください。  
  
 **トレース テンプレートを作成するには**  
  
 [トレース テンプレートの作成 &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md)  
  
 **トレース テンプレートからトレースを実行するには**  
  
 [トレースの作成 &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md)  
  
 **トレース テンプレートを変更するには**  
  
 [SQL Server Profiler を使用します。](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
 [Transact-SQL の使用](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
  
 **トレース テンプレートまたはトレース ファイルからイベントを追加または削除するには**  
  
 [SQL Server Profiler を使用します。](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Transact-SQL の使用](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
## <a name="see-also"></a>参照  
 [トレースを開始する](start-a-trace.md)  
  
  
