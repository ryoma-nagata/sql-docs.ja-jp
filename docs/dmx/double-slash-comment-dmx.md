---
title: 倍精度浮動小数点 (コメント) (DMX) をスラッシュ |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ca3b7040e5d51c324ddd50d489243b0f67f64feb
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37981834"
---
# <a name="double-slash-comment-dmx"></a>2 つのスラッシュ (コメント) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  テキストを示す文字列を[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]は実行されません。 コメントは、データ マイニング拡張機能 (DMX) ステートメント内で入れ子にしたり、コード行の最後に含めたり、別の行に挿入したりすることができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
// Comment_Text   
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>コメント  
 単一行のみのコメントには、// を使用します。 // を使用して挿入されたコメントは、改行文字によって分割されます。  
  
 コメントの長さには制限がありません。  
  
 DMX でさまざまな種類のコメントを使用する方法の詳細については、次を参照してください。[コメント&#40;DMX&#41;](../dmx/comments-dmx.md)します。  
  
## <a name="see-also"></a>参照  
 [スラッシュ アスタリスク&#40;コメント&#41; &#40;DMX&#41;](../dmx/slash-star-comment-dmx.md)   
 [--&#40;コメント&#41; &#40;DMX&#41;の概要](../dmx/comment-dmx-summary.md)   
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [演算子&#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
