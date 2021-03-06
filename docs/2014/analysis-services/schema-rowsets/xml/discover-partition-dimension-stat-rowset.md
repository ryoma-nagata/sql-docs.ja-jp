---
title: DISCOVER_PARTITION_DIMENSION_STAT Rowset | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bf4626b3-4d6b-4795-bb01-df335fb9c09a
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9f4dc209f985cafe804f81fa54fa68c56655d3e4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310742"
---
# <a name="discoverpartitiondimensionstat-rowset"></a>DISCOVER_PARTITION_DIMENSION_STAT 行セット
  パーティションに関連付けられているディメンションについての統計を返します。  
  
 **適用対象:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_PARTITION_DIMENSION_STAT`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|説明|  
|-----------------|--------------------|-----------------|-----------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|必須|データベースの名前。<br /><br /> この列は制限リストに必要です。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|必須|キューブまたはテーブル モデルの名前。<br /><br /> この列は制限リストに必要です。|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|必須|メジャー グループの名前。<br /><br /> この列は制限リストに必要です。|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|必須|パーティションの名前。<br /><br /> この列は制限リストに必要です。|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||ディメンションの名前。<br /><br /> この列は制限リストに必要です。|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||ディメンションの属性の名前。|  
|`ATTRIBUTE_INDEXED`|`DBTYPE_BOOL`||true の場合、属性にインデックスが設定されていることを示します。それ以外の場合は false です。|  
|`ATTRIBUTE_COUNT_MIN`|`DBTYPE_I8`||属性の最小数。|  
|`ATTRIBUTE_COUNT_MAX`|`DBTYPE_I8`||属性の最大数。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd8e-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  
