---
title: IRow による 1 行のフェッチ |Microsoft ドキュメント
description: SQL Server 用の OLE DB Driver IRow インターフェイスを使用して 1 つの行のフェッチ
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- OLE DB Driver for SQL Server, fetching
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 21123e4d9918216f9b23ca2c7304bdcb1be2b0c7
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690045"
---
# <a name="fetching-a-single-row-with-irow"></a>IRow による 1 行のフェッチ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  **IRow**パフォーマンスが向上するのには SQL Server が簡略化のインターフェイスの OLE DB ドライバーに実装します。 **IRow**単一行オブジェクトの列に直接アクセスできます。 事前にわかっているコマンドの実行の結果が正確に 1 つの行を生成する場合**IRow**その行の列を取得します。 結果セットには、複数の行が含まれている場合**IRow**最初の行のみを公開します。  
  
 **IRow**実装では、行を移動することはできません。 行内の各列には 1 回だけアクセスされます。ただし、例外が 1 つあります。最初に列サイズを確認し、次にデータをフェッチする場合は、列に 2 回アクセスできます。  
  
> [!NOTE]  
>  **Irow::open**のみ DBGUID_STREAM 型と DBGUID_ 型のオブジェクトに開かれるをサポートしています。  
  
 使用して行オブジェクトを取得する**icommand::execute**メソッド、IID_IRow を渡す必要があります。 **IMultipleResults**インターフェイスは、複数の結果セットを処理するために使用する必要があります。 **IMultipleResults**サポート**IRow**と**IRowset**です。 **IRowset**一括操作のために使用します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [IRow::GetColumns の使用](../../oledb/ole-db-rowsets/using-irow-getcolumns.md)   
  
## <a name="see-also"></a>参照  
 [行セット](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
