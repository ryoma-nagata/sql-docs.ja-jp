---
title: MSSQLSERVER_41399 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18f6619ed33640a0659e4260a8c40dedcb225727
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425121"
---
# <a name="mssqlserver41399"></a>MSSQLSERVER_41399
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|41399|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|MAX_SORT_ROW_WIDTH_EXCEEDED|  
|メッセージ テキスト|並べ替え操作が複雑すぎます。 詳細については、SQL Server オンライン ブックを参照してください。|  
  
## <a name="explanation"></a>説明  
 結合操作と集計操作の結果を並べ替えると、並べ替えバッファー内の行のサイズが大きくなり、並べ替え操作の複雑さが増します。 このエラーは、行のサイズが、ネイティブ コンパイル ストアド プロシージャの Sort 演算子でサポートされる最大サイズを超えていることを意味します。 並べ替えバッファー内の行のサイズは、単純に、結合の数および集計関数の数と種類で決まることに注意してください。 ベース テーブル内の行のサイズは、バッファー内の行のサイズに影響しません。  
  
## <a name="user-action"></a>ユーザーの操作  
 結合または集計関数を削除することでクエリの複雑さを軽減してください。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
