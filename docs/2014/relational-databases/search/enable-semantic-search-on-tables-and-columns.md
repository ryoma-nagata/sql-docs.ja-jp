---
title: テーブルおよび列に対するセマンティック検索の有効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], enabling
ms.assetid: 895d220c-6749-4954-9dd3-2ea4c6a321ff
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8187e19e40eba87e663c800ba9e593b30fe87a86
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296442"
---
# <a name="enable-semantic-search-on-tables-and-columns"></a>テーブルおよび列に対するセマンティック検索の有効化
  ドキュメントまたはテキストが格納されている選択した列に対して統計的セマンティック インデックス作成を有効または無効にする方法について説明します。  
  
 統計的セマンティック検索では、フルテキスト検索によって作成されたインデックスを使用し、追加のインデックスを作成します。 このフルテキスト検索に対する依存関係があるため、新しいフルテキスト インデックスの定義や既存のフルテキスト インデックスの変更の際には、新しいセマンティック インデックスを作成します。 新しいセマンティック インデックスを作成するには、このトピックで説明するように、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用するか、または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のフルテキスト インデックス作成ウィザードおよびその他のダイアログ ボックスを使用します。  
  
##  <a name="BasicEnabling"></a> セマンティック インデックスの作成  
  
###  <a name="reqenable"></a> セマンティック インデックスの作成の要件と制限  
  
-   インデックスは、フルテキスト インデックス作成でサポートされる、テーブルおよびインデックス付きビューを含むいずれかのデータベース オブジェクトに作成できます。  
  
-   特定の列のセマンティック インデックス作成を有効にするには、次の前提条件が満たされている必要があります。  
  
    -   データベースのフルテキスト カタログが存在する。  
  
    -   テーブルにフルテキスト インデックスがある。  
  
    -   選択された列がフルテキスト インデックスに含まれている。  
  
     これらのすべての要件は、同時に作成および有効化することができます。  
  
-   セマンティック インデックスは、フルテキスト インデックス作成でサポートされるいずれかのデータ型の列に作成できます。 詳細については、「 [フルテキスト インデックスの作成と管理](create-and-manage-full-text-indexes.md)」をご覧ください。  
  
