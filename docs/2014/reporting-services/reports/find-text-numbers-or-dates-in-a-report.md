---
title: (追加する Reporting Services SharePoint 統合モードで) レポート内のテキスト、数値、または日付の検索 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- searching reports
ms.assetid: 309dffe5-00f5-404f-bb63-9e6046253ae0
caps.latest.revision: 11
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: e1f744568bcce20528df364ca2faf638eb677784
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278281"
---
# <a name="find-text-numbers-or-dates-in-a-report-reporting-services-in-sharepoint-integrated-mode"></a>レポート内のテキスト、数値、または日付を検索する (Reporting Services の SharePoint 統合モード)
  レポートのコンテンツは、単語や語句を入力して検索できます (検索用語の最大文字数は 256 文字です)。 検索は、レポート内にある一致する値を検出し、その値の位置にカーソルを移動するナビゲーション技法です。  
  
 検索は大文字と小文字を区別せず、現在選択されているページまたはセクションから開始されます。 レポートで表示されているコンテンツのみが、検索の対象になります。 展開したり折りたたんだりできる領域がレポートに含まれている場合、その領域に含まれている値は検索対象外となります。 検索できるのは、現在のレポート内のテキスト、数値、または日付だけです。 自動生成されたクリックスルー レポートを使用してデータを検索している場合、以前に生成されたレポートに含まれる用語を検索することはできません。また、データ パスに含まれる用語を検索することもできません。  
  
 検索する値を入力する際には、レポートで実際に使用されていることが予想される値を入力します。 「今月の平均利益は」のような質問は、この文字列がレポートに含まれていると予想できる場合を除いて不適切です。  
  
 一度に検索できる用語または値は 1 つだけです。 検索演算子 (AND や OR など)、記号、およびワイルドカードは使用できません。 複数のセクションにわたったデータは検索できません (たとえば、特定の製品のある月の純売上高を検索することはできません)。 このような分析には、レポート ビルダーを使用してクリックスルー レポートを作成するか、作成したクリックスルー レポートを使用します。  
  
 レポート データへのアクセスを制限するデータベースとモデルのセキュリティ設定は、検索操作にも適用されます。 データ ソースにモデルを使用しているクリックスルー レポートで値を検索する場合に、そのモデルの一部にアクセス権限がないと、その部分に含まれるデータは検索対象外になります。  
  
### <a name="to-find-data-in-a-report"></a>レポートでデータを検索するには  
  
1.  レポートを開きます。  
  
2.  レポート ツール バーで、検索するテキスト、数値、または日付を入力します。  
  
     レポート ツール バーが表示されない場合は、意図的に非表示に設定されているため、レポート ツール バーの機能を使用することはできません。 このツール バーが表示されるかどうかは、レポート ビューアー Web パーツのプロパティで指定されます。  
  
3.  **[検索]** をクリックします。  
  
4.  同じ値で引き続き検索を続ける場合は、 **[次へ]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [レポート ビューアー Web パーツを Web ページに追加&#40;Reporting Services の SharePoint 統合モード&#41;](../report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)  
  
  
