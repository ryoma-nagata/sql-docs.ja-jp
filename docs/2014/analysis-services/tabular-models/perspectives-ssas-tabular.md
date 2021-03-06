---
title: パースペクティブ (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1f78c3a1-ce2c-4e7f-a277-71a657692bea
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5ad07ccba62df7054f4ec19e0713192154ad62db
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37304302"
---
# <a name="perspectives-ssas-tabular"></a>パースペクティブ (SSAS テーブル)
  テーブル モデルでパースペクティブを使用すると、ビジネス固有またはアプリケーション固有のビューポイントをモデルに対して的を絞って作成するための、表示可能なサブセットを定義できます。  
  
 このトピックのセクション:  
  
-   [利点](#bkmk_understanding)  
  
-   [パースペクティブのテスト](#bkmk_testpersp)  
  
-   [関連タスク](#bkmk_related_tasks)  
  
##  <a name="bkmk_understanding"></a> 利点  
 テーブル モデルは非常に複雑であるために、扱いが困難なことがあります。 テーブル モデルは、1 つだけで多くのテーブル、メジャー、ディメンションを持つ完全なデータ ウェアハウスの内容を表すことができます。 しかしこのような複雑さは、ビジネス インテリジェンス要件やレポート要件を満たすために、モデルのごく一部分しか操作する必要のないユーザーにとっては大きな負担になります。  
  
 パースペクティブでは、テーブル、列、およびメジャー (KPI を含む) がフィールド オブジェクトとして定義されます。 パースペクティブごとに複数の表示可能なフィールドを選択できます。 たとえば、1 つのモデルに商品、売上、財務、従業員、および地域のデータが含まれている場合があります。 販売部門では商品、売上、プロモーション、地域のデータは必要ですが、従業員や財務のデータはおそらく必要ありません。 同様に、人事部門では販売プロモーションや地域のデータは必要ありません。  
  
 パースペクティブが定義されたモデルに (データ ソースとして) 接続する際、ユーザーは使用するパースペクティブを選択できます。 たとえば、Excel のモデル データ ソースに接続する際、人事部門のユーザーはデータ接続ウィザードの [テーブルとビューの選択] ページにある人事パースペクティブを選択できます。 ピボットテーブルのフィールド一覧には、人事パースペクティブに定義されたフィールド (テーブル、列、およびメジャー) のみが表示されます。  
  
 パースペクティブは、セキュリティ メカニズムとして使用するためのものではなく、ユーザーの使用体験をより良いものにするためのツールとして使用するものです。 特定のパースペクティブのセキュリティはすべて、基になるモデルから継承されます。 パースペクティブでは、ユーザーがアクセス権を持っていないモデル オブジェクトにアクセスできません。 パースペクティブでモデルのオブジェクトへのアクセスが提供されるようにするには、そのモデル データベースのセキュリティを解決しておく必要があります。 セキュリティ ロールを使用して、モデルのメタデータとデータをセキュリティ保護することができます。 詳しくは、「[ロール &#40;SSAS テーブル&#41;](roles-ssas-tabular.md)」をご覧ください。  
  
##  <a name="bkmk_testpersp"></a> パースペクティブのテスト  
 モデルの作成時に、モデル デザイナーの Excel で分析機能を使用して、定義したパースペクティブの有効性をテストできます。 モデル デザイナーで **[モデル]** メニューの **[Excel で分析]** をクリックすると、Excel が開く前に **[資格情報とパースペクティブの選択]** ダイアログ ボックスが表示されます。 このダイアログ ボックスでは、データ ソースとしてモデル ワークスペース データベースに接続し、データを表示するために使用する、現在のユーザー名、別のユーザー、ロール、およびパースペクティブを指定できます。  
  
##  <a name="bkmk_related_tasks"></a> 関連タスク  
  
|トピック|説明|  
|-----------|-----------------|  
|[作成し、管理のパースペクティブ&#40;SSAS 表形式&#41;](perspectives-ssas-tabular.md)|モデル デザイナーで [パースペクティブ] ダイアログ ボックスを使用して、パースペクティブを作成し管理する方法を説明します。|  
  
## <a name="see-also"></a>参照  
 [ロール&#40;SSAS 表形式&#41;](roles-ssas-tabular.md)   
 [階層&#40;SSAS 表形式&#41;](hierarchies-ssas-tabular.md)  
  
  