-   フルテキスト検索のインデックス作成でサポートされているドキュメントの種類を指定する`varbinary(max)`列。 詳細については、このトピックの「 [方法: どのドキュメントの種類でインデックス作成ができるかを判断する](#doctypes) 」を参照してください。  
  
-   セマンティック インデックス作成では、選択した列に対し、キー フレーズのインデックスとドキュメントの類似性のインデックスの 2 種類のインデックスが作成されます。 セマンティック インデックス作成を有効にするときに 1 種類のインデックスだけを選択することはできません。 ただし、これらの 2 つのインデックスに対するクエリは別々に実行できます。 詳細については、「 [セマンティック検索を使用したドキュメント内のキー フレーズの検索](find-key-phrases-in-documents-with-semantic-search.md) 」および「 [セマンティック検索による類似および関連したドキュメントの検索](find-similar-and-related-documents-with-semantic-search.md)」をご覧ください。  
  
-   セマンティック インデックスの LCID を明示的に指定しない場合、セマンティック インデックス作成には主言語とそれに関連する言語統計のみが使用されます。  
  
-   言語モデルを使用できない列に対して言語を指定した場合、インデックスの作成は失敗し、エラー メッセージが返されます。  
  
###  <a name="HowToEnableCreate"></a> 方法: フルテキスト インデックスがない場合にセマンティック インデックスを作成します。  
 **CREATE FULLTEXT INDEX** ステートメントを使用して新しいフルテキスト インデックスを作成する場合、列定義の一部としてキーワード **STATISTICAL_SEMANTICS** を指定すると、列レベルでのセマンティック インデックス作成を有効にすることができます。 また、フルテキスト インデックス作成ウィザードを使用して新しいフルテキスト インデックスを作成するときにセマンティック インデックス作成を有効にすることもできます。  
  
 **TRANSACT-SQL を使用して新しいセマンティック インデックスを作成します。**  
 **CREATE FULLTEXT INDEX** ステートメントを呼び出し、セマンティック インデックスを作成するそれぞれの列に対して **STATISTICAL_SEMANTICS** を指定します。 このステートメントのすべてのオプションの詳細については、「[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)」をご覧ください。  
  
 **例 1: 一意のインデックス、フルテキスト インデックス、およびセマンティック インデックスを作成する**  
  
 次の例では、既定のフルテキスト カタログ、**ft** を作成します。次に、AdventureWorks2012 サンプル データベースの **HumanResources.JobCandidate** テーブルの **JobCandidateID** 列に一意のインデックスを作成します。 この一意のインデックスは、フルテキスト インデックスのキー列として必要です。 次に、 **Resume** 列にフルテキスト インデックスとセマンティック インデックスを作成します。  
  
```tsql  
CREATE FULLTEXT CATALOG ft AS DEFAULT  
GO  
  
CREATE UNIQUE INDEX ui_ukJobCand  
    ON HumanResources.JobCandidate(JobCandidateID)  
GO  
  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate  
    (Resume  
        Language 1033  
        Statistical_Semantics  
    )   
    KEY INDEX JobCandidateID   
    WITH STOPLIST = SYSTEM  
GO  
```  
  
 **例 2: インデックスの作成を遅延させて、いくつかの列でフルテキスト インデックスとセマンティック インデックスを作成する**  
  
 次の例では、AdventureWorks2012 サンプル データベースにフルテキスト カタログ **documents_catalog**を作成します。 その後、この新しいカタログを使用するフルテキスト インデックスを作成します。 フルテキスト インデックスは、 **Production.Document**テーブルの **Title**、 **DocumentSummary** 、 **Document** の各列に作成します。セマンティック インデックスは、 **Document** 列にのみ作成します。 このフルテキスト インデックスは、新たに作成されたフルテキスト カタログおよび既存の一意なキー インデックス、 **PK_Document_DocumentID**を使用します。 推奨されているように、このインデックス キーは整数列、 **DocumentID**に作成されます。 この例では、列のデータの言語である英語の LCID、1033 を指定します。  
  
 さらに、この例では、変更の追跡が OFF で、NO POPULATION を指定しています。 代わりに、 **ALTER FULLTEXT INDEX** ステートメントを指定して、後のピーク タイム以外の時間に新しいインデックスの完全作成を開始し、自動変更追跡を有効にしています。  
  
```tsql  
CREATE FULLTEXT CATALOG documents_catalog  
GO  
  
CREATE FULLTEXT INDEX ON Production.Document  
    (   
    Title  
        Language 1033,   
    DocumentSummary  
        Language 1033,   
    Document   
        TYPE COLUMN FileExtension  
        Language 1033  
        Statistical_Semantics  
    )  
    KEY INDEX PK_Document_DocumentID  
        ON documents_catalog  
        WITH CHANGE_TRACKING OFF, NO POPULATION  
GO  
```  
  
 後のピーク タイム以外の時間にインデックスを作成  
  
```tsql  
ALTER FULLTEXT INDEX ON Production.Document SET CHANGE_TRACKING AUTO  
GO  
```  
  
 **SQL Server Management Studio を使用して新しいセマンティック インデックスを作成します。**  
 フルテキスト インデックス作成ウィザードを実行し、セマンティック インデックスを作成するそれぞれの列に対し **[テーブル列の選択]** ページで **[統計的セマンティクス]** を有効にします。 フルテキスト インデックス作成ウィザードの起動方法などの詳細については、「 [フルテキスト インデックス作成ウィザードの使用](use-the-full-text-indexing-wizard.md)」をご覧ください。  
  
###  <a name="HowToEnableAlter"></a> 既存のフルテキスト インデックスがある場合にセマンティック インデックスを作成する方法  
 **ALTER FULLTEXT INDEX** ステートメントを使用して既存のフルテキスト インデックスを変更するとき、セマンティック インデックス作成を追加できます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のさまざまなダイアログ ボックスを使用して、セマンティック インデックス作成を追加することもできます。  
  
 **TRANSACT-SQL を使用してセマンティック インデックスを追加します。**  
 セマンティック インデックスを追加するそれぞれの列に対し、次に示すオプションを指定して **ALTER FULLTEXT INDEX** ステートメントを呼び出します。 このステートメントのすべてのオプションの詳細については、「[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)」をご覧ください。  
  
 特に指定しない限り、フルテキスト インデックスとセマンティック インデックスのどちらも **ALTER** 呼び出しの後に再作成されます。  
  
-   フルテキスト インデックス作成のみを列に追加するには、 **ADD** 構文を使用します。  
  
-   フルテキスト インデックス作成とセマンティック インデックス作成の両方を列に追加するには、 **STATISTICAL_SEMANTICS** オプションを指定した **ADD** 構文を使用します。  
  
-   フルテキスト インデックス作成が既に有効になっている列にセマンティック インデックス作成を追加するには、 **ADD STATISTICAL_SEMANTICS** オプションを使用します。 1 つの **ALTER** ステートメントでは 1 つの列にのみセマンティック インデックス作成を追加できます。  
  
 **例: フルテキスト インデックス作成が既に存在する列にセマンティック インデックス作成を追加する**  
  
 次の例では、AdventureWorks2012 サンプル データベースの **Production.Document** テーブルの既存のフルテキスト インデックスを変更します。 この例では、フルテキスト インデックスが既に存在している **Production.Document** テーブルの **Document** 列にセマンティック インデックスを追加します。 この例では、インデックスが自動的に再作成されないように指定します。  
  
```tsql  
ALTER FULLTEXT INDEX ON Production.Document  
    ALTER COLUMN Document  
        ADD Statistical_Semantics  
    WITH NO POPULATION  
GO  
```  
  
 **SQL Server Management Studio を使用してセマンティック インデックスを追加します。**  
 **[フルテキスト インデックスのプロパティ]** ダイアログ ボックスの **[フルテキスト インデックスの列]** ページで、セマンティック インデックス作成とフルテキスト インデックス作成が有効な列を変更できます。 詳細については、「 [フルテキスト インデックスの管理](../../database-engine/manage-full-text-indexes.md)」をご覧ください。  
  
###  <a name="addreq"></a> 既存のインデックスの変更の要件と制限  
  
-   インデックスの作成の進行中は既存のインデックスを変更できません。 インデックスの作成の進行状況を監視する方法の詳細については、「 [セマンティクス検索の管理および監視](manage-and-monitor-semantic-search.md)」をご覧ください。  
  
-   インデックス作成を列に追加する操作とこの列のインデックス作成を変更または削除する操作を **ALTER FULLTEXT INDEX** ステートメントの 1 回の呼び出しで行うことはできません。  
  
##  <a name="dropping"></a> セマンティック インデックスの削除  
  
###  <a name="drophow"></a> 方法: セマンティック インデックスを削除  
 **ALTER FULLTEXT INDEX** ステートメントを使用して既存のフルテキスト インデックスを変更するとき、セマンティック インデックス作成を削除できます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のさまざまなダイアログ ボックスを使用して、セマンティック インデックス作成を削除することもできます。  
  
 **TRANSACT-SQL を使用して、セマンティック インデックスを削除します。**  
 -   1 つまたは複数の列からセマンティック インデックス作成だけを削除するには、**ALTER COLUMN ***<列名>*** DROP STATISTICAL_SEMANTICS** オプションを指定して、**ALTER FULLTEXT INDEX** ステートメントを呼び出します。 1 つの **ALTER** ステートメントを使用して複数の列からインデックス作成を削除できます。  
  
    ```tsql  
    USE database_name  
    GO  
  
    ALTER FULLTEXT INDEX  
        ALTER COLUMN column_name  
        DROP STATISTICAL_SEMANTICS  
    GO  
    ```  
  
-   列からフルテキスト インデックス作成とセマンティック インデックス作成の両方を削除するには、**ALTER COLUMN ***<列名>*** DROP** オプションを指定して、**ALTER FULLTEXT INDEX** ステートメントを呼び出します。  
  
    ```tsql  
    USE database_name  
    GO  
  
    ALTER FULLTEXT INDEX  
        ALTER COLUMN column_name  
        DROP  
    GO  
    ```  
  
 **SQL Server Management Studio を使用して、セマンティック インデックスを削除します。**  
 **[フルテキスト インデックスのプロパティ]** ダイアログ ボックスの **[フルテキスト インデックスの列]** ページで、セマンティック インデックス作成とフルテキスト インデックス作成が有効な列を変更できます。 詳細については、「 [フルテキスト インデックスの管理](../../database-engine/manage-full-text-indexes.md)」をご覧ください。  
  
###  <a name="dropreq"></a> セマンティック インデックスの削除の要件と制限  
  
-   セマンティック インデックス作成を保持しているときに列からフルテキスト インデックス作成を削除することはできません。 セマンティック インデックス作成は、ドキュメントの類似性の結果に関してフルテキスト インデックス作成に依存します。  
  
-   セマンティック インデックス作成が有効になっていたテーブルの最後の列からセマンティック インデックス作成を削除するときは、 **NO POPULATION** オプションを指定できません。 以前にインデックスが作成された結果を削除するには、インデックス作成サイクルが必要になります。  
  
## <a name="checking-whether-semantic-search-is-enabled-on-database-objects"></a>データベース オブジェクトでセマンティック検索が有効かどうかの確認  
  
###  <a name="HowToCheckEnabled"></a> 方法: データベース オブジェクトでセマンティック検索が有効になっているかどうかを確認します。  
 **データベースに対してセマンティック検索が有効でしょうか。**  
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) メタデータ関数の **IsFullTextEnabled** プロパティのクエリを実行します。  
  
 戻り値 1 は、データベースに対してフルテキスト検索とセマンティック検索が有効化されていることを示します。戻り値 0 は、フルテキスト検索とセマンティック検索が有効化されていないことを示します。  
  
