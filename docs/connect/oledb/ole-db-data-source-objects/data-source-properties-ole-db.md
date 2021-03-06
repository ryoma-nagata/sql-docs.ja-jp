---
title: データ ソースのプロパティ (OLE DB) |Microsoft ドキュメント
description: データ ソースのプロパティ (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- OLE DB data source properties [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 1b426d49bd6a37167c16889f1e17c27ee72531c0
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665502"
---
# <a name="data-source-properties-ole-db"></a>データ ソースのプロパティ (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server では、次のようにデータ ソースのプロパティを実装します。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|DBPROP_CURRENTCATALOG|R/W: 読み取り/書き込み&lt;br&gt;&lt;/br&gt;既定値 : なし<br /><br /> 説明: DBPROP_CURRENTCATALOG の値に報告する、現在のデータベースの OLE DB ドライバーで SQL Server セッション。 使用して、現在のデータベースを設定するのと同じ効果を持つプロパティ値を設定、[!INCLUDE[tsql](../../../includes/tsql-md.md)]使用*データベース*ステートメントです。<br /><br /> 以降で[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]を呼び出す場合は、 [sp_defaultdb](../../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md)データベース名を指定し、小文字で、データベースは、混在のケースの名前を持つ最初に作成された場合でも DBPROP_CURRENTCATALOG は名前を返しますで小文字に変換します。 以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、大文字と小文字が混在する名前が DBPROP_CURRENTCATALOG によって返されます。|  
|DBPROP_MULTIPLECONNECTIONS|R/W : 読み取り/書き込み<br></br>既定値 : VARIANT_FALSE<br /><br /> 説明 : 行セットを生成しないコマンドまたはサーバー カーソルではない行セットを生成するコマンドが接続で実行されているときに、ユーザーが別のコマンドを実行すると、DBPROP_MULTIPLECONNECTIONS が VARIANT_TRUE に設定されている場合は、新しいコマンドを実行するために新しい接続が作成されます。<br /><br /> DBPROP_MULTIPLECONNECTION が VARIANT_FALSE の場合、またはトランザクションの接続でアクティブな場合、SQL Server の OLE DB Driver は別の接続を作成できません。 SQL Server の OLE DB Driver は、DBPROP_MULTIPLECONNECTIONS が VARIANT_FALSE に、E_FAIL が返された場合は、アクティブなトランザクションがある場合、DB_E_OBJECTOPEN を返します。 トランザクションとロックは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって接続ごとに管理されます。 2 番目の接続を作成する場合は、個別の接続のコマンドではロックは共有されません。 あるコマンドで別のコマンドがブロックされないようにするには、他のコマンドによって要求される行にロックを設定します。 このことは、複数のセッションを作成する場合にも適用されます。<br /><br /> 各セッションには個別の接続があります。|  
  
 プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERDATASOURCE では、SQL Server の OLE DB Driver は、次の追加のデータ ソースのプロパティを定義します。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|SSPROP_ENABLEFASTLOAD|R/W : 読み取り/書き込み<br></br>既定値 : VARIANT_FALSE<br /><br /> 説明 : メモリからの一括コピーを有効にするには、SSPROP_ENABLEFASTLOAD プロパティを VARIANT_TRUE に設定する必要があります。 このプロパティをデータ ソースに設定すると、新しく作成されたセッションでは消費者のアクセスを[IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)インターフェイスです。<br /><br /> プロパティが VARIANT_TRUE に設定されている場合**IRowsetFastLoad**インターフェイスを使用してを通じて**iopenrowset::openrowset**要求することによって、 **IID_IRowsetFastLoad**インターフェイスかを設定**SSPROP_IRowsetFastLoad**を VARIANT_TRUE に設定します。|  
|SSPROP_ENABLEBULKCOPY|R/W : 読み取り/書き込み<br></br>既定値 : VARIANT_FALSE<br /><br /> 説明 : ファイルからの一括コピーを有効にするには、SSPROP_ENABLEBULKCOPY プロパティを VARIANT_TRUE に設定する必要があります。 データ ソースにこのプロパティを設定すると、コンシューマーから IBCPSession インターフェイスにセッションと同じレベルでアクセスできるようになります。<br /><br /> また、SSPROP_IRowsetFastLoad を VARIANT_TRUE に設定する必要があります。|  
  
## <a name="see-also"></a>参照  
 [データ ソース オブジェクト&#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
