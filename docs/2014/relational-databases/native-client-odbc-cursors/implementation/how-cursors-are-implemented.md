---
title: カーソルを実装する方法 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC], about ODBC cursors
ms.assetid: 2b1d7dd4-08a4-43fc-b3eb-70c183d0941f
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 80b3df4fd3b4e6e515de68b8e5f1a7af034bdb42
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423051"
---
# <a name="how-cursors-are-implemented"></a>カーソルの実装方法
  ODBC アプリケーションでは SQL ステートメントを実行する前に、1 つ以上のステートメント属性を設定することにより、カーソルの動作を制御します。 ODBC には、カーソルの特性を指定する方法として、次の 2 つが用意されています。  
  
-   カーソルの種類  
  
     カーソルの種類の SQL_ATTR_CURSOR_TYPE 属性を使用して設定[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)します。 ODBC カーソルの種類には、順方向専用、静的、キーセット ドリブン、混合、および動的があります。 カーソルの種類を設定することは、カーソルを指定するための ODBC 独自の方法でした。  
  
-   カーソルの動作  
  
     SQL_ATTR_CURSOR_SCROLLABLE と SQL_ATTR_CURSOR_SENSITIVITY 属性を使用してカーソルの動作を設定**SQLSetStmtAttr**します。 これらの属性は、ISO 標準で DECLARE CURSOR ステートメント用に定義されている SCROLL キーワードと SENSITIVE キーワードをモデルにしたものです。 これら 2 つの ISO オプションは、ODBC Version 3.0 で導入されました。  
  
 ODBC カーソルの特性は、これら 2 つの方法のいずれかを使用して指定する必要がありますが、ODBC カーソルの種類を使用することをお勧めします。  
  
 ODBC アプリケーションではカーソルの種類を設定すること以外に、1 回のフェッチで返される行数、同時実行オプション、トランザクション分離レベルなど、他のオプションも設定します。 これらのオプションは、ODBC 形式のカーソル (順方向専用、静的、キーセット ドリブン、混合、および動的) または ISO 形式のカーソル (スクロール機能と感度) に対して設定できます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、さまざまな種類のカーソルを物理的に実装するためにいくつかの方法をサポートしています。 このドライバーでは、いくつかの種類のカーソルは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定の結果セットを使用して実装されます。また ODBC カーソル ライブラリを使用してサーバー カーソルとして実装される場合もあります。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [SQL Server の既定の結果セットの使用](using-sql-server-default-result-sets.md)  
  
-   [サーバー カーソルの使用](using-server-cursors.md)  
  
-   [ODBC カーソル ライブラリ](odbc-cursor-library.md)  
  
## <a name="see-also"></a>参照  
 [カーソルを使用して&#40;ODBC&#41;](../using-cursors-odbc.md)  
  
  
