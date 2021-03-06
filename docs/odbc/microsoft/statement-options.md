---
title: ステートメントのオプション |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- custom statement options [ODBC]
- statement options [ODBC]
- ODBC driver for Oracle [ODBC], statement options
ms.assetid: cd73b769-c8b5-43e0-9f80-b3011b7a6162
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9402bb45fbd995aedc53e4d490709e1e6504a5f9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904367"
---
# <a name="statement-options"></a>ステートメントのオプション
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 これらのオプションには、アプリケーション内の特定の実行ステートメントのカスタマイズができるようにします。  
  
|ステートメントのオプション|注|  
|----------------------|-----------|  
|SQL_BIND_TYPE|2,147, 483,647 バイトまたは使用可能なメモリを超えることはできません。|  
|SQL_CONCURRENCY|許可される値は、次を参照してください。、[カーソルの種類および同時実行の組み合わせ](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md)です。|  
|SQL_CURSOR_TYPE|ドライバーでは、SQL_CURSOR_DYNAMIC は許可されません。 参照してください[SQLSetScrollOptions](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md)詳細についてはします。 許可される値は、次を参照してください。、[カーソルの種類および同時実行の組み合わせ](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md)です。|  
|SQL_GET_BOOKMARK|現在のレコード数のブックマークは、32 ビット整数値を返します。 取得のみです。設定できません。|  
|SQL_KEYSET_SIZE|0 に設定できます。|  
|SQL_MAX_ROWS|結果から返される行の最大数を設定します。|  
|SQL_ROW_NUMBER|結果セット内の現在の行の位置を示す 32 ビット整数を返します。 取得のみです。設定できません。|  
|SQL_ROWSET_SIZE|4,294,967,296 行を超えることはできません。ただし、リクエストを処理するコンピューターに十分な仮想メモリが必要です。|  
|SQL_USE_BOOKMARKS|SQL_UB_ON に SQL_USE_BOOKMARKS の設定をサポートし、固定長のブックマークを公開します。|
