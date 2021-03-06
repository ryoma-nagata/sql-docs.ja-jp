---
title: プログラム変数から一括コピー |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], program variables
- bcp_bind function
- mapping data types [ODBC]
- SQL Server Native Client ODBC driver, bulk copy
- data types [ODBC], bulk copying
- ODBC, bulk copy operations
- program variables [ODBC]
ms.assetid: e4284a1b-7534-4b34-8488-b8d05ed67b8c
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 253123cc62751c39c39e9f5ab9282e2b1e6a3c10
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420021"
---
# <a name="bulk-copying-from-program-variables"></a>プログラム変数からの一括コピー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  プログラム変数から直接一括コピーできます。 行のデータを保持する変数を割り当てた後[bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)一括コピーを開始するには、呼び出す[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)の各列に関連付けられているプログラム変数の形式と場所を指定するには列。 各変数のデータを呼び出すし[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)サーバーに 1 行のデータを送信します。 変数を入力し、呼び出す手順を繰り返す**bcp_sendrow**のすべての行は、サーバーに送信された、まで呼び出して[bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)操作が完了したかを指定します。  
  
 **Bcp_bind * * * pData*パラメーターには、列にバインドされている変数のアドレスが含まれています。 各列のデータは、次の 2 つの方法のいずれかを使用して格納できます。  
  
-   データを保持する変数を 1 つ割り当てる  
  
-   データ変数の直前にインジケーター変数を割り当てる  
  
 インジケーター変数は、可変長列のデータの長さを示します。列で NULL 値を許容している場合は NULL 値も示します。 データ変数を使用すると、専用の場合、この変数のアドレスに保存、**bcp_bind * * * pData*パラメーター。 インジケーター変数のアドレスが格納されているインジケーター変数を使用する場合、**bcp_bind * * * pData*パラメーター。 一括コピー関数を追加して、data 変数の場所を計算する、**bcp_bind * * * cbIndicator*と*pData*パラメーター。  
  
 **bcp_bind**可変長データを処理するための 3 つのメソッドをサポートしています。  
  
-   使用*cbData*データ変数のみにします。 配置内のデータの長さ*cbData*します。 一括データの長さには、変更がコピーされるたびに呼び出す[bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)をリセットする*cbData*します。 その他の 2 つのメソッドのいずれかが使用されている場合に SQL_VARLEN_DATA を指定*cbData*します。 列に指定されたすべてのデータ値が NULL の場合は、指定の SQL_NULL_DATA *cbData*します。  
  
-   インジケーター変数を使用します。 新しい各データ値をデータ変数に移動するときに、その値の長さをインジケーター変数に格納します。 その他の 2 つのメソッドのいずれかが使用されている場合に 0 を指定*cbIndicator*します。  
  
-   ターミネータ ポインターを使用します。 ロード、**bcp_bind * * * pTerm*パラメーター データを終了するビット パターンのアドレスを使用します。 NULL を指定する場合は、その他の 2 つのメソッドのいずれかが使用されている*pTerm*します。  
  
 これらのメソッドの 3 つすべては同じで使用できる**bcp_bind**呼び出すには、コピーするデータ量の最小の仕様を使用する場合。  
  
 **Bcp_bind * * * 型*パラメーターは、Db-library のデータ型識別子、ODBC データ型識別子されません。 Db-library のデータ型識別子は、ODBC で使用するための sqlncli.h で定義されて**bcp_bind**関数。  
  
 一括コピー関数では、すべての ODBC C データ型をサポートしているわけではありません。 たとえば、一括コピー関数が ODBC SQL_C_TYPE_TIMESTAMP 構造体をサポートして、これを使用して、 [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)または[SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) SQL_C_CHAR 変数に ODBC sql_type_timestamp 型のデータを変換します。 使用する場合**bcp_bind**で、*型*sqlcharacter を変数にバインドするパラメーター、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime**列、一括コピー関数を変換、適切な datetime 形式の文字変数にタイムスタンプ エスケープ句。  
  
 次の表は、ODBC SQL データ型のマッピングで使用する推奨されるデータ型、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。  
  
