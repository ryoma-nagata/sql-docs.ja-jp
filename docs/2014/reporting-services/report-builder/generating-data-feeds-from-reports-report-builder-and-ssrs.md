---
title: 複数のレポートからのデータ フィードの生成 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4e00789f-6967-42e5-b2b4-03181fdb1e2c
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 9594eca6b955081be5689862d96d1c9d09a6a664
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37202662"
---
# <a name="generating-data-feeds-from-reports-report-builder-and-ssrs"></a>複数のレポートからのデータ フィードの生成 (レポート ビルダーおよび SSRS)
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Atom 表示拡張機能は、レポートから利用できるデータ フィードを一覧表示する Atom サービス ドキュメントを生成およびレポートの領域、データ データからをフィードします。 この拡張機能を使用すると、レポートから生成されたデータ フィードを使用できるアプリケーションで読み取りおよび交換が可能な、Atom に準拠したデータ フィードを生成できます。 たとえば、Atom 表示拡張機能を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クライアントで使用できるデータ フィードを生成できます。  
  
 Atom サービス ドキュメントには、レポート内の各データ領域について 1 つ以上のデータ フィードが一覧表示されます。 データ領域と、データ領域が表示されるデータの種類に応じて[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]データ領域から複数のデータ フィードを生成する可能性があります。 たとえば、マトリックスまたはグラフでは、複数のデータ フィードを提供できます。 Atom 表示拡張機能によって Atom サービス ドキュメントが作成されると、各データ フィードに対して一意な識別子が作成されます。URL 内でこの識別子を使用することで、データ フィードの内容にアクセスできます。  
  
 Atom 表示拡張機能でデータ フィード用のデータを生成する方法は、コンマ区切り値 (CSV) 表示拡張機能でデータから CSV ファイルを提供する方法に似ています。 CSV ファイルと同様に、データ フィードは、レポート データのフラット化された表現です。 たとえば、グループ内の売上を合計する行グループを含むテーブルでは、すべてのデータ行で合計が繰り返され、合計のみを含む独立した行がありません。  
  
 Atom サービス ドキュメントおよびデータ フィードは、レポート マネージャー、レポート サーバー、または [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] と統合された SharePoint サイトを使用して生成できます。  
  
 Atom は、一式の関連標準に適用されます。 Atom サービス ドキュメントは RFC 5023 Atom パブリッシング プロトコル仕様に準拠し、データ フィードは RFC 4287 Atom 配信形式プロトコル仕様に準拠します。  
  
 以降のセクションでは、Atom 表示拡張機能の使用法に関する追加情報を提供します。  
  
 [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="ReportDataAsDataFeeds"></a> データ フィードとしてのレポート  
 運用レポートをデータ フィードとしてエクスポートすることも、データ フィードの形式でアプリケーションにデータを提供することを第 1 の目的とするレポートを作成することもできます。 データ フィードとしてのレポートは、クライアント データ プロバイダーを介してデータにアクセスするのが困難な場合や、データ ソースの複雑さを隠してデータをより簡単に使用できるようにする場合に、データをアプリケーションに提供するための方法の 1 つです。 レポート データをデータ フィードとして使用するもう 1 つのメリットは、レポート マネージャー、セキュリティ、スケジュール設定、レポート スナップショットなどの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 機能を使用して、データ フィードを提供するレポートを管理できることです。  
  
 Atom 表示拡張機能を有効に利用するためには、レポートがどのようにデータ フィードに表示されるかを理解する必要があります。 既存のレポートを使用している場合は、レポートからどのようなデータ フィードが生成されるかを予測できることが必要です。データ フィードとして使用する専用のレポートを作成している場合は、データ フィードの有用性を最大限に高めるために、データを組み込んでレポート レイアウトを微調整できることが重要です。  
  
 詳細については、「[1 つのレポートからのデータ フィードの生成 (レポート ビルダーおよび SSRS)](generate-data-feeds-from-a-report-report-builder-and-ssrs.md)」を参照してください。  
  

  
##  <a name="AtomServiceDocument"></a> Atom サービス ドキュメント (.atomsvc ファイル)  
 Atom サービス ドキュメントは、1 つまたは複数のデータ フィードへの接続を指定します。 接続は、少なくとも、フィードを生成するデータ サービスへの単純な URL です。  
  
 Atom 表示拡張機能を使用してレポート データを表示すると、Atom サービス ドキュメントによってレポートで利用できるデータ フィードが一覧表示されます。 このドキュメントには、レポート内の各データ領域について 1 つ以上のデータ フィードが一覧表示されます。 テーブルおよびゲージから生成されるデータ フィードはそれぞれ 1 つのみです。これに対し、マトリックス、リスト、およびグラフの場合、表示するデータによっては複数のデータ フィードが生成される場合があります。  
  
 次の図に、2 つのテーブルと 1 つのグラフを使用するレポートを示します。  
  
 ![RS_Atom_TableAndChartDataFeeds](../media/rs-atom-tableandchartdatafeeds.gif "RS_Atom_TableAndChartDataFeeds")  
  
 このレポートから生成される Atom サービス ドキュメントには、各テーブルから 1 つずつ、グラフから 1 つの、合計 3 つのデータ フィードが含まれます。  
  
 マトリックス データ領域には、マトリックスの構造に応じて複数のデータ フィードが含まれる場合があります。 次の図に、2 つのデータ フィードを生成するマトリックスが使用されているレポートを示します。  
  
 ![RS_Atom_PeerDynamicColumns](../media/rs-atom-peerdynamiccolumns.gif "RS_Atom_PeerDynamicColumns")  
  
 このレポートから生成される Atom サービス ドキュメントには、動的なピア列 Territory と Year に対応する 2 つのデータ フィードが含まれます。 次の図に、各データ フィードの内容を示します。  
  
 ![RS_Atom_PeerDynamicDataFeeds](../media/rs-atom-peerdynamicdatafeeds.gif "RS_Atom_PeerDynamicDataFeeds")  
  

  
##  <a name="DataFeeds"></a> データ フィード  
 データ フィードは、時間が経過しても変化しない一貫した表形式と、レポートを実行するたびに変化する可能性のある可変データから成る、XML ファイルです。 によって生成されたデータ フィード[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]は ADO.NET Data Services によって生成されたものと同じ形式です。  
  
 データ フィードには、ヘッダー セクションとデータ セクションの 2 つのセクションが含まれます。 Atom 仕様には、各セクションの要素が定義されています。 ヘッダーには、データ フィードで使用する文字エンコード スキーマなどの情報が含まれています。  
  
### <a name="header-section"></a>ヘッダー セクション  
 次の XML コードは、データ フィードのヘッダー セクションを示しています。  
  
 `<?xml version="1.0" encoding="utf-8" standalone="yes"?><feed xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservices" xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<title type="text"></title>`  
  
 `<id>uuid:1795992c-a6f3-40ec-9243-fbfd0b1a5be3;id=166321</id>`  
  
 `<updated>2009-05-08T23:09:58Z</updated>`  
  
### <a name="data-section"></a>データ セクション  
 データ フィードのデータ セクションには、Atom 表示拡張機能によって生成されたフラット化された行セット内の行ごとに 1 つの <`entry`> 要素が含まれています。  
  
 次の図に、グループと合計を使用するレポートを示します。  
  
 ![RS_Atom_ProductSalesSummaryCircledValues](../media/rs-atom-productsalessummarycircledvalues.gif "RS_Atom_ProductSalesSummaryCircledValues")  
  
 次の XML に示す、<`entry`> データ フィード内のレポートからの要素。 なお、<`entry`> 要素には、売上および注文のすべてのグループの合計と売上および注文の合計が含まれています。 <`entry`> 要素には、レポート上のすべての値が含まれます。  
  
 `<entry><id>uuid:1795992c-a6f3-40ec-9243-fbfd0b1a5be3;id=166322</id><title type="text"></title><updated>2009-05-08T23:09:58Z</updated><author /><content type="application/xml"><m:properties>`  
  
 `<d:ProductCategory_Value>Accessories</d:ProductCategory_Value>`  
  
 `<d:OrderYear_Value m:type="Edm.Int32">2001</d:OrderYear_Value>`  
  
 `<d:SumLineTotal_Value m:type="Edm.Decimal">20235.364608</d:SumLineTotal_Value>`  
  
 `<d:SumOrderQty_Value m:type="Edm.Int32">1003</d:SumOrderQty_Value>`  
  
 `<d:SumLineTotal_Total_2_1 m:type="Edm.Decimal">1272072.883926</d:SumLineTotal_Total_2_1>`  
  
 `<d:SumOrderQty_Total_2_1 m:type="Edm.Double">61932</d:SumOrderQty_Total_2_1>`  
  
 `<d:SumLineTotal_Total_2_2 m:type="Edm.Decimal">109846381.399888</d:SumLineTotal_Total_2_2>`  
  
 `<d:SumOrderQty_Total_2_2 m:type="Edm.Double">274914</d:SumOrderQty_Total_2_2></m:properties></content>`  
  
 `</entry>`  
  
### <a name="working-with-data-feeds"></a>データ フィードの操作  
 レポートによって生成されるすべてのデータ フィードには、データ フィードを生成するデータ領域の親のスコープ内のレポート アイテムが含まれます。 と統合された SharePoint サイトを使用して生成できます。 複数のテーブルと 1 つのグラフが含まれているレポートを想像してください。 レポート本文のテキスト ボックスは、各データ領域の説明テキストを提供します。 レポートによって生成されるすべてのデータ フィードのすべてのエントリには、テキスト ボックスの値が含まれます。 たとえば、テキストが "販売地域別の月次売上の平均を示すグラフ" の場合、3 つのすべてのデータ フィードの各行にこのテキストが含まれます。  
  
 入れ子になったデータ領域のような階層データ リレーションシップがレポート レイアウトに含まれている場合、これらのリレーションシップは、レポート データのフラット化された行セットに含まれます。  
  
 一般に、入れ子になったデータ領域のデータ行は幅が広くなります。入れ子になったテーブルおよびマトリックスにグループや合計が含まれる場合は特にそうです。 期待どおりのデータが生成されるかどうかを確認するには、レポートをデータ フィードにエクスポートした後でデータ フィードを表示すると便利です。  
  
 Atom 表示拡張機能によって Atom サービス ドキュメントが作成されると、データ フィードに対して一意な識別子が作成されます。URL 内でこの識別子を使用することで、データ フィードの内容を確認できます。 上に示した、サンプルの Atom サービス ドキュメントには、URL が含まれています。 http://ServerName/ReportServer?%2fProduct+Sales+Summary&rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=xAx0x1"。 この URL は、レポート (Product Sales Summary)、Atom 表示形式 (ATOM)、およびデータ フィードの名前 (xAx0x1) を識別します。  
  
 レポート アイテムの名前には、直感的でなく覚えにくい、レポート アイテムのレポート定義言語 (RDL) 要素の名前が既定で使用されます。 たとえば、レポートに配置された最初のマトリックスの既定の名前は Tablix 1 となります。 データ フィードでは、これらの名前が使用されます。  
  
 データ領域の DataElementName プロパティを使用してわかりやすい名前を付けることで、データ フィードの操作を容易にすることができます。 DataElementName の値を指定する場合、データ フィードのサブ要素 <`d`> は使用が既定のデータ領域名の代わりです。 たとえば、データ領域の既定の名前が Tablix1、DataElementName に SalesByTerritoryYear を設定し、<`d`> SalesByTerritoryYear を使用して、データ フィードです。 上で説明したマトリックス レポートのようにデータ領域に 2 つのデータ フィードがある場合、データ フィードで使用される名前は、SalesByTerritoryYear _Territory と SalesByTerritoryYear _Year となります。  
  
 レポート上に表示されたデータとデータ フィード内のデータを比較した場合、いくつかの相違があります。 通常、レポートに表示される数値データや日時データは書式設定されていますが、データ フィードには書式設定されていないデータが含まれます。  
  
 データ フィードは、拡張子が .atom のファイル名で保存されます。 テキスト エディターまたは XML エディター (たとえば、メモ帳や XML Editor) を使用して、ファイルの構造および内容を確認できます。  
  

  
##  <a name="FlatteningReportData"></a> レポート データのフラット化  
 Atom レンダラーは、XML 形式のフラット化された行セットとしてレポート データを提供します。 データ テーブルをフラット化する場合のルールは、いくつかの例外を除き、CSV レンダラーに適用されるルールと同じです。  
  
-   スコープ内のアイテムは、詳細レベルにフラット化されます。 CSV レンダラーとは異なり、最上位レベルにあるテキスト ボックスは、データ フィードに書き込まれるすべてのエントリに含められます。  
  
-   レポート パラメーター値は、出力の行ごとに表示されます。  
  
 階層データとグループ化データは、Atom に準拠した形式で表示するためにフラット化する必要があります。 表示拡張機能では、レポートをフラット化して、データ領域内で入れ子になっているグループを表すツリー構造にします。 レポートをフラット化する手順は次のとおりです。  
  
-   行階層がフラット化されてから列階層がフラット化されます。  
  
-   行階層のメンバーがデータ フィードに表示された後、列階層のメンバーが表示されます。  
  
-   列が並べ替えられます。本文中のテキスト ボックスが左から右、上から下に並べ替えられた後、データ領域が左から右、上から下に並べ替えられます。  
  
-   データ領域内の列が、コーナーのメンバー、行階層メンバー、列階層メンバー、セルの順に並べ替えられます。  
  
-   ピア データ領域は、一般的なデータ領域または動的な先祖を共有する、データ領域または動的グループです。 ピア データがフラットなツリーの分岐で識別されます。  
  
 詳細については、「 [テーブル、マトリックス、および一覧 (レポート ビルダーおよび SSRS)](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)」を参照してください。  
  

  
##  <a name="AtomRendering"></a> Atom 表示ルール  
 Atom 表示拡張機能は、データ フィードを表示するときに次の情報を無視します。  
  
-   書式設定およびレイアウト  
  
-   ページ ヘッダー  
  
-   ページ フッター  
  
-   カスタム レポート アイテム  
  
-   四角形  
  
-   線  
  
-   画像  
  
-   自動集計  
  
 その他のレポート アイテムは、まず先頭から末尾に、そして左から右に向かって並べ替えられます。 その後、各アイテムが列に生成されます。 レポートに一覧やテーブルなどの入れ子になったデータ アイテムがある場合は、親アイテムが各行に繰り返し使用されます。  
  
 次の表では、表示した際のレポート アイテムの外観について説明します。  
  
|アイテム|表示動作|  
|----------|------------------------|  
|テーブル|テーブルを展開して表示します。最も詳細なレベルでの各行と列に対応した、行と列が作成されます。 集計の行と列には、列見出しまたは行見出しは付けられません。 詳細レポートはサポートされません。|  
|マトリックス|マトリックスを展開して表示します。最も詳細なレベルでの各行と列に対応した、行と列が作成されます。 集計の行と列には、列見出しまたは行見出しは付けられません。|  
|一覧|一覧の詳細行またはインスタンスそれぞれに対応するレコードが表示されます。|  
|サブレポート|親アイテムは、コンテンツのインスタンスごとに繰り返し表示されます。|  
|グラフ|それぞれのグラフ値にすべてのグラフ ラベルを付けてレコードを表示します。 階層内の系列およびカテゴリのラベルは、フラット化され、グラフ値の行内に含まれています。|  
|データ バー|グラフのように表示されます。 通常、データ バーには階層またはラベルは含まれません。|  
|スパークライン|グラフのように表示されます。 通常、スパークラインには階層またはラベルは含まれません。|  
|ゲージ|線形スケールの最小値/最大値、範囲の開始値/終了値、およびポインターの値を含む単一のレコードとして表示されます。|  
|インジケーター|アクティブな状態名、使用可能な状態、およびデータ値を持つ単一のレコードとして表示されます。|  
|マップ|各マップ データ領域にデータ フィードを生成します。 複数のマップ レイヤーが同じデータ領域を使用している場合、データ フィードにはすべてのマップ レイヤーが含まれます。 データ フィードには、マップ レイヤーのマップ メンバーごとにラベルと値を持つレコードが含まれます。|  
  

  
##  <a name="DeviceInfo"></a> デバイス情報設定  
 使用するエンコード スキーマなど、このレンダラーのいくつかの既定の設定は変更することができます。 詳細については、「 [ATOM Device Information Settings](../atom-device-information-settings.md)」を参照してください。  
  

  
## <a name="see-also"></a>参照  
 [CSV ファイルにエクスポートする&#40;レポート ビルダーおよび SSRS&#41;](exporting-to-a-csv-file-report-builder-and-ssrs.md)   
 [レポートのエクスポート&#40;レポート ビルダーおよび SSRS&#41;](export-reports-report-builder-and-ssrs.md)  
  
  
