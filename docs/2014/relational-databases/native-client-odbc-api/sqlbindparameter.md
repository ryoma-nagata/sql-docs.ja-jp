---
title: SQLBindParameter |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
caps.latest.revision: 46
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50d2c364a6632052dbab387544e6c224d0bb1e05
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37430691"
---
# <a name="sqlbindparameter"></a>SQLBindParameter
  `SQLBindParameter` データを提供するために使用するときにデータ変換の負担を解消できます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー、アプリケーションのクライアントとサーバーの両方のコンポーネントの大幅なパフォーマンスが大幅に向上します。 その他に、概数データ型を挿入または更新するときに有効桁数を失うことが少なくなるという利点もあります。  
  
> [!NOTE]  
>  `char` 型と `wchar` 型のデータを image 型の列に挿入するときは、バイナリ形式に変換後のデータのサイズではなく、渡すデータのサイズを使用します。  
  
 パラメーター配列の配列要素の 1 つで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー エラーが発生しても、残りの配列要素に対しては引き続きステートメントが実行されます。 アプリケーションがこのステートメントのパラメーター状態要素の配列をバインドした場合は、その配列を基にして、エラーが発生したパラメーター行を特定できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを使用する場合は、入力パラメーターのバインド時に SQL_PARAM_INPUT を指定します。 OUTPUT キーワードで定義されたストアド プロシージャ パラメーターをバインドするときは、SQL_PARAM_OUTPUT または SQL_PARAM_INPUT_OUTPUT のみを指定してください。  
  
 [SQLRowCount](sqlrowcount.md)は信頼できません、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーの場合は、バインドされたパラメーター配列の配列要素、ステートメントの実行でエラーが発生します。 また、ODBC ステートメント属性 SQL_ATTR_PARAMS_PROCESSED_PTR は、エラーが発生する前に処理された行数を報告します。 その後、必要に応じてパラメーター状態配列全体をアプリケーションで調査することにより、正常に実行されたステートメント数を検出できます。  
  
## <a name="binding-parameters-for-sql-character-types"></a>SQL 文字型のパラメーターのバインド  
 渡された SQL データ型が文字型の場合*ColumnSize*文字 (バイトではなく) のサイズです。 (バイト単位)、データの文字列の長さが 8000 より大きい場合*ColumnSize*に設定する必要があります`SQL_SS_LENGTH_UNLIMITED`SQL 型のサイズに制限がないことを示します。  
  
 たとえば、SQL データ型の場合`SQL_WVARCHAR`、 *ColumnSize* 4000 より大きくする必要がありますできません。 実際のデータ長がより大きいかどうか、4000、 *ColumnSize*に設定する必要があります`SQL_SS_LENGTH_UNLIMITED`ように`nvarchar(max)`ドライバーによって使用されます。  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a>SQLBindParameter とテーブル値パラメーター  
 その他のパラメーター型と同様に、テーブル値パラメーターは、SQLBindParameter によってバインドされます。  
  
 テーブル値パラメーターがバインドされた後、そのパラメーターの列もバインドされます。 列をバインドするを呼び出す[SQLSetStmtAttr](sqlsetstmtattr.md) SQL_SOPT_SS_PARAM_FOCUS にテーブル値パラメーターの序数を設定します。 次に、テーブル値パラメーターの各列に対して SQLBindParameter を呼び出します。 最上位パラメーター バインドに戻るには、SQL_SOPT_SS_PARAM_FOCUS に 0 を設定します。  
  
 テーブル値パラメーターの記述子フィールドへのマッピングのパラメーターについては、次を参照してください。[バインドと Data Transfer of Table-Valued パラメーターおよび列の値](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)します。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)します。  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a>SQLBindParameter による機能強化された日付と時刻のサポート  
 説明されているように、日付/時刻型のパラメーター値が変換されます[C から SQL への変換](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)します。 注型のパラメーター`time`と`datetimeoffset`必要があります*ValueType*として指定された`SQL_C_DEFAULT`または`SQL_C_BINARY`場合、対応する構造体 (`SQL_SS_TIME2_STRUCT`と`SQL_SS_TIMESTAMPOFFSET_STRUCT`) 使用されます。  
  
 詳細については、次を参照してください。[日付と時刻の強化&#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)します。  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a>SQLBindParameter による大きな CLR UDT のサポート  
 `SQLBindParameter` は、大きな CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型&#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)します。  
  
## <a name="see-also"></a>参照  
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)   
 [SQLBindParameter 関数](http://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
