---
title: 'レッスン 5: リレーションシップの作成 |Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 36993a468a6997ff8de40da542deac00b25b18b4
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38034770"
---
# <a name="lesson-4-create-relationships"></a>レッスン 4: リレーションシップを作成します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、データのインポート時に自動的に作成されたリレーションシップを確認し、異なるテーブル間に新しいリレーションシップを追加します。 リレーションシップとは、2 つのテーブル間を接続し、それらのテーブル内のデータをどのように関連付けるかを決定するものです。 たとえば、DimProduct テーブルと DimProductSubcategory テーブルには、各製品が特定のサブカテゴリに属しているということに基づくリレーションシップがあります。 詳細についてを参照してください。[リレーションシップ](../analysis-services/tabular-models/relationships-ssas-tabular.md)します。
  
このレッスンの推定所要時間: **10 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 3: 日付テーブルとしてマーク](../analysis-services/lesson-3-mark-as-date-table.md)します。 
  
## <a name="review-existing-relationships-and-add-new-relationships"></a>既存のリレーションシップの確認と新しいリレーションシップの追加  
データをインポートするには、テーブルのインポート ウィザードを使用して、AdventureWorksDW データベースから 7 つのテーブルがあります。 一般に、リレーショナル ソースからデータをインポートするときに既存のリレーションシップがデータと共に自動的にインポートします。 ただし、モデルの作成を進める前に、それらのテーブル間リレーションシップが適切に作成されたかどうかを確認する必要があります。 またこのチュートリアルでは、3 つの新しいリレーションシップの追加も行います。  
  
#### <a name="to-review-existing-relationships"></a>既存のリレーションシップを確認するには  
  
1.  をクリックして、**モデル**メニュー >**モデル ビュー** > **ダイアグラム ビュー**します。  

    モデル デザイナーがダイアグラム ビューで表示されます。このグラフィカルな形式では、インポートしたすべてのテーブルが、それらを結ぶ線と共に表示されます。 テーブル間の線は、データのインポート時に自動的に作成されたリレーションシップを表します。
    
    ![として-テーブル-lesson4-図](../analysis-services/media/as-tabular-lesson4-diagram.png)
  
    モデル デザイナーの右下隅にあるミニマップ コントロールを使用すると、できるだけ多くのテーブルが表示されるようにビューを調整できます。 テーブルをクリックして別の場所にドラッグすれば、テーブルどうし近づけたり、特定の順序に並べたりすることもできます。 テーブルを移動しても、テーブル間の既存のリレーションシップには影響しません。 特定のテーブル内のすべての列を表示するには、テーブルの端をクリックしてドラッグし、大きさを調整します。  
  
2.  間の実線をクリックして、 **DimCustomer**テーブルおよび**DimGeography**テーブル。 これら 2 つのテーブル間の実線は、そのリレーションシップがアクティブであることを示します。つまり、そのリレーションシップは DAX 数式の計算時に既定で使用されます。  
  
    通知、 **GeographyKey**内の列、 **DimCustomer**テーブルおよび**GeographyKey**内の列、 **DimGeography**テーブル両方のようになりましたボックス内に表示されます。 これは、これらがリレーションシップに使用される列であるということを示しています。 リレーションシップのプロパティが、**[プロパティ]** ウィンドウに表示されます。  
  
    > [!TIP]  
    > だけでなく、モデル デザイナーを使用して、ダイアグラム ビューで、テーブル形式ですべてのテーブル間のリレーションシップを表示するのにリレーションシップの管理 ダイアログ ボックスを使用することもできます。 右クリック**リレーションシップ**クリックして、表形式モデル エクスプ ローラーで**リレーションシップの管理**します。 リレーションシップの管理 ダイアログ ボックスでは、データのインポート時に自動的に作成されたリレーションシップを示します。  
  
