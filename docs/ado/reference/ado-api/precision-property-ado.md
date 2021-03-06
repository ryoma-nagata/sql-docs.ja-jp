---
title: Precision プロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Precision
- Field20::Precision
helpviewer_keywords:
- Precision property [ADO]
ms.assetid: 1fa38e78-6b5b-414d-ba0a-3dd26b29b766
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 630bae40ab9e473656abeb3fa8cdb79de89e258c
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280641"
---
# <a name="precision-property-ado"></a>Precision プロパティ (ADO)
内の数値の正確さの度合いを示す、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクトまたは数値に[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**バイト**値を表すために使用する最大桁数を示す値。  
  
## <a name="remarks"></a>コメント  
 使用して、**精度**型の数値の値を表すために使用する最大桁数を決定するプロパティ**パラメーター**または**フィールド**オブジェクト。  
  
 読み取り/書き込みするには、値、**パラメーター**オブジェクト。  
  
 **フィールド**オブジェクト、**精度**は通常読み取り専用です。 ただし、新規の**フィールド**に追加されたオブジェクト、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)のコレクション、[レコード](../../../ado/reference/ado-api/record-object-ado.md)、**精度**読み取り/書き込みのみ後に、[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティを**フィールド**が指定されているデータ プロバイダーが追加、新しいおよび**フィールド**を呼び出すことによって[更新](../../../ado/reference/ado-api/update-method.md)のメソッド、**フィールド**コレクション。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Field オブジェクト](../../../ado/reference/ado-api/field-object.md)|[Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>参照  
 [NumericScale と (VB) の有効桁数のプロパティの例](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale と (vc++) の有効桁数のプロパティの例](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [NumericScale プロパティ (ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)
