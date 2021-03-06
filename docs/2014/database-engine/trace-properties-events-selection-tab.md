---
title: トレースのプロパティ (イベントの選択 タブ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.eventsselection.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: e1892f24-7272-4d5d-8926-6150cc82b2c3
caps.latest.revision: 24
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 033cde8c84edc6ceb7b0fb9686e31b6ce98ef1c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283828"
---
# <a name="trace-properties-events-selection-tab"></a>[トレースのプロパティ] ([イベントの選択] タブ)
  **[トレースのプロパティ]** ダイアログ ボックスの **[イベントの選択]** タブを使用すると、トレースの対象となるイベントとデータ列を表示および指定できます。  
  
## <a name="options"></a>および  
 **[イベント]** 列  
 イベント列のチェック ボックスをオンまたはオフにして、トレースするイベントを指定します。 **[イベント]** 列は、イベント カテゴリ別に分類されています。 テンプレートで指定されているイベント クラスが自動的に選択されます。 詳しくは、「 [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)」をご覧ください。  
  
 データ列  
 必要なイベント列とデータ列に対応するチェック ボックスをオンにして、トレースするデータ列を指定します。 トレースの対象になる各イベントに対応するイベント列は、既定ですべてオンになっています。  
  
 フィルターを指定するには、データ列のヘッダーをクリックし、フィルター基準を入力します。 フィルター選択されるデータ列については、 **[フィルターの編集]** ダイアログ ボックスの列ラベルの左側にフィルターのアイコンが表示されます。 詳細については、「 [SQL Server Profiler - [フィルターの編集]](../../2014/database-engine/sql-server-profiler-edit-filter.md)」を参照してください。  
  
 **[すべてのイベントを表示する]**  
 表示できるイベントをすべて表示します。 既定では、 **[イベントの選択]** グリッドで選択されている行だけが表示されます。 このチェック ボックスをオフにすると、 **[イベントの選択]** グリッドで選択されていないイベントがすべて非表示になります。  
  
 **[すべての列を表示]**  
 表示できるデータ列をすべて表示します。 既定では、選択されているデータ列だけが表示されます。 このチェック ボックスをオフにすると、 **[イベントの選択]** グリッドで選択されていないデータ列がすべて非表示になります。  
  
 **列フィルター**  
 **[フィルターの編集]** ダイアログ ボックスを起動します。 このダイアログ ボックスを使用して、データ列のフィルターを編集できます。  
  
 **[列の構成]**  
 トレースとグループ化の結果で、1 つ以上の列を使用して列の順序を変更します。  
  
## <a name="see-also"></a>参照  
 [トレース ファイルのイベントとデータ列を指定&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [トレースに表示される列を整理&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)   
 [トレース内のイベントをフィルター処理&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)   
 [フィルター情報の表示 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)   
 [フィルターを変更する&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)   
 [SQL Server プロファイラーのテンプレートと権限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
