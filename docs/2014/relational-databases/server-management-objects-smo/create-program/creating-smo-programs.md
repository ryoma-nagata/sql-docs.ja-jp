---
title: SMO プログラムの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Visual Basic [SMO]
- Visual C# [SMO]
- programming [SMO]
- SQL Server Management Objects, programming
- SMO [SQL Server], programming
ms.assetid: 7d2f0bcf-f1ae-45b8-bc3f-7aea4fae7e45
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a92ff5f60136d910632ead2aefbcc5023a387a3b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158033"
---
# <a name="creating-smo-programs"></a>SMO プログラムの作成
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) オブジェクトの一般的なプログラミングには、メソッドの実行、プロパティの設定、およびコレクションの操作など、すべてのオブジェクトが共有する共通エリアが含まれています。  
  
|トピック|説明|  
|-----------|-----------------|  
|[SQL Server のインスタンスへの接続](connecting-to-an-instance-of-sql-server.md)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスへの接続を確立する最も基本的な SMO プログラム。 Windows 認証および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を示します。 また、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のローカル インスタンスおよびリモート インスタンスへの接続を示すサンプルも含まれています。|  
|[SQL Server のインスタンスからの切断](disconnecting-from-an-instance-of-sql-server.md)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスから切断する方法を示すプログラム。|  
|[メソッドの呼び出し](calling-methods.md)|このセクションでは、メソッドを呼び出すための一般的な方法について説明します。 パラメーターの使用、および <xref:System.Data.DataTable> オブジェクトに返されるデータのテーブルを処理する方法について説明します。 また、オブジェクト コンストラクターを呼び出す方法、および `Clone` メソッドを呼び出す方法の例も含まれています。|  
|[プロパティの設定](setting-properties-smo.md)|このセクションでは、プロパティのさまざまな型を設定する方法について説明します。 オブジェクト プロパティを設定および取得する方法について示します。 また、オブジェクトの作成時にオブジェクト プロパティを設定する例、およびオブジェクトのすべてのプロパティを反復処理する方法も含まれています。|  
|[コレクションの使用](using-collections.md)|オブジェクト コレクションと共に使用されるテクニックについて説明するさまざまなプログラム。 コレクションを使用するオブジェクトを参照する方法について説明します。 また、コレクションのメンバーを反復処理する方法の例も含まれています。|  
|[SMO イベントの処理](handling-smo-events.md)|このセクションでは、SMO でイベントの設定および処理を行う方法について説明します。 イベント ハンドラーを設定する方法、およびイベント サブスクリプションを設定する方法の例が含まれています。|  
|[SMO 例外の処理](handling-smo-exceptions.md)|このセクションでは、SMO で例外をトラップする方法について説明します。 例外をキャッチする方法、および内部例外を表示する方法の例が含まれています。|  
|[データ型の処理](working-with-data-types.md)|このセクションでは、さまざまな [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型を操作する方法について説明します。 オブジェクト コンストラクターでの指定でデータ型を構築する方法について説明します。 また、既定のコンストラクターを使用してデータ型を作成する方法の例も含まれています。|  
|[トランザクションの使用](using-transactions.md)|このセクションでは、SMO プログラムでトランザクション処理を実装する方法について説明します。 SMO プログラムでトランザクションを使用する方法の例が含まれています。|  
|[キャプチャ モードの使用](using-capture-mode.md)|このセクションでは、SMO プログラムの出力を記録する方法について説明します。 この例では、後で実行するために [!INCLUDE[tsql](../../../includes/tsql-md.md)] のインスタンスに送信された [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ステートメントとして、SMO プログラムが記録されます。|  
  
  
