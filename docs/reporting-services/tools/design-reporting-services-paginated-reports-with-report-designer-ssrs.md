---
title: レポート デザイナーを使用してレポートをデザインする (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: tools
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], report creation
ms.assetid: 3a26dccc-6ad6-48f5-a882-f96c6c0dd405
caps.latest.revision: 77
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 09311458bc7815a7a63d58ad19c8d8b0a3845da4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="design-reporting-services-paginated-reports-with-report-designer-ssrs"></a>レポート デザイナーを使用して Reporting Services の改ページ調整されたレポートをデザインする (SSRS)

レポート デザイナーを使用すると、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のフル機能付きのページ分割レポートおよびレポート ソリューションを作成できます。 レポート デザイナーには、データ ソース、データセット、およびクエリ、データ領域とフィールドのレポート レイアウトの配置、連携するパラメーターとレポートのセットなどの対話機能を定義できるグラフィカル インターフェイスが用意されています。  

レポート デザイナーは、Microsoft Visual Studio のビジネス インテリジェンス ソリューション作成環境である  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の機能です。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、SQL Server には含まれていません。 [SQL Server Data Tools](http://go.microsoft.com/fwlink/?LinkID=616714)をダウンロードします。 
  
## <a name="benefits-of-report-projects"></a>レポート プロジェクトの利点  
レポート プロジェクトは、レポート定義およびリソース用のコンテナーの役割を果たします。 プロジェクトを使用する目的  
  
-   レポートおよび関連アイテムを 1 つのコンテナーにまとめます。  
  
-   レポートおよび関連アイテムがローカルに格納されているレポート ソリューションをテストします。  
  
-   関連アイテムをまとめて配置します。 プロジェクトのプロパティと構成管理を使用して、複数の環境に配置します。  
  
-   レポートおよび関連アイテムの一連のマスター コピーを保持します。 配置後、パブリッシュされたレポートが誤って変更される可能性があります。  
  
 このトピックの情報は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ソリューションで単一レポート プロジェクトのページ分割レポートおよび関連アイテムを設計する場合に参考にしてください。 SQL Server Data Tools のソリューションおよび複数のプロジェクトの詳細については、「 [SQL Server Data Tools の Reporting Services](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)」を参照してください。  

  
##  <a name="bkmk_SharedDataSources"></a> 共有データ ソース  
 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] を使用して、レポート ソリューションの共有データ ソースを定義および配置します。 共有データ ソースは、 **OverwriteDataSources** プロパティおよび **TargetDataSourceFolder** プロパティを使用して、プロジェクト内の他のアイテムとは別に配置できます。 詳細については、「[配置プロパティを設定する (Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md)」を参照してください。  
  
 レポート デザイナーでは、レポート データ ペインとソリューション エクスプローラーの両方で作業して、レポートで使用されるデータ ソースを定義します。 詳しくは、「 [Report Data Pane](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md#bkmk_ReportDataPane)」をご覧ください。 レポート サーバーまたは SharePoint サイトにパブリッシュされ、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] ソリューションに含まれていないデータ ソースを開く際に、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] を使用することはできません。 その機能については、「[レポート ビルダーの作成環境 (SSRS)](../../reporting-services/tools/report-builder-authoring-environment-ssrs.md)」を参照してください。  
  
 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] はクライアント ツールです。 レポート ソリューションをローカル コンピューターでテストし、サーバー ソリューションをテストするためにテスト環境に配置した後、運用環境に配置できます。 配置後、データ ソース処理拡張機能とデータ ソース資格情報がレポート サーバー環境用に構成されていることを確認します。 構成マネージャーを使用すると、さまざまな配置のプロパティを管理できます。 詳細については、「[SQL Server データ ツールの Reporting Services (SSDT)](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)」を参照してください。  
  
 詳細については、「 [データ接続、データ ソース、および接続文字列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)」を参照してください。  
   
##  <a name="bkmk_SharedDatasets"></a> 共有データセット  
 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] を使用して、レポート ソリューションの共有データセットを定義および配置します。 共有データセットは、 **OverwriteDatasets** プロパティおよび **TargetDatasetFolder** プロパティを使用して、プロジェクト内の他のアイテムとは別に配置できます。 詳細については、「[配置プロパティを設定する (Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md)」を参照してください。  
  
 レポート デザイナーでは、レポート データ ペインとソリューション エクスプローラーの両方で作業して、レポートで使用される共有データセットを定義します。 詳しくは、「 [Report Data Pane](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md#bkmk_ReportDataPane)」をご覧ください。 レポート サーバーまたは SharePoint サイトから直接パブリッシュ済みデータセットを開く際に、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] を使用することはできません。 その機能については、共有データセット モードで[レポート ビルダーの作成環境 (SSRS)](../../reporting-services/tools/report-builder-authoring-environment-ssrs.md) を使用します。  
  
 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] はクライアント ツールです。 クエリ デザイナーを使用すると、[プレビュー] でクエリ結果をローカルに作成してテストできます。 配置後、共有データセットは、依存する共有データ ソースおよびレポートとは別に管理できます。 詳細については、「[レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)」、「[クエリ デザイン ツール (SSRS)](../../reporting-services/report-data/query-design-tools-ssrs.md)」、および「[共有データセットを管理する](../../reporting-services/report-data/manage-shared-datasets.md)」を参照してください。  
  
##  <a name="bkmk_Reports"></a> ページネーションのあるレポート  
ページネーションのあるレポートは、レポート プロジェクト内に保存されるファイルです。 レポートは、スタンドアロン レポート、サブレポート、またはメイン レポートからのドリルスルー アクションの対象として使用できます。 **TargetReportFolder** プロパティおよびその他のプロパティを使用して、プロジェクト内の他のアイテムとは別にレポートを配置できます。 詳細については、「[配置プロパティを設定する (Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md)」を参照してください。  
  
> [!NOTE]  
>  SharePoint モードでレポート サーバーにパブリッシュする場合、レポート デザイナー プロジェクトでは一部のレポート ソリューション機能をテストできません。 レポート、サブレポート、および詳細レポートへの参照では、レポート プロジェクトの配置後にのみテストできる完全修飾 URL を使用する必要があります。 詳細については、「 [SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 &#40;SSRS&#41;](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)」を参照してください。  
  
 レポートは、次の方法でプロジェクトに追加できます。  
  
-   **新しいレポート プロジェクトを追加します。** 既定では、空のレポートがレポート デザイナーに表示されます。 詳細については、「[新規または既存のレポートをレポート プロジェクトに追加する (SSRS)](../../reporting-services/tools/add-a-new-or-existing-report-to-a-report-project-ssrs.md)」を参照してください。  
  
-   **レポート ウィザード プロジェクトを追加します。** 順を追った指示に従ってレポートを作成します。 レポート ウィザードでは、データ定義とレポート デザインが、一連の手順に簡略化され、完成したレポートが生成されます。 スタイルを追加して、組織のウィザードをカスタマイズできます。 詳細については、「[新規または既存のレポートをレポート プロジェクトに追加する (SSRS)](../../reporting-services/tools/add-a-new-or-existing-report-to-a-report-project-ssrs.md)」を参照してください。  
  
-   **新しい種類のアイテム (レポート) を追加します。** 空のレポートがレポート デザイナーに表示されます。  
  
-   **既存のアイテムを追加します。** 既存のレポート定義 (.rdl) がレポート デザイナーに表示されます。 以前のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] からレポートまたはプロジェクトを開くと、プロジェクトが現在のバージョンに、レポートが現在のスキーマに自動的にアップグレードされます。 詳細については、「 [Upgrade Reports](../../reporting-services/install-windows/upgrade-reports.md)」を参照してください。  
  
-   **[!INCLUDE[msCoName](../../includes/msconame-md.md)] Access レポートをインポートします。** Access データベース (.mdb、.accdb) またはプロジェクト (.adp) ファイルからすべてのレポートをインポートします。 レポート デザイナーによって、データベースまたはプロジェクト ファイル内の各レポートが RDL に変換され、レポート プロジェクト内に保存されます。 Access レポートのすべての機能がレポート定義 (.rdl) ファイルに転送されるわけではありません。 詳細については、「[Microsoft Access からレポートをインポートする &#40;Reporting Services&#41;](http://msdn.microsoft.com/library/4f29d5b8-b77d-4714-a84a-05523df55646)」および「[サポートされる Access レポート機能 &#40;SSRS&#41;](http://msdn.microsoft.com/library/7ffec331-6365-4c13-8e58-b77a48cffb44)」を参照してください。  
  
    > [!NOTE]  
    >  インポート機能を使用するには、レポート デザイナーがインストールされているコンピューターに Access 2002 以降のバージョンがインストールされている必要があります。 レポートのインポート時に、Access レポートのデータ ソースが使用可能な状態である必要があります。  
  
-   **RDL で直接操作します。** レポート デザイナーで作成したレポートは、XML 形式のレポート定義言語 (RDL) ファイルとして保存されます。 このファイルは、レポート デザイナー、テキスト エディターをはじめ、XML の編集が可能な任意のツールで編集できます。  
  
     レポート デザイナーでレポート定義ソースを編集する際は、開発ツールのインストール元である [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンの現在の RDL スキーマで作業していることになります。 プロジェクトを構築する際に、配置プロパティに応じてスキーマ バージョンが変更されることがあります。 詳細については、「 [SQL Server データ ツールの配置およびバージョン サポート (SSRS)](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)には含まれていません。  
  
     RDL を直接編集すると、生成されるレポートがレポート サーバーにパブリッシュできなかったり、実行できない場合があります。 XML ファイルと同様に、要素内で使用されている XML 固有の文字が正しくエンコードされていることを確認してください。 レポートをパブリッシュすると、レポート サーバー側でそのスキーマを基にして RDL ファイルに含まれる XML の検証が行われます。  
  
     RDL スキーマの一部ではない要素を含めるには、その要素を Custom 要素に配置します。 Custom 要素はカスタム表示拡張機能で読み取ることができますが、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]で提供されている表示拡張機能では無視されます。 たとえば、Custom 要素を使用するとレポートにコメントを保存できます。  
  
     詳細については、「[レポート定義言語 (SSRS)](../../reporting-services/reports/report-definition-language-ssrs.md)」を参照してください。  
  
##  <a name="bkmk_ReportParts"></a> レポート パーツ  
 レポート デザイナーで、プロジェクトのテーブル、グラフ、および他のページ分割されたレポート アイテムを作成した後、それらを " *レポート パーツ* " として、レポート サーバーまたはレポート サーバーと統合されている SharePoint サイトにパブリッシュできます。これにより、自分や他のユーザーが、それらのレポート パーツを別のレポートで再利用できるようになります。 詳細については、「[レポート デザイナーでのレポート パーツ &#40;SSRS&#41;](../../reporting-services/report-design/report-parts-in-report-designer-ssrs.md)」を参照してください。  
  
 **TargetReportPartFolder** プロパティおよびその他のプロパティを使用して、プロジェクト内の他のアイテムとは別にレポート パーツを配置できます。 詳細については、「[配置プロパティを設定する (Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md)」を参照してください。  
  
##  <a name="bkmk_Resources"></a> リソース  
 レポートに関連していて、レポート サーバーによって処理されないファイルを、プロジェクトに追加できます。 たとえば、写真の画像や空間データの ESRI シェープファイルを追加できます。 詳しくは、「 [Resources](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md#bkmk_Resources)」をご覧ください。  
 
##  <a name="bkmk_ReportLayout"></a> ページ分割されたレポートのレイアウト  
 レポート レイアウトを作成するには、レポート アイテムとデータ領域をツールボックスからデザイン画面にドラッグして位置を調整します。 レポートにデータを追加するには、データセット フィールドをデザイン画面のアイテムにドラッグします。 Tablix データ領域でデータをグループにまとめるには、データセット フィールドをグループ化ペインにドラッグします。 レポート作成ツールは基本的にレポート定義を作成する方法であるため、レポート ビルダーとレポート デザイナーのレポート デザイン方法は非常に似ています。  
   
##  <a name="bkmk_Preview"></a> ページ分割されたレポートのプレビュー  
 **[プレビュー]** は、レポート データとレイアウト デザインを確認する際に使用します。 レポートをプレビューすると、レポート プロセッサはレポート定義スキーマと式の構文を検証し、 [Output](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md#bkmk_Output) ウィンドウに問題を一覧表示します。  
  
> [!NOTE]  
>  レポートをプレビューすると、レポートのデータがローカル コンピューターのファイルにキャッシュされます。 同じレポートを、同じクエリ、パラメーター、および資格情報を使用して再びプレビューすると、レポート デザイナーはクエリを再実行する代わりにキャッシュされたコピーを表示します。 データ ファイルは *\<reportname>*.rdl.data として、レポート定義ファイルと同じディレクトリに保存されます。 レポート デザイナーを終了してもファイルは削除されません。  
  
 レポートは、次の方法でプレビューできます。  
  
-   **[プレビュー] ビュー。** **[プレビュー]** タブをクリックします。レポート サーバーで提供されるものと同じレポート処理および表示機能を使用して、レポートがローカルで実行されます。 表示されるレポートは対話型のイメージです。ユーザーは、パラメーターの選択、リンクのクリック、ドキュメント マップの表示、レポートの非表示部分の展開と折りたたみなどを行うことができます。 また、インストールされている任意の表示形式にレポートをエクスポートできます。  
  
-   **スタンドアロン プレビュー。** ブラウザーでローカル レポートを実行します。 デバッグ構成を使用すると、このモードを使用して、作成したカスタム アセンブリをデバッグすることもできます。 プロジェクトをデバッグ モードで実行するには 3 つの方法があります。  
  
    -   **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。  
  
    -   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の標準ツール バーの **[開始]** をクリックする。  
  
    -   F5 キーを押す。  
  
     レポートを作成しても配置しないプロジェクト構成を使用している場合は、現在の構成の **StartItem** プロパティで指定されたレポートが、別のプレビュー ウィンドウで開きます。  
  
    > [!NOTE]  
    >  デバッグ モードを使用するには、開始アイテムを設定する必要があります。 ソリューション エクスプローラーでレポート プロジェクトを右クリックし、 **[プロパティ]** をクリックします。次に、 **[StartItem]** で、表示するレポートの名前を選択します。  
  
     プロジェクトの開始アイテムではない特定のレポートをプレビューする場合は、レポートを作成しても配置しない構成 (DebugLocal 構成など) を選択し、レポートを右クリックして、 **[実行]** をクリックします。 レポートを配置しない構成を選択する必要があります。そうしないと、レポートはローカルのプレビュー ウィンドウに表示されずに、レポート サーバーにパブリッシュされます。  
  
-   **印刷プレビュー。**  
  
     プレビュー モードまたはプレビュー ウィンドウに最初に表示されるレポートは、HTML 表示拡張機能によって生成されるレポートと似ています。 プレビューは HTML 形式ではありませんが、レポートのレイアウトおよび改ページは HTML 出力と似ています。  
  
     印刷プレビュー モードに切り替えることによって、表示を変更し、印刷されるレポートを表示できます。 プレビュー ツール バーの **[印刷プレビュー]** ボタンをクリックします。 レポートは、実際のページに近い状態で表示されます。 この表示は、画像表示拡張機能および PDF 表示拡張機能によって生成される出力と似ています。 印刷プレビューは画像または PDF ファイルではありませんが、レポートのレイアウトおよびページ割り当ては、それらの形式での出力と似ています。 ページの幅を設定するなど、レポート画像のサイズを選択できます。  
  
     印刷プレビューを使用すると、レポートを印刷するときに発生する可能性があるさまざまなレポート表示の問題を識別できます。 一般的な表示の問題は次のとおりです。  
  
    -   レポートの幅が広すぎて、レポートに対して指定した用紙サイズに収まらないため、余分な空白ページが表示される。  
  
    -   指定した用紙の幅を超えて動的に拡張されるマトリックスがレポートに含まれているため、余分な空白ページが表示される。  
  
    -   グループ間の改ページが思いどおりに動作しない。  
  
    -   ヘッダーとフッターが期待どおりに表示されない。  
  
    -   印刷形式で読みやすいようにレポート レイアウトを変更する必要がある。  
   
##  <a name="bkmk_SaveandDeploy"></a> ページ分割レポートの保存および配置  
 レポート デザイナーでは、レポートおよび他のプロジェクト ファイルをローカルに保存することも、レポート サーバーまたは SharePoint サイトに配置することもできます。 共有データ ソース、共有データセット、レポート、レポート リソース、およびレポート パーツは、ユーザーが構成するプロジェクト配置プロパティに応じて、別々に配置することも、まとめて配置することもできます。 詳しくは、「 [Configuration and Deployment Properties](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md#bkmk_ConfigurationandDeploymentProperties)」をご覧ください。  
  
 レポート デザイナーでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の現在のバージョンの [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でサポートされているレポート定義スキーマを使用してレポートをデザインする点を理解しておくことが重要です。 特定のレポート サーバーまたは SharePoint サイトのプロジェクト配置プロパティを設定してから、レポートを保存すると、レポート デザイナーによって、対象レポート サーバーのバージョンと一致するスキーマ内のビルド ディレクトリにレポート定義が保存されます。 下位のレポート サーバー上でパブリッシュできるレポートを作成するために、レポート デザイナーは対象スキーマに存在しないレポート アイテムを削除します。 この処理は、メッセージが表示されずに自動的に行われます。 この場合、元のレポート定義はプロジェクト フォルダーに保持されます。 配置される変更済みのレポート定義は、ビルド フォルダーにあります。  
  
> [!NOTE]  
>  式および配置エラーをデバッグする場合、ビルド フォルダー内のレポート定義を表示する必要があります。 **[ソースの表示]** は使用しないでください。 **[ソースの表示]** を使用すると、プロジェクト フォルダーのレポート定義ソースが表示されます。  
  
 詳細については、「 [SQL Server データ ツールの配置およびバージョン サポート (SSRS)](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)には含まれていません。  
  
### <a name="save-a-report-locally"></a>ローカルでのレポートの保存  
 レポート デザイナーでレポートまたは他のプロジェクト アイテムを操作する場合、ファイルはローカル コンピューターまたはアクセス権限のある別のコンピューター上の共有に保存されます。  
  
 ソース管理ソフトウェアを使用している場合は、レポートを保存するときにレポートをソース管理サーバーにチェックインすることがあります。 詳しくは、「 [Source Control](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md#bkmk_SourceControl)」をご覧ください。  
  
### <a name="deploy-or-publish-paginated-reports"></a>ページ分割レポートの配置または公開  
 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]では、レポートまたは他のプロジェクト アイテムを複数のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーに配置できます。 対象レポート サーバーと互換性のあるスキーマ バージョンへのレポート定義のアップグレードを制御するには、プロジェクト構成を使用します。 プロジェクト構成で制御されるプロパティには、対象レポート サーバー、ビルド プロセスでプレビューと配置のためにレポートを一時的に保存するフォルダー、およびエラー レベルが含まれます。 詳細については、「[構成プロパティと配置プロパティ](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md#bkmk_ConfigurationandDeploymentProperties)」および「[配置プロパティを設定する (Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md)」を参照してください。  
  
### <a name="export-a-paginated-report-to-a-different-file-format"></a>別のファイル形式へのページ分割レポートのエクスポート  
 レポートは、さまざまな形式にエクスポートできますが、エクスポートすることによって、一部のレポート レイアウトや対話機能に影響が生じることがあります。 各種の出力形式に関するデザイン上の注意事項の詳細については、「[レポートのエクスポート (レポート ビルダーおよび SSRS)](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)」を参照してください。  
   
##  <a name="bkmk_ReportValidationandErrorLevels"></a> レポートの検証とエラー レベル  
 レポートは、プレビューの前および配置時に検証されます。 レポートをビルドする際にビルドに関する複数の問題が発生する可能性があります。 レポートには、プロジェクトによって指定された [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のバージョンと互換性のない、式やクエリなどの文字列が含まれる場合があります。  
  
 ビルドに関する警告やエラーを管理するには、ErrorLevel プロパティを使用します。 ErrorLevel プロパティには 0 ～ 4 の範囲の値が含まれます。 値によって、エラーとしてレポートされるビルドの問題や、警告としてレポートされるビルドの問題が決まります。 既定値は 2 です。 警告とエラーは [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)][Output](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md#bkmk_Output) ウィンドウに問題を一覧表示します。  
  
 ErrorLevel の値以下の重大度レベルを持つ問題は、エラーとしてレポートされます。それ以外の問題は、警告としてレポートされます。  
  
 次の表に、エラー レベルを示します。  
  
|エラー レベル|Description|  
|-----------------|-----------------|  
|0|レポートのプレビューおよび配置を妨げる、最も重大で避けることのできないビルドの問題。|  
|@shouldalert|レポートのレイアウトが大幅に変更される重大なビルドの問題。|  
|2|レポートのレイアウトが大きく変更される重大度のやや低いビルドの問題。|  
|3|レポートのレイアウトが目立たない程度に若干変更されるマイナーなビルドの問題。|  
|4|パブリッシュ上の警告としてのみ使用される。|  
  
 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]で新しくなったレポート アイテムが含まれるレポートをプレビューまたは配置しようとすると、これらのレポート アイテムはレポートから削除される可能性があります。 既定では、構成の ErrorLevel プロパティは 2 に設定されます。この設定では、マップが削除されると、レポートの作成が失敗する原因となります。 ただし、ErrorLevel プロパティの値を 0 または 1 に変更すると、マップが削除されても、警告が発行され、ビルド プロセスは続行されます。  

## <a name="next-steps"></a>次の手順

[SQL Server Data Tools のダウンロード](http://go.microsoft.com/fwlink/?LinkID=616714)  
[SQL Server Data Tools の Reporting Services](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)   
[クエリ デザイン ツール](../../reporting-services/report-data/query-design-tools-ssrs.md)   
[SQL Server Data Tools の配置およびバージョン サポート](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)  

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
