---
title: sys.dm_exec_xml_handles (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_xml_handles
- dm_exec_xml_handles_TSQL
- sys.dm_exec_xml_handles_TSQL
- sys.dm_exec_xml_handles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_xml_handles dynamic management function
ms.assetid: a873ce0f-6955-417a-96a1-b2ef11a83633
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 66702418faae18f1c4582a28353e2f5ae7c156bc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38046110"
---
# <a name="sysdmexecxmlhandles-transact-sql"></a>sys.dm_exec_xml_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  によって開かれたアクティブ ハンドルに関する情報を返します**sp_xml_preparedocument**します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dm_exec_xml_handles (session_id | 0 )  
```  
  
## <a name="arguments"></a>引数  
 *session_id* | 0,  
 セッションの ID を指定します。 場合*session_id*を指定すると、この関数は、指定したセッションで XML ハンドルに関する情報を返します。  
  
 0 を指定した場合、この関数ではすべてのセッションのすべての XML ハンドルに関する情報が返されます。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|この XML ドキュメント ハンドルを保持しているセッションのセッション ID。|  
|**document_id**|**int**|によって返される XML ドキュメント ハンドル ID **sp_xml_preparedocument**します。|  
|**namespace_document_id**|**int**|3 番目のパラメーターとして渡された名前空間が関連付けられているドキュメントに使用される内部ハンドル ID **sp_xml_preparedocument**します。 名前空間ドキュメントがない場合は NULL になります。|  
|**sql_handle**|**varbinary(64)**|ハンドルが定義されている SQL コードのテキストへのハンドル。|  
|**statement_start_offset**|**int**|現在実行中に文字数のバッチまたはストアド プロシージャを**sp_xml_preparedocument**呼び出しが発生します。 組み合わせて使用することができます、 **sql_handle**、 **statement_end_offset**、および**sys.dm_exec_sql_text**動的管理関数を取得する、現在要求のステートメントを実行します。|  
|**statement_end_offset**|**int**|現在実行中に文字数のバッチまたはストアド プロシージャを**sp_xml_preparedocument**呼び出しが発生します。 組み合わせて使用することができます、 **sql_handle**、 **statement_start_offset**、および**sys.dm_exec_sql_text**動的管理関数を取得する、現在要求のステートメントを実行します。|  
|**creation_time**|**datetime**|タイムスタンプと**sp_xml_preparedocument**が呼び出されました。|  
|**original_document_size_bytes**|**bigint**|未解析の XML ドキュメントのサイズ (バイト単位)。|  
|**original_namespace_document_size_bytes**|**bigint**|未解析の XML 名前空間ドキュメントのサイズ (バイト単位)。 名前空間ドキュメントがない場合は NULL になります。|  
|**num_openxml_calls**|**bigint**|このドキュメント ハンドルを使用する OPENXML 呼び出しの数。|  
|**row_count**|**bigint**|このドキュメント ハンドルに対する前のすべての OPENXML 呼び出しによって返される行数。|  
|**dormant_duration_ms**|**bigint**|最後に OPENXML が呼び出されてから経過した時間 (ミリ秒)。 OPENXML が呼び出されていない場合は、以降のミリ秒数を返します、 **sp_xml_preparedocumen**t 呼び出し。|  
  
## <a name="remarks"></a>コメント  
 有効期間**sql_handle**への呼び出しを実行する SQL テキストを取得するために使用**sp_xml_preparedocument**クエリを実行するために使用するキャッシュされたプランよりも長くなります。 クエリ テキストがキャッシュ内で使用できない場合は、関数の結果に示された情報を使用してデータを取得することはできません。 この状況は、大きなバッチを多数実行している場合に発生する可能性があります。  
  
## <a name="permissions"></a>アクセス許可  
 呼び出し元が所有していないすべてのセッションまたはセッション ID を参照するには、サーバーに対する VIEW SERVER STATE 権限が必要です。 呼び出し元は常に自分の現在のセッション ID のデータを参照できます。      
  
## <a name="examples"></a>使用例  
 次の例では、アクティブ ハンドルをすべて選択します。  
  
```  
SELECT * FROM sys.dm_exec_xml_handles(0);  
```  
  
## <a name="see-also"></a>参照  
 <br>[動的管理ビューおよび関数 (TRANSACT-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
 <br>[実行関連の動的管理ビューおよび関数 (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)
 <br>[sp_xml_preparedocument (TRANSACT-SQL)](../system-stored-procedures/sp-xml-preparedocument-transact-sql.md)
 <br>[sp_xml_removedocument (TRANSACT-SQL)](../system-stored-procedures/sp-xml-removedocument-transact-sql.md)


 
  
  