|ODBC SQL データ型|ODBC C データ型|bcp_bind*型*パラメーター|SQL Server データ型|  
|-----------------------|----------------------|--------------------------------|--------------------------|  
|SQL_CHAR|SQL_C_CHAR|SQLCHARACTER|**character**<br /><br /> **char**|  
|SQL_VARCHAR|SQL_C_CHAR|SQLCHARACTER|**varchar**<br /><br /> **文字がさまざまな**<br /><br /> **char varying**<br /><br /> **sysname**|  
|SQL_LONGVARCHAR|SQL_C_CHAR|SQLCHARACTER|**text**|  
|SQL_WCHAR|SQL_C_WCHAR|SQLNCHAR|**nchar**|  
|SQL_WVARCHAR|SQL_C_WCHAR|SQLNVARCHAR|**nvarchar**|  
|SQL_WLONGVARCHAR|SQL_C_WCHAR|SQLNTEXT|**ntext**|  
|SQL_DECIMAL|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **dec**<br /><br /> **money**<br /><br /> **smallmoney**|  
|SQL_NUMERIC|SQL_C_NUMERIC|SQLNUMERICN|**numeric**|  
|SQL_BIT|SQL_C_BIT|SQLBIT|**bit**|  
|SQL_TINYINT (符号付き)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_TINYINT (符号なし)|SQL_C_UTINYINT|SQLINT1|**tinyint**|  
|SQL_SMALL_INT (符号付き)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_SMALL_INT (符号なし)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **整数 (integer)**|  
|SQL_INTEGER (符号付き)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **整数 (integer)**|  
|SQL_INTEGER (符号なし)|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **dec**|  
|SQL_BIGINT (符号付きと符号なし)|SQL_C_CHAR|SQLCHARACTER|**bigint**|  
|SQL_REAL|SQL_C_FLOAT|SQLFLT4|**real**|  
|SQL_FLOAT|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_DOUBLE|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_BINARY|SQL_C_BINARY|SQLBINARY|**[バイナリ]**<br /><br /> **timestamp**|  
|SQL_VARBINARY|SQL_C_BINARY|SQLBINARY|**varbinary**<br /><br /> **バイナリのさまざまな**|  
|SQL_LONGVARBINARY|SQL_C_BINARY|SQLBINARY|**image**|  
|SQL_TYPE_DATE|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIME|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIMESTAMP|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_GUID|SQL_C_GUID|SQLUNIQUEID|**uniqueidentifier**|  
|SQL_INTERVAL_|SQL_C_CHAR|SQLCHARACTER|**char**|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 署名されていない**tinyint**の符号なし**smallint**、符号なしまたは**int**データ型。 値のデータの損失を防ぐためには、これらのデータ型を移行するときに、作成、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [次へ] の最大の整数データ型を含むテーブル。 ユーザーが元のデータ型で許容されている範囲外の値を後から追加しないようにするには、次のようにルールを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列に適用し、ソースのデータ型でサポートされる範囲内に許容値を限定します。  
  
```  
CREATE TABLE Sample_Ints(STinyIntCol   SMALLINT,  
USmallIntCol INT)  
GO  
CREATE RULE STinyInt_Rule  
AS   
@range >= -128 AND @range <= 127  
GO  
CREATE RULE USmallInt_Rule  
AS   
@range >= 0 AND @range <= 65535  
GO  
sp_bindrule STinyInt_Rule, 'Sample_Ints.STinyIntCol'  
GO  
sp_bindrule USmallInt_Rule, 'Sample_Ints.USmallIntCol'  
GO  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interval データ型を直接サポートしません。 アプリケーション文字列と interval のエスケープ シーケンスを格納できる、ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字型列。 アプリケーションでは、後で使用するためにこれらのエスケープ シーケンスを読み取ることができますが、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント内では使用できません。  
  
 すばやくデータを読み込む一括コピー関数を使用できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ODBC データ ソースから読み取られました。 使用して、 [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)プログラム変数に結果セットの列をバインドするを使用し、 **bcp_bind**一括コピー操作をプログラム変数にバインドします。 呼び出す[SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)または**SQLFetch**プログラムの変数と呼び出しに ODBC データ ソースからデータの行をフェッチ[bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)データを一括コピープログラム変数から[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
 アプリケーションで使用できます、 [bcp_colptr](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md)関数で指定したデータ変数のアドレスを変更する必要があるときにいつでも、 **bcp_bind** *pData*パラメーター。 アプリケーションで使用できます、 [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)関数の最初に指定したデータの長さを変更する必要があるときにいつでも、**bcp_bind * * * cbData*パラメーター。  
  
 データを読み取ることができません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一括コピーを使用してプログラム変数にあるような"bcp_readrow"関数。 実行できるのは、アプリケーションからサーバーへのデータの送信だけです。  
  
## <a name="see-also"></a>参照  
 [一括コピー操作を実行する&#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
