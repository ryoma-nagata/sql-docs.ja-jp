---
title: CLR データベース オブジェクトからの XML シリアル化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8b59c013a9a21aaa50465acd5a565eda5c1e0653
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279828"
---
# <a name="xml-serialization-from-clr-database-objects"></a>CLR データベース オブジェクトからの XML シリアル化
  XML シリアル化は、次の 2 つのシナリオで必要になります。  
  
-   CLR (共通言語ランタイム) オブジェクトから Web サービスを呼び出す場合。  
  
-   UDT (ユーザー定義型) を XML に変換する場合。  
  
 `XmlSerializer` クラスを呼び出して XML シリアル化を実行すると、通常、新たにシリアル化アセンブリが生成され、シリアル化の基になるアセンブリを含むプロジェクトにオーバーロードされます。 ただし、セキュリティ上の理由から、CLR ではこのオーバーロードが無効になります。 そのため、web サービスを呼び出したり、UDT から内の XML への変換を実行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と呼ばれるツールを使用して手動でアセンブリを作成する必要があります**Sgen.exe**のために必要なを生成する .NET Framework に付属シリアル化アセンブリ。 `XmlSerializer` を呼び出す場合は、次の手順に従って、シリアル化アセンブリを手動で作成する必要があります。  
  
1.  実行、 **Sgen.exe**はソース アセンブリ用の XML シリアライザーを格納しているアセンブリを作成する .NET Framework SDK に付属するツール。  
  
2.  `CREATE ASSEMBLY` ステートメントを使用して、生成したアセンブリを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に登録します。  
  
 エラーに関する情報が表示されるときに XML シリアル化を実行する次のマイクロソフトのサポート資料を参照: [「動的に生成されたシリアル化アセンブリを読み込むことができません」](http://support.microsoft.com/kb/913668)します。  
  
 XMLSerializer でサポートされないデータ型については、.NET Framework のドキュメントで、.NET Framework の XML スキーマ バインディング サポートに関する情報を参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR データベース オブジェクトからのデータ アクセス](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)   
 [CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  