```tsql  
SELECT DATABASEPROPERTYEX('database_name', 'IsFullTextEnabled')  
GO  
```  
  
 **テーブルに対してセマンティック検索が有効にしますか。**  
 [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql) メタデータ関数の **TableFullTextSemanticExtraction** プロパティのクエリを実行します。  
  
 戻り値 1 は、テーブルに対してセマンティック検索が有効化されていることを示します。戻り値 0 は、セマンティック検索が有効化されていないことを示します。  
  
```scr  
SELECT OBJECTPROPERTYEX(OBJECT_ID('table_name'), 'TableFullTextSemanticExtraction')  
GO  
```  
  
 **列に対してセマンティック検索が有効にしますか。**  
 特定の列に対して統計的セマンティック検索が有効化されているかどうかを確認するには、次の操作を実行します。  
  
-   [COLUMNPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql) メタデータ関数の **StatisticalSemantics** プロパティのクエリを実行します。  
  
     戻り値 1 は、列に対してセマンティック検索が有効化されていることを示します。戻り値 0 は、セマンティック検索が有効化されていないことを示します。  
  
    ```tsql  
    SELECT COLUMNPROPERTY(OBJECT_ID('table_name'), 'column_name', 'StatisticalSemantics')  
    GO  
    ```  
  
