---
title: SkipLine メソッド |Microsoft ドキュメント
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
- _Stream::raw_SkipLine
- _Stream::SkipLine
helpviewer_keywords:
- Skipline method [ADO]
ms.assetid: 0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b5a2c6c5808abdcb13acb00c967ef35eeb943148
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282051"
---
# <a name="skipline-method"></a>SkipLine メソッド
テキストを読み取るときに 1 行全体をスキップ[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>コメント  
 次の行区切り記号を含むすべての文字はスキップされます。 既定では、 [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)は**adCRLF**です。 過去のスキップしようとする場合[EOS](../../../ado/reference/ado-api/eos-property.md)、現在の位置のままになります**EOS**です。  
  
 **SkipLine**メソッドがテキスト ストリームで使用される ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
