---
title: 複数の列でテーブルを結合する (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- multiple column joins
- joins [SQL Server], multiple columns
ms.assetid: 56a158bc-a42a-4b78-baad-4721d2d22cd3
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e0b8807ad4a8b2cbcadc0ecaa30db2db105ed482
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218692"
---
# <a name="join-tables-on-multiple-columns-visual-database-tools"></a>複数の列でテーブルを結合する (Visual Database Tools)
  テーブルの結合は、複数の列を使用して行うこともできます。 つまり、2 つのテーブルの行が複数の条件を満たす場合だけこれらのテーブルの行を対応させるクエリを作成できます。 データベースのリレーションシップによって、複数存在する外部キー列を他方のテーブルの複数列にわたる主キーと一致させる場合、このリレーションシップを使用して複数列結合を作成できます。 詳しくは、「[テーブルの自動結合 (Visual Database Tools)](visual-database-tools.md)」をご覧ください。  
  
 複数列の外部キー リレーションシップがデータベースにない場合でも、この結合を手動で作成できます。  
  
### <a name="to-manually-create-a-multicolumn-join"></a>複数列結合を手動で作成するには  
  
1.  結合するテーブルを [ダイアグラム ペイン](diagram-pane-visual-database-tools.md) に追加します。  
  
2.  最初のテーブル ウィンドウの最初の結合列の名前をドラッグし、2 番目のテーブル ウィンドウの関連する列にドロップします。 text 型、ntext 型、または image 型の列を結合することはできません。  
  
    > [!NOTE]  
    >  一般に、結合列のデータ型は、同じ型か互換性のある型である必要があります。 たとえば、最初のテーブルの結合列が日付型の場合は、2 番目のテーブルの結合列も日付型としてください。 一方、最初の結合列が整数型の場合、関連付ける結合列も整数型である必要がありますが、サイズは異なってもかまいません。 ただし、暗黙的なデータ型の変換により、見かけ上は互換性のない列を結合できる場合もあります。  
    >   
    >  [クエリおよびビュー デザイナー](query-and-view-designer-tools-visual-database-tools.md) では、結合の作成に使用した列のデータ型がチェックされることはありません。ただしデータ型に互換性がない場合、クエリの実行時にデータベースによってエラーが表示されます。  
  
3.  最初のテーブル ウィンドウの 2 番目の結合列の名前をドラッグし、2 番目のテーブル ウィンドウの関連する列にドロップします。  
  
4.  2 つのテーブルに結合列の対を追加するたびに、手順 3. を繰り返します。  
  
5.  クエリを実行します。  
  
## <a name="see-also"></a>参照  
 [結合を使用したクエリ (Visual Database Tools)](query-with-joins-visual-database-tools.md)  
  
  
