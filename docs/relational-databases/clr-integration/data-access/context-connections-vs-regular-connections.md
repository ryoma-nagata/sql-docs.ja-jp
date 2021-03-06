---
title: 通常とは。コンテキスト接続 |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 938ae2b6a740f793a87a1ed634d2d02b061a6123
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37356324"
---
# <a name="context-connections-vs-regular-connections"></a>コンテキスト接続とします。通常の接続
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  リモート サーバーに接続している場合は、常に、コンテキスト接続ではなく通常の接続を使用します。 ストアド プロシージャや関数を実行している同一サーバーに接続する必要がある場合は、ほとんどの場合、コンテキスト接続を使用します。 コンテキスト接続には、同一のトランザクション領域で実行され、再認証が不要であるなどの利点があります。  
  
 また、コンテキスト接続を使用すると、通常、パフォーマンスが向上し、リソースの使用が抑えられます。 コンテキスト接続はインプロセスのみの接続なので、ネットワーク プロトコルやトランスポート層を迂回して Transact-SQL ステートメントを送信したり結果を受信することで、"直接" サーバーにアクセスできます。 認証プロセスも同様に迂回されます。 次の図の主要コンポーネント、 **SqlClient**プロバイダーとコンテキスト接続を使用する場合と通常の接続を使用する場合、相互に、さまざまなコンポーネントがやり取りする方法を管理します。  
  
 ![コードのコンテキストと通常の接続のパス。](../../../relational-databases/clr-integration/data-access/media/clrintdataaccess.gif "コンテキストと通常の接続のコード パス。")  
  
 コンテキスト接続で使用するコード パスは、通常の接続よりも短く、関連するコンポーネントの数も少ないので、サーバーへの要求とサーバーからの結果の取得が通常の接続よりも速くなることが期待できます。 サーバーでのクエリの実行時間は、どちらの接続でも同じです。  
  
 同じサーバーに対して通常の接続を別に開く必要が生じる場合もあります。 たとえば、上で説明されている、コンテキスト接続を使用して制限があり、[標準モードとコンテキスト接続に関する制限事項](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md)します。  
  
## <a name="see-also"></a>参照  
 [コンテキスト接続](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
