---
title: サービス プロバイダーとコンポーネント |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB providers [ADO]
- ADO, OLE DB providers
- service providers [ADO]
ms.assetid: 1fd7a374-587b-4ca9-9204-3a4019b67a71
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 085e0caa494baf624468ccb4f4c4bd99020c588b
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38984314"
---
# <a name="service-providers-and-components"></a>サービス プロバイダーとコンポーネント
サービス プロバイダーは、データ ストアによってネイティブでサポートされていない拡張インターフェイスを実装するデータ プロバイダーの機能を拡張するコンポーネントです。  
  
 Universal Data Access の提供、*コンポーネント アーキテクチャ*劣るストア上、データベースの機能や「サービス」の個別のセットを実装するために、特殊化された個々 のコンポーネント。 したがって、独自の拡張機能の実装を提供するには、各データ ストアまたは強制的にデータベースの機能を内部的に実装する汎用アプリケーションではなくサービス コンポーネント、一般的な実装を提供できる任意のアプリケーション任意のデータ ストアにアクセスするときに使用します。 一部の機能が汎用的なコンポーネントをデータ ストアとネイティブ実装されているという事実は、アプリケーションに対して透過的です。  
  
 たとえば、カーソル エンジンをなど[for OLE DB、カーソル サービス](http://msdn.microsoft.com/57638feb-4ecd-4051-becb-8f828d21cf44)はスクロール可能なデータを生成するために、シーケンシャルな前方参照専用のデータ ストアからデータを使用できるサービス コンポーネントです。 ADO でよく使用されるその他のサービス プロバイダーには、 [Microsoft OLE DB Persistence Provider (サービス プロバイダーの ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) (ファイルにデータを保存します)、用、 [Microsoft Data Shaping Service for OLE DB (ADO サービス プロバイダー)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (の階層**レコード セット**)、および[Microsoft OLE DB リモート処理 Provider (サービス プロバイダーの ADO)](../../../ado/guide/appendixes/microsoft-ole-db-remoting-provider-ado-service-provider.md) (リモート コンピューター上のデータ プロバイダーの呼び出し) にします。  
  
 サービスおよびデータ プロバイダーの詳細については、次を参照してください。[付録 a: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)します。
