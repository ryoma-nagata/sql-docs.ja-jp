---
title: 検証を伴わない暗号化を使用して |Microsoft ドキュメント
description: 検証を伴わない暗号化の使用
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], encryption
- cryptography [OLE DB Driver for SQL Server]
- MSOLEDBSQL, encryption
- encryption [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, encryption
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 96e33a0dfdb301c9088d37d6b33460b8c453c1b2
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2018
ms.locfileid: "35612337"
---
# <a name="using-encryption-without-validation"></a>検証を伴わない暗号化の使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、常に、ログインに関連するネットワーク パケットを暗号化します。 サーバーの起動時に証明書がサーバーに提供されないと、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はログイン パケットの暗号化に使用される自己署名入りの証明書を生成します。  

自己署名証明書では、セキュリティが保証されません。 暗号化ハンドシェイクは、NT LAN Manager (NTLM) に基づいています。 SQL サーバー上のセキュリティで保護された接続は検証可能な証明書をプロビジョニングすることを強くお勧めします。 証明書の検証でのみセキュリティで保護されたトランスポート セキュリティ層 (TLS) を作成できます。

アプリケーションでは、接続文字列キーワードまたは接続プロパティを使用して、すべてのネットワーク トラフィックの暗号化を要求することもできます。 キーワードは、"Encrypt"の OLE DB プロバイダー文字列を使用するときに**idbinitialize::initialize**、または"Use Encryption for Data"ADO および OLE DB 初期化文字列を使用する場合の**IDataInitialize**. によって構成もこの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Configuration Manager を使用して、 **Force Protocol Encryption**オプション、およびで暗号化された接続を要求するクライアントの構成します。 既定では、接続のネットワーク トラフィックをすべて暗号化するには、証明書をサーバーに提供する必要があります。 サーバー上の証明書を信頼するようにクライアントを設定するが、中間の攻撃に対する脆弱性のようになります。 サーバーで検証可能な証明書を展開する場合は、FALSE には、証明書の信頼に関するクライアント設定を変更することを確認します。

接続文字列キーワードについては、次を参照してください。 [OLE DB Driver for SQL Server での接続文字列キーワードの使用](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md )です。  
  
 サーバーで、証明書がプロビジョニングされていないときに使用される暗号化を有効にする[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]構成マネージャーを使用して、両方を設定できます、 **Force Protocol Encryption**と**Trust Server Certificate**オプション。 この場合、検証可能な証明書がサーバーに提供されなかった場合は、暗号化には検証を伴わない自己署名入りのサーバー証明書を使用します。  
  
 アプリケーションでは、暗号化が行われることを保証するために "TrustServerCertificate" キーワードまたはそれに関連する接続属性も使用できます。 アプリケーションの設定によって、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クライアント構成マネージャーで設定されるセキュリティのレベルを緩和することはできません。ただし、厳密にすることはできます。 たとえば場合、 **Force Protocol Encryption**が設定されていないアプリケーションはクライアントは、暗号化自体を要求する可能性があります。 サーバー証明書が提供されなかった場合でも暗号化を保証するには、アプリケーションから暗号化と "TrustServerCertificate" を要求できます。 ただし、クライアントの構成で "TrustServerCertificate" が有効になっていない場合は、サーバー証明書を提供する必要があります。 次の表ですべてのケースを説明します。  
  
|[Force Protocol Encryption] クライアント設定|[Trust Server Certificate] クライアント設定|接続文字列/接続属性 Encrypt/Use Encryption for Data|接続文字列/接続属性 Trust Server Certificate|結果|  
|----------------------------------------------|---------------------------------------------|------------------------------------------------------------------------------|----------------------------------------------------------------------|------------|  
|いいえ|なし|いいえ (既定値)|無視|暗号化は行われません。|  
|いいえ|なし|はい|いいえ (既定値)|暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。|  
|いいえ|なし|はい|はい|暗号化は常に行われますが、自己署名入りのサーバー証明書を使用することがあります。|  
|はい|いいえ|無視|無視|暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。|  
|はい|はい|いいえ (既定値)|無視|暗号化は常に行われますが、自己署名入りのサーバー証明書を使用することがあります。|  
|はい|はい|はい|いいえ (既定値)|暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。|  
|はい|はい|はい|はい|暗号化は常に発生するが自己署名サーバー証明書を使用する場合があります。|  
||||||

> [!CAUTION]
> 上記の表は、異なる構成で、システムの動作にのみ、ガイドを提供します。 セキュリティで保護された接続は、クライアントとサーバーの両方が暗号化を要求することを確認します。 検証可能な証明書、およびをサーバーにあることを確認してください、 **TrustServerCertificate**クライアントの設定が FALSE に設定します。

## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server 
 SQL Server の OLE DB Driver は、DBPROPSET_SQLSERVERDBINIT プロパティ セットに実装される SSPROP_INIT_TRUST_SERVER_CERTIFICATE データ ソース初期化プロパティの追加によって検証を伴わない暗号化をサポートします。 さらに、新しい接続文字列キーワード、"TrustServerCertificate"のように追加されました。 "TrustServerCertificate" は、yes または no を値として受け取ります。既定値は no です。 サービス コンポーネントを使用しているときは、"TrustServerCertificate" は true または false を値として受け取ります。既定値は false です。  
  
 DBPROPSET_SQLSERVERDBINIT プロパティ セットへの拡張機能の詳細については、次を参照してください。[初期化プロパティと承認プロパティ](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)です。  

  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server の機能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
