---
title: 探索データ (SQL Server データ マイニング アドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- histogram [data mining]
- data visualization
ms.assetid: 714845a9-4c27-461a-9ba3-149e1e818386
caps.latest.revision: 20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 813da97a8128464ef105d27780f459060867f11c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177029"
---
# <a name="explore-data-sql-server-data-mining-add-ins"></a>データの探索 (SQL Server データ マイニング アドイン)
  ![探索データ ウィザード](media/dmc-explore.gif "データの探索ウィザード")  
  
 **データの探索**ウィザードを使用して、型とデータ テーブル内のデータの量を把握できます。 ウィザードは、選択した列の分布と値を一度に 1 列ずつグラフ化します。 その後、データのグループ化の方法を変更したり、確認用に内容を示すグラフを Excel ブックにコピーしたりできます。  
  
 データに連続する数値データが含まれている場合は、次の 2 つのビューを切り替えることができます。  
  
-   **線グラフ。** このグラフは、データ値を X 軸、ケース数を Y 軸として表示します。  
  
-   **横棒グラフ。** このグラフは、それぞれの値のケース数に基づいて値をグループ化します。  
  
 データにグループが見つかると、データ値の実際の分布が使用されます。 そのため、横棒グラフには、一般的な 10 や 100 などの整数値軸マーカーが表示されません。 代わりに、横棒グラフに表示される範囲は 43521-55603 のようになります (Income 列の場合)。  
  
 データを別の範囲にグループ化するには、データを分析する前に Excel でこの操作を行う必要があります。 または、データを使用してラベルを変更することができます、[ラベルの変更](relabel-sql-server-data-mining-add-ins.md)ウィザード。  
  
## <a name="using-the-explore-data-wizard"></a>データの探索ウィザードの使用  
  
1.  **データ マイニング**リボンで、をクリックして**データの探索**します。  
  
2.  **ソースの選択** ダイアログ ボックスで、テーブルまたはデータを含むセルの範囲を選択します。  
  
3.  **列の選択** ダイアログ ボックスで、ウィンドウに表示するサンプル データから、分析する列を選択します。  
  
4.  **データの探索** ダイアログ ボックスで、データの分布を表示するため、グラフの種類を選択します。  
  
5.  オプションで、新しい列をデータに追加したり、データを分割する方法を変更したり、グラフを Excel にコピーしたりできます。  
  
### <a name="requirements"></a>要件  
 使用する、**データの探索**ウィザード、データは、Excel データ テーブルである必要があります。   
  
## <a name="see-also"></a>参照  
 [データ マイニングの準備のチェック リスト](checklist-of-preparation-for-data-mining.md)  
  
  
