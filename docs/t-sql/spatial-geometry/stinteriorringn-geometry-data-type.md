---
title: STInteriorRingN (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STInteriorRingN_TSQL
- STInteriorRingN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STInteriorRingN (geometry Data Type)
ms.assetid: 47310f9f-2cdb-41e0-a6da-7c3cfbf139ac
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 07df50a6de97ea992935b536c19ffab8eb9d0fd9
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36250334"
---
# <a name="stinteriorringn-geometry-data-type"></a>STInteriorRingN (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

**Polygongeometry** インスタンスの指定した内部リングを返します。
  
## <a name="syntax"></a>構文  
  
```  
  
.STInteriorRingN ( expression )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 1 から **geometry** インスタンスの内部リング数までの **int** 式です。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の戻り値の型: **geometry**  
  
 CLR 戻り値の型: **SqlGeometry**  
  
 Open Geospatial Consortium (OGC) の型: **LineString**  
  
## <a name="remarks"></a>Remarks  
 **geometry** インスタンスが多角形ではない場合、このメソッドは **NULL** を返します。 また、式がリングの数より大きい場合、このメソッドは **ArgumentOutOfRangeException** をスローします。 リングの数は `STNumInteriorRing``()` を使用して返すことができます。  
  
## <a name="examples"></a>使用例  
 `Polygon` インスタンスを作成し、`STInteriorRingN()` を使用して多角形の外部リングを **LineString** として返す例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STInteriorRingN(1).ToString();  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

