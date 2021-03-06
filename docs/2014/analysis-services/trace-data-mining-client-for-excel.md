---
title: トレース (Excel 用データ マイニング クライアント) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- tracer
- connections
ms.assetid: 4aea3e17-cd0f-48dd-8f22-b54a6c716426
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ee0268eb960aab09029774b6ad26ccccd3d352e6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37326522"
---
# <a name="trace-data-mining-client-for-excel"></a>トレース (Excel 用のデータ マイニング クライアント)
  ![トレース ボタン](media/misc-trace.gif "トレース ボタン")  
  
 **トレーサー**  ダイアログ ボックスでは、インスタンスに送信されるステートメントを監視できます。[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データ マイニングを使用しています。 インスタンスへの接続を作成した後[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、ログインしているクライアントとサーバー間のすべての対話、**トレーサー**構造を作成、マイニング モデルを追加し、ステートメントを含むウィンドウ予測だけでなく、サーバーから返す一部のメッセージ。  
  
 要求されるアクションに応じて、ステートメントは、データ マイニング拡張機能 (DMX) のデータ定義クエリやデータ操作クエリ、Analysis Services スクリプト言語 (ASSL) パケット、または Analysis Services ストアド プロシージャの呼び出しになります。 ただし、実際の数値で表される結果やデータ値は表示されません。  
  
 **トレース**は現在の接続のみとの内容を監視、**トレーサー**  ダイアログ ボックスは格納されません。  
  
## <a name="options"></a>および  
 [トレーサー] ペイン  
 Excel クライアントからサーバーに送信されたすべてのステートメントが一覧表示されます。  
  
 要求されるアクションに応じて、ステートメントは、DMX データ操作ステートメントやデータ定義ステートメント、Analysis Services ストアド プロシージャの呼び出し、または XML/A パケットになります。  
  
 **現在の接続**  
 クリックすると、現在の接続の定義が表示されます。 定義には、接続の名前、プロバイダー、データ ソース、カタログ、トランザクションのために接続が最後に使用された時間、および現在の状態 ([オープン]、[非アクティブ]) が含まれます。  
  
 **セッション モデルを使用**  
 データ マイニング モデルおよび構造を一時オブジェクトとしてサーバーに保存する場合は、このチェック ボックスをオンにします。 作成するモデルと構造は、現在のセッションが確立されている間のみ使用可能となります。  
  
 モデルまたは構造を Analysis Services サーバーに格納する場合は、このチェック ボックスをオフにします。  
  
 **注**一時オブジェクトを使用する機能は、Excel 用テーブル分析ツールを使用している場合にのみ使用します。 Visio データ マイニング テンプレートおよび Excel 用のデータ マイニング クライアントでは、構造とモデルをサーバーに格納する必要があります。  
  
## <a name="tracing-temporary-structures-and-models"></a>一時的な構造およびモデルのトレース  
 テーブル分析ツールを使用する場合、既定では一時的な構造およびモデルが作成されます。この場合、サーバーとクライアントの間のアクティビティは監視されますが、作成されたモデルまたは構造はサーバーに永続的には保存されません。  
  
 テーブル分析ツールのいずれかを使用する際に、作業内容を保持する場合、オプションの選択を解除できます**セッション モデルを使用して、** すると、モデルを永続的に、サーバーに保存します。 内のステートメントをコピーすることも、**トレーサー**ファイル ウィンドウ職場を後で再作成できるようにします。  
  
## <a name="understanding-sessions"></a>セッションについて  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスに接続すると、データ マイニング アドインによりセッションが開始されます。 それぞれのセッションは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンス上の既存のセッションを識別するセッション識別子を受け取ります。 ただし、セッション識別子は、セッションが有効であることを保証するわけではありません。 セッションは、タイムアウトした場合やセッションに関連付けられた接続が解除された場合に期限切れとなります。 セッションが期限切れとなり有効でなくなった場合、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、セッションを終了し、進行中のトランザクションをロールバックします。 無効になったセッション識別子でメッセージを送信した場合は、指定したセッションが見つからないことを示すエラーが発生して、そのメッセージは失敗します。  
  
 一部のデータ マイニング モデルはサーバー上に明示的に格納されますが、セッション マイニング モデルおよび構造は格納されず、セッション データ マイニング アクティビティのレコードも保存されません。 一時的なマイニング モデルおよび構造はセッションを終了するとすぐに削除されるため、必要な作業を保存するまでは Excel ブックを閉じないように注意してください。  
  
## <a name="changing-connections"></a>接続の変更  
 接続を変更した場合でも、以前の接続からトレースは削除されません。 ブックを閉じた場合のみ、セッションが消去されます。  
  
 Excel ブックで作業しながら接続を変更する場合、接続の変更には記録されず、**トレーサー**ウィンドウ。 明示的に名前と現在の接続の状態を表示するにはクリックして**現在の接続**します。  
  
## <a name="understanding-statements-in-the-tracer"></a>トレーサーのステートメントについて  
 DMX は、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のデータ マイニング モデルを作成および操作するための言語です。 DMX を使用して、新しいデータ マイニング モデルの構造の作成、これらのモデルのトレーニング、およびモデルの参照、管理、予測を行うことができます。 DMX は、データ定義言語 (DDL) ステートメント、データ操作言語 (DML) ステートメント、および関数と演算子で構成されています。  
  
 ここでは、DMX ステートメントとその構文を詳しく説明しません。 ただし、内の情報を使用することができます、**トレーサー** DMX ステートメントの動作に関する詳細情報を検索するウィンドウ。 また、Excel 用のデータ マイニング アドインを使用すると、複雑な DMX ステートメントを作成したり、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーを操作したりできるようになります。 詳細については、次を参照してください。[クエリ&#40;SQL Server データ マイニング アドイン&#41;](query-sql-server-data-mining-add-ins.md)します。  
  
> [!NOTE]  
>  多くの DMX ステートメントはパラメーター化されます。 単純型の場合、ステートメントの下にパラメーターの値が表示されます。 一方、複合型の場合は、パラメーターの型のみが表示されます。  
  
 SQL Server Analysis Services では、さらに XML for Analysis (XMLA) プロトコルを使用して、Excel 用のデータ マイニング クライアントおよび [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスを含む、クライアント アプリケーション間のすべての通信を処理します。  
  
 DMX 構文、および XMLA のコマンドや要素の詳細については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブックを参照してください。  
  
 サーバーに送信される一部のステートメントには、Analysis Services システム ストアド プロシージャを呼び出すクエリが含まれる場合があります。 詳細については、SQL Server オンライン ブックを参照してください。  
  
  