3.  ダイアグラム ビュー、またはリレーションシップの管理 ダイアログ ボックスで、モデル デザイナーを使用して、AdventureWorksDW データベースからインポートされた各テーブルの際に、次のリレーションシップが作成されたことを確認します。  
  
    |Active|テーブル|関連する参照テーブル|  
    |----------|---------|------------------------|  
    |はい|**DimCustomer [GeographyKey]**|**DimGeography [GeographyKey]**|  
    |はい|**DimProduct [ProductSubcategoryKey]**|**DimProductSubcategory [ProductSubcategoryKey]**|  
    |はい|**DimProductSubcategory [ProductCategoryKey]**|**DimProductCategory [ProductCategoryKey]**|  
    |はい|**FactInternetSales [CustomerKey]**|**DimCustomer [CustomerKey]**|  
    |はい|**FactInternetSales [ProductKey]**|**DimProduct [ProductKey]**|  
  
    上記のテーブル内のリレーションシップのいずれかが存在しない場合は、次のテーブルがモデルに含まれることを確認します。 DimCustomer、DimDate、DimGeography、DimProduct、DimProductCategory、DimProductSubcategory、FactInternetSales とします。 同じデータ ソース接続からのテーブルが複数回インポートされた場合、それらのテーブル間のリレーションシップは作成されず、手動で作成する必要があります。  

### <a name="take-a-closer-look"></a>詳しく見てください。
ダイアグラム ビューでは、矢印、アスタリスク、およびテーブル間のリレーションシップを表示する行の数がわかります。

![として表形式 lesson4-行に](../analysis-services/media/as-tabular-lesson4-line.png)

矢印は、アスタリスクはこのテーブルがリレーションシップのカーディナリティの"多"側であり、1 は、このテーブルは、リレーションシップの一方の側を示しています。 フィルターの方向を示しています。 リレーションシップを編集する必要がある場合たとえば、リレーションシップのフィルターの方向やカーディナリティの変更、リレーションシップの編集 ダイアログを開きますダイアグラム ビューでのリレーションシップの線をダブルクリックします。

![として-テーブル-lesson4-編集](../analysis-services/media/as-tabular-lesson4-edit.png)

ほとんどの場合、リレーションシップを編集する必要はありません。 これらの機能は高度なデータ モデリングのためのものし、このチュートリアルの範囲外です。 詳細についてを参照してください。[双方向で SQL Server 2016 Analysis Services 表形式モデルのクロス フィルター](../analysis-services/tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md)します。

場合によっては、特定のビジネス ロジックをサポートするために、モデル内のテーブル間に追加のリレーションシップを作成する必要があります。 このチュートリアルでは、FactInternetSales テーブルと DimDate テーブルの間の 3 つの追加のリレーションシップを作成する必要があります。  
  
#### <a name="to-add-new-relationships-between-tables"></a>テーブル間に新しいリレーションシップを追加するには  
  
1.  モデル デザイナーでの**FactInternetSales**テーブルをクリックし、保持、 **OrderDate**列にカーソルをドラッグし、**日付**内の列、 **DimDate**テーブル、および離します。  

    間のアクティブなリレーションシップを作成したを示す実線が表示されます、 **OrderDate**内の列、 **Internet Sales**テーブルおよび**日付**列**日付**テーブル。 
  
      ![-テーブル-lesson4-新規と](../analysis-services/media/as-tabular-lesson4-new.png) 
  
    > [!NOTE]  
    > リレーションシップを作成するときに、主テーブルと関連する参照テーブルの間のカーディナリティとフィルターの方向が自動的に選択します。  
  
2.  **FactInternetSales**テーブルをクリックし、保持、 **DueDate**  列にカーソルをドラッグし、**日付**内の列、 **DimDate**テーブル、および離します。  
  
    間の非アクティブなリレーションシップを作成したを示す点線が表示されます、 **DueDate**内の列、 **FactInternetSales**テーブルおよび**日付**内の列**DimDate**テーブル。 テーブル間には複数のリレーションシップを設定できますが、一度にアクティブにできるのは 1 つだけです。  
  
3.  最後に、作成するもう 1 つのリレーションシップです。**FactInternetSales**テーブルをクリックし、保持、 **ShipDate**  列にカーソルをドラッグし、**日付**内の列、 **DimDate**テーブル、および離します。  
    
     ![として-テーブル-lesson4-newinactive](../analysis-services/media/as-tabular-lesson4-newinactive.png)
  
## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 5: 計算列の作成](../analysis-services/lesson-5-create-calculated-columns.md)です。
  
  
  
