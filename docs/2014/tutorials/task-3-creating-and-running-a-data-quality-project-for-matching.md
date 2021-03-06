---
title: 'タスク 3: を作成して、一致するデータ品質プロジェクトを実行している |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cf5fc254aff0398b40605fdc6c568d9dc01b3a60
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216272"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a>タスク 3: 照合するデータ品質プロジェクトを作成および実行する
  ここでは、照合アクティビティ用のデータ品質プロジェクトを作成し、クレンジングされた仕入先データで照合プロセスを実行して、データ内の重複部分を削除します。  
  
1.  メイン ページで、 **DQS クライアント**、 をクリックして**新しいデータ品質プロジェクト**します。  
  
2.  型**Remove Supplier Duplicates**から、**プロジェクトの名前**します。  
  
3.  選択**Suppliers** Kb の一覧から、**ナレッジ ベースを使用**フィールド。 前のレッスンでは、このナレッジ ベースの照合ポリシーを作成しました。  
  
4.  選択**照合**から、**活動の一覧を**右下のペインから。  
  
     ![新しいデータ品質プロジェクトの選択に一致する](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "選択に一致する、新しいデータ品質プロジェクト")  
  
5.  **[次へ]** をクリックします。  
  
6.  **[マップ]** ページの **[データ ソース]** で **[Excel ファイル]** を選択します。  
  
7.  をクリックして**参照**選択と**Cleansed Supplier List.xls**、これは、クレンジング アクティビティの出力ファイル。  
  
8.  マップ**SupplierID**を基になる列、 **Supplier ID**ドメイン、 **Supplier Name**列**Supplier Name**ドメイン、および**ContactEmailAddress**列**Contact Email**ドメイン。  
  
9. をクリックして**次**に切り替える、**照合**ページ。  
  
10. クリックして**開始**一致するプロセスを開始します。 照合ポリシーを定義する際に同じ入力ファイルを使用したため、前のタスクの結果と同様の結果が表示されます。  
  
11. リスト ボックスのすべての一致レコードと照合スコアを確認します。 この結果は、前のタスクで表示された結果と同じになります。 この照合アクティビティの結果を解析するには、前のタスクの手順を参照してください。  
  
12. をクリックして**次**に切り替える、**エクスポート**ページ。  
  
## <a name="next-step"></a>次の手順  
 [タスク 4: 照合アクティビティから Excel ファイルに結果をエクスポートする](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)  
  
  