-   フルテキスト インデックスのカタログ ビュー [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) のクエリを実行します。  
  
     **statistical_semantics** 列の値 1 は、指定された列に対してフルテキスト インデックス作成とセマンティック インデックス作成が有効になっていることを示します。  
  
    ```tsql  
    SELECT * FROM sys.fulltext_index_columns WHERE object_id = OBJECT_ID('table_name')  
    GO  
    ```  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]のオブジェクト エクスプローラーで、列を右クリックし、 **[プロパティ]** を選びます。 **[列のプロパティ]** ダイアログ ボックスの **[全般]** ページで、 **[統計的セマンティクス]** プロパティの値を確認します。  
  
     値 True は、指定された列に対してフルテキスト インデックス作成とセマンティック インデックス作成が有効になっていることを示します。  
  
## <a name="determining-what-can-be-indexed-for-semantic-search"></a>セマンティック検索用にインデックスを作成できる対象の確認  
  
###  <a name="HowToCheckLanguages"></a> 方法: セマンティック検索はサポートされている言語を確認します。  
  
> [!IMPORTANT]  
>  セマンティック インデックス作成は、フルテキスト インデックス作成ほどサポートされている言語が多くありません。 このため、フルテキスト検索用にインデックスを作成できる一方でセマンティック検索用にはインデックスを作成できない列が存在する場合があります。  
  
 カタログ ビュー [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql) のクエリを実行します。  
  
```tsql  
SELECT * FROM sys.fulltext_semantic_languages  
GO  
```  
  
 セマンティック インデックス作成でサポートされている言語は以下のとおりです。 この一覧は、LCID の順に並べ替えたカタログ ビュー [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql) の出力を表します。  
  
|[言語]|LCID (LCID)|  
|--------------|----------|  
|ドイツ語|1031|  
|英語 (米国)|1033|  
|フランス語|1036|  
|イタリア語|1040|  
|ポルトガル語 (ブラジル)|1046|  
|ロシア語|1049|  
|スウェーデン語|1053|  
|英語 (英国)|2057|  
|ポルトガル語 (ポルトガル)|2070|  
|スペイン語|3082|  
  
###  <a name="doctypes"></a> どのドキュメントの種類のインデックスを作成できるを取得する方法  
 カタログ ビュー [sys.fulltext_document_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) のクエリを実行します。  
  
 インデックスの対象とするドキュメントの種類が、サポートされている種類の一覧に含まれていない場合は、追加のフィルターを探してダウンロードし、インストールしなければならない場合があります。 詳細については、「 [登録済みのフィルターおよびワード ブレーカーの表示または変更](view-or-change-registered-filters-and-word-breakers.md)」を参照してください。  
  
##  <a name="BestPracticeFilegroup"></a> ベスト プラクティス: フルテキストおよびセマンティック インデックスの個別のファイル グループの作成を検討してください。  
 ディスク領域の割り当てが問題となる場合は、フルテキスト インデックスとセマンティック インデックスに対して別個のファイル グループを作成することを検討してください。 セマンティック インデックスは、フルテキスト インデックスと同じファイル グループに作成されます。 完全に作成されたセマンティック インデックスには大量のデータが含まれる可能性があります。  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="IssueNoResults"></a> 問題点: 特定の列の検索で結果が返されない  
 **Unicode 以外の LCID が Unicode 言語に指定されていませんか。**  
 Unicode の語のみを含む言語の LCID (たとえば、ロシア語の LCID 1049) を持つ非 Unicode 列型に対してセマンティック インデックス作成を有効にすることができます。 この場合、この列のセマンティック インデックスから結果が返されることはありません。  
  
  
