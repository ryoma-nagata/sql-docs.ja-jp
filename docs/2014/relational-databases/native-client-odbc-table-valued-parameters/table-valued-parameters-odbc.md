---
title: テーブル値パラメーター (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC)
- ODBC, table-valued parameters
ms.assetid: ef06cd13-18e2-4c65-8ede-c3955d820e54
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce0cd9e87d4bd594fb2c2be4a01e9f2cf8ef4a27
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421791"
---
# <a name="table-valued-parameters-odbc"></a>テーブル値パラメーター (ODBC)
  ODBC のテーブル値パラメーターのサポートにより、クライアント アプリケーションは、1 回の呼び出しで複数の行をサーバーに送信することで、パラメーター化されたデータをサーバーに効率的に送信できます。  
  
 サーバー上のテーブル値パラメーターについては、次を参照してください。[テーブル値パラメーターの&#40;データベース エンジン&#41;](../tables/use-table-valued-parameters-database-engine.md)します。  
  
 ODBC でテーブル値パラメーターをサーバーに送信するには、次の 2 つの方法があります。  
  
-   テーブル値パラメーターのすべてのデータを SQLExecDirect または SQLExecute の呼び出し時にメモリにできます。 テーブル値に複数の行がある場合、このデータを配列に格納します。  
  
-   SQLExecDirect または SQLExecute が呼び出されたときに、アプリケーションは、テーブル値パラメーターの実行時データを指定できます。 この場合、テーブル値のデータの行をバッチ内で指定するか、必要なメモリ量を減らすために 1 つずつ指定することができます。  
  
 1 つ目の方法では、より多くのビジネス ロジックをストアド プロシージャにカプセル化できます。 たとえば、発注品目をテーブル値パラメーターとして渡す場合、注文入力のトランザクション全体を 1 つのストアド プロシージャにカプセル化することができます。 サーバーとのやり取りが 1 回で済むため、この方法は非常に効率的です。 また、異なるプロシージャを使用して、注文ヘッダーと発注品目を個別に処理することもできます。この場合、必要なコードが多くなり、クライアントとサーバー間のコントラクトが複雑になります。  
  
 2 つ目の方法は、膨大な量のデータを使用する一括操作のときに効率の良いメカニズムです。 この方法では、アプリケーションで最初にデータ行をメモリ内のバッファーに格納しなくても、データ行をサーバーにストリーム送信できます。  
  
 テーブル変数を作成するときに、制約と主キーを作成できます。 制約は、テーブル内のデータが特定の要件を満たしていることを確認するのに優れた方法です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ODBC テーブル値パラメーターの使用](uses-of-odbc-table-valued-parameters.md)  
 テーブル値パラメーターと ODBC の主なユーザー シナリオについて説明します。  
  
 [テーブル値パラメーター用の ODBC SQL 型](odbc-sql-type-for-table-valued-parameters.md)  
 SQL_SS_TABLE 型について説明します。 この型は、テーブル値パラメーターをサポートする新しい ODBC SQL 型です。  
  
 [テーブル値パラメーターの記述子フィールド](table-valued-parameter-descriptor-fields.md)  
 テーブル値パラメーターをサポートする記述子フィールドについて説明します。  
  
 [テーブル値パラメーターを構成する列の記述子フィールド](descriptor-fields-for-table-valued-parameter-constituent-columns.md)  
 テーブル値パラメーターで意味を持つ記述子フィールドについて説明します。  
  
 [テーブル値パラメーターの診断レコードのフィールド](table-valued-parameter-diagnostic-record-fields.md)  
 テーブル値パラメーターをサポートするために診断レコードに追加された 2 つの診断フィールドについて説明します。  
  
 [テーブル値パラメーターに影響を与えるステートメント属性](statement-attributes-that-affect-table-valued-parameters.md)  
 テーブル値パラメーター列に対処できるようにする記述子の新しいヘッダー フィールドについて説明します。  
  
 [テーブル値パラメーターおよび列の値のバインドとデータ転送](binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)  
 パラメーター バインドと、テーブル値パラメーターをサーバーに渡す方法について説明します。  
  
 [準備されたステートメント用のテーブル値パラメーターのメタデータ](table-valued-parameter-metadata-for-prepared-statements.md)  
 アプリケーションから、準備されたプロシージャ呼び出しのメタデータを取得する方法について説明します。  
  
 [テーブル値パラメーターの追加メタデータ](additional-table-valued-parameter-metadata.md)  
 SQLProcedureColumns、SQLTables、および SQLColumns を使用して、テーブル値パラメーターのメタデータを取得する方法について説明します。  
  
 [テーブル値パラメーターのデータ変換およびその他のエラーと警告](table-valued-parameter-data-conversion-and-other-errors-and-warnings.md)  
 テーブル値パラメーターの列値に関するエラーを処理する方法について説明します。  
  
 [複数バージョン間の互換性](cross-version-compatibility.md)  
 テーブル値パラメーターが、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] より前のバージョンのクライアントまたはサーバーで使用されるときに発生する可能性がある競合について説明します。  
  
 [ODBC テーブル値パラメーター API の概要](odbc-table-valued-parameter-api-summary.md)  
 テーブル値パラメーターをサポートする、ODBC 関数の一覧を示します。  
  
 [ODBC テーブル値パラメーターのプログラミング例](../../database-engine/dev-guide/odbc-table-valued-parameter-programming-examples.md)  
 一般的なタスクの実行方法について説明します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [テーブル値パラメーター &#40;SQL Server Native Client&#41;](../native-client/features/table-valued-parameters-sql-server-native-client.md)  
  
  
