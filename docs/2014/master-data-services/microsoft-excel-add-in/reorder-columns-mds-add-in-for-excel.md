---
title: 列の並べ替え (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ac00462e-c0f7-4b8d-86f2-d9eda2598a15
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: eb9fb3e45cbe3adda1c3800a7b74b54c97d9c42c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271358"
---
# <a name="reorder-columns-mds-add-in-for-excel"></a>列の並べ替え (Excel 用 MDS アドイン)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] では、読み込み前に一覧をフィルター処理して列を並べ替えることができます。  
  
 **[フィルター]** ダイアログ ボックスの属性を並べ替えると、Excel には新しい順序でデータが読み込まれます。 しかし、次にその属性データをフィルター処理すると、元のデザインの順序に戻ります。 順序を完全に変更するには、管理者がマスター データ マネージャーの **[システム管理]** 領域で順序を変更する必要があります。 詳細については、「 [Change the Order of Attributes](../change-the-order-of-attributes.md)」を参照してください。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
### <a name="to-reorder-mds-managed-columns"></a>MDS によって管理される列を並べ替えるには  
  
1.  Excel を開いて、 **[マスター データ]** タブで MDS リポジトリに接続します。 詳細については、「[MDS リポジトリへの接続 (Excel 用 MDS アドイン)](connect-to-an-mds-repository-mds-add-in-for-excel.md)」を参照してください。  
  
2.  **[マスター データ エクスプローラー]** ペインで、モデルおよびバージョンを選択します。 エンティティの一覧が作成されます。  
  
    -   **[マスター データ エクスプローラー]** ペインが表示されない場合は、 **[接続と読み込み]** グループの **[エクスプローラーの表示]** をクリックします。  
  
    -   **[マスター データ エクスプローラー]** ペインが無効になっている場合は、既存のシートに MDS によって管理されるデータが既に含まれています。 ペインを有効にするには、新しいワークシートを開きます。  
  
3.  **[マスター データ エクスプローラー]** ペインで、エンティティをクリックします。  
  
4.  **[接続と読み込み]** グループで、 **[フィルター]** をクリックします。  
  
5.  **[フィルター]** ダイアログ ボックスの **[列]** セクションに表示される属性の一覧で、移動する属性をクリックします。  
  
6.  一覧の右側で、 **上** 矢印または **下** 矢印をクリックして、ワークシート内の属性を左右に移動します。  
  
7.  ワークシート内で目的の順序 (左から右) となるまで、各属性について手順 7. を繰り返します。  
  
8.  **[データの読み込み]** をクリックします。 MDS によって管理されるデータがシートに入力され、指定した順序で列が表示されます。  
  
## <a name="see-also"></a>参照  
 [データの読み込み&#40;MDS アドインの Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
  
