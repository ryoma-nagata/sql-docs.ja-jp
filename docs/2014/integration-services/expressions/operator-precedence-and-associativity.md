---
title: 演算子の優先順位と結合規則 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- associativity [Integration Services]
- precedence [Integration Services]
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1cd491119fb0af27eb9e2692271fe168e630dc98
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219642"
---
# <a name="operator-precedence-and-associativity"></a>演算子の優先順位と結合規則
  式エバリュエーターがサポートする演算子セット内の各演算子には、優先順位の階層内で指定された優先順位があり、演算子が評価される方向が含まれています。 演算子の評価の方向は、演算子の結合規則と呼ばれます。 優先順位の高い演算子が先に評価されます。 複合式に複数の演算子がある場合、演算子の優先順位により、操作が実行される順序が決定されます。 実行される順序により、結果の値は大きく変わります。 演算子の一部には、優先順位が同じものがあります。 式に複数の演算子が含まれており、その優先順位が同じ場合、それらの演算子は、左から右または右から左の方向に評価されます。  
  
 次の表に、演算子の優先順位が高い順に一覧表示します。 同じレベルの演算子の優先順位は、同じです。  
  
|演算子記号|演算の種類|結合規則|  
|---------------------|-----------------------|-------------------|  
|( )|式|左から右|  
|–、!、~|単項演算子|右から左|  
|キャスト|単項演算子|右から左|  
|*、/、%|乗算|左から右|  
|+、–|加法|左から右|  
|\<、>、\<=、>=|リレーショナル|左から右|  
|==、!=|等式|左から右|  
|&|ビット演算子 AND|左から右|  
|^|ビット演算子排他的 OR|左から右|  
|&#124;|ビット演算子包含的 OR|左から右|  
|&&|論理積|左から右|  
|&#124;&#124;|論理和|左から右|  
|? :|条件式|右から左|  
  
## <a name="see-also"></a>参照  
 [演算子&#40;SSIS 式&#41;](operators-ssis-expression.md)  
  
  
