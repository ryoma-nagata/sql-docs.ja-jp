---
title: 列ストア インデックス - 概要 | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- indexes creation, columnstore
- indexes [SQL Server], columnstore
- columnstore index
- batch mode execution
- columnstore index, described
- xVelocity, columnstore indexes
ms.assetid: f98af4a5-4523-43b1-be8d-1b03c3217839
caps.latest.revision: 80
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f6647b4e87a1ea3e83bd76eacde73a93c7b6fe57
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37791443"
---
# <a name="columnstore-indexes---overview"></a>列ストア インデックス - 概要
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

*列ストア インデックス* は、大規模なデータ ウェアハウス ファクト テーブルを格納し、そのテーブルにクエリを実行するための標準です。 このインデックスは列ベースのデータ ストレージとクエリ処理を使用して、データ ウェアハウスで最大 **10 倍のクエリ パフォーマンス** (従来の行指向ストレージと比較)、および最大 **10 倍のデータ圧縮** (非圧縮データ サイズと比較) を実現します。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降、列ストア インデックスでは運用分析が可能になり、トランザクション ワークロードでパフォーマンスの高いリアルタイム分析を実行することができます。  
  
シナリオに移動:  
  
-   [データ ウェアハウスの列ストア インデックス](../../relational-databases/indexes/columnstore-indexes-data-warehouse.md)  
-   [列ストアを使用したリアルタイム運用分析の概要](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
  
## <a name="what-is-a-columnstore-index"></a>列ストア インデックスとは  
 *columnstore index* は、列ストアと呼ばれる列指向データ形式を使用してデータを格納、取得、および管理するためのテクノロジです。  
  
### <a name="key-terms-and-concepts"></a>主な用語と概念  
ここでは、列ストア インデックスに関連する主な用語と概念について説明します。  
  
**列ストア**  
*列ストア* は、行と列を含むテーブルとして論理的に編成され、列方向のデータ形式で物理的に格納されているデータです。  
  
**行ストア**  
*行ストア* は、行と列を含むテーブルとして論理的に編成され、行方向のデータ形式で物理的に格納されているデータです。 これは、リレーショナル テーブル データを格納する従来の方法です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、行ストアは、基になるデータ ストレージ形式が、ヒープ、クラスター化インデックス、またはメモリ最適化テーブルであるテーブルを示します。  
  
> [!NOTE]  
> 列ストア インデックスの説明では、データ ストレージの形式を強調する目的で *行ストア* と *列ストア* という用語を使用しています。  
  
**行グループ**  
*行グループ* は、同時に列ストア形式に圧縮される行のグループです。 通常、1 つの行グループには、行グループあたりの最大行数である 1,048,576 行が含まれます。  
  
高パフォーマンスと高い圧縮率を実現するために、列ストア インデックスは、テーブルを行グループと呼ばれる行のグループにスライスし、各行グループを列方向に圧縮します。 行グループ内の行数は、高い圧縮率が実現される程度に多く、インメモリ操作の利点を得られる程度に少なくなければなりません。    

**列セグメント**  
*列セグメント* は、行グループ内のデータ列です。  
  
-   それぞれの行グループには、テーブルの 1 つの列につき 1 つの列セグメントが含まれます。  
-   それぞれの列セグメントは一緒に圧縮され、物理メディアに格納されます。  
  
![Column segment](../../relational-databases/indexes/media/sql-server-pdw-columnstore-columnsegment.gif "Column segment")  
  
**クラスター化列ストア インデックス**  
*クラスター化列ストア インデックス* は、テーブル全体に対する物理ストレージです。    
  
![Clustered Columnstore Index](../../relational-databases/indexes/media/sql-server-pdw-columnstore-physicalstorage.gif "Clustered Columnstore Index")  
  
列セグメントの断片化を低減し、パフォーマンスを高めるために、列ストア インデックスでは、一部のデータを、クラスター化インデックス (デルタストアと呼ばれます) と削除された行の ID の btree リストに格納することがあります。 デルタストア操作は内部で処理されます。 列ストア インデックスは、正しいクエリ結果を返すために、列ストアとデルタストアの両方からのクエリ結果を結合します。  
  
**デルタ行グループ**  
*デルタ行グループ*は、列ストア インデックスでのみ使用されるクラスター化インデックスです。このデルタストアは、行数がしきい値に達して列ストアに移動できるまで行を格納することで、列ストアの圧縮とパフォーマンスを高めます。  

デルタ行グループは、最大行数に達すると閉じられます。 閉じている行グループは、組ムーバー プロセスによって確認されます。 閉じている行グループが見つかると、その行グループが圧縮され、列ストアに格納されます。  
  
**デルタストア** A 列ストア インデックスは、複数のデルタ行グループを持つことができます。  すべてのデルタ行グループは総称して、*デルタストア*と呼ばれます。   

大規模な一括読み込みでは、行のほとんどがデルタストアを通らずに列ストアに直接移動します。 一括読み込みの最後に位置する行の数は、行グループの最小サイズである 102,400 行を満たすには足りないことがあります。 この場合、それらの行は列ストアではなくデルタストアに移動します。 102,400 行未満の小規模な一括読み込みでは、すべての行がデルタストアに直接移動します。  
  
**非クラスター化列ストア インデックス**  
*非クラスター化列ストア インデックス* とクラスター化列ストアインデックスは同じように機能します。 異なるのは、非クラスター化列ストア インデックスが、行ストア テーブルに作成されたセカンダリ インデックスであるのに対し、クラスター化インデックスは、テーブル全体のプライマリ ストレージである点です。  
  
非クラスター化インデックスには、基になるテーブルの行と列の一部または全体のコピーが含まれています。 インデックスはテーブルの 1 つ以上の列として定義され、行のフィルター処理条件をオプションで設定できます。  
  
非クラスター化列ストア インデックスによりリアルタイム運用分析が可能になります。ここで、OLTP ワークロードは基になるクラスター化インデックスを使用します。一方、列ストア インデックスでは同時に分析が実行されます。 詳細については、「 [Get started with Columnstore for real time operational analytics (列ストアを使用したリアルタイム運用分析の概要)](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)」を参照してください。  
  
**バッチ モード実行**  
"*バッチ モード実行*" は、複数の行をまとめて処理するためのクエリ処理方法です。 バッチ モード実行は、列ストア ストレージ形式と緊密に統合され、このストレージ形式に合わせて最適化されています。 バッチ モード実行は、ベクター ベースの実行またはベクター化された実行と呼ばれることもあります。 列ストア インデックスのクエリではバッチ モード実行が使用され、これによりクエリ パフォーマンスが、通常、2 ～ 4 倍向上します。 実行モードについて詳しくは、「[クエリ処理アーキテクチャ ガイド](../query-processing-architecture-guide.md#execution-modes)」をご覧ください。 
  
##  <a name="benefits"></a> 列ストア インデックスを使用する理由  
列ストア インデックスにより、非常に高いレベルでデータ圧縮が実現し (通常 10 倍)、データ ウェアハウスのストレージ コストが大幅に削減されます。 さらに、分析についても、btree インデックスと比べ、桁違いに優れたパフォーマンスを発揮します。 この列ストア インデックスは、データ ウェアハウスと分析ワークロードの推奨データ ストレージ形式です。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降、運用ワークロードにおけるリアルタイム分析で列ストア インデックスを使用できます。  
  
列ストア インデックスが高速に動作する理由:  
  
-   列には同じドメインの値 （一般的に似たような値） が格納されます。これにより圧縮率が上がります。 また、システムの IO のボトルネックが最小化または排除され、メモリ使用量も大幅に削減されます。  
  
-   高い圧縮比率により、メモリ使用量が削減され、クエリのパフォーマンスが向上します。 さらに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がより多くのクエリやデータ操作をインメモリで実行できるため、クエリのパフォーマンスが向上する場合があります。  
  
-   バッチ実行では複数の行をまとめて処理することで、クエリのパフォーマンスを高めます (通常は 2 ～ 4 倍)。  
  
-   クエリはテーブルから少数の列のみを選択することが多く、物理メディアからの合計 I/O を低減します。  
  
## <a name="when-should-i-use-a-columnstore-index"></a>列ストア インデックスを使用するタイミング  
推奨されるユース ケース  
  
-   クラスター化列ストア インデックスを使用して、データ ウェアハウス ワークロード用にファクト テーブルと大きなディメンション テーブルを格納します。 これにより、クエリ パフォーマンスとデータ圧縮が最大 10 倍に向上します。 「 [データ ウェアハウスの列ストア インデックス](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md)」を参照してください。  
  
-   非クラスター化列ストア インデックスを使用して、OLTP ワークロードでリアルタイム分析を実行します。 「 [Get started with Columnstore for real time operational analytics (列ストアを使用したリアルタイム運用分析の概要)](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)」を参照してください。  
  
### <a name="how-do-i-choose-between-a-rowstore-index-and-a-columnstore-index"></a>行ストア インデックスと列ストア インデックスはどのように選択すればよいですか。  
行ストア インデックスは、データのシーク、特定の値の検索、狭い範囲の値でのクエリ検索を実行するときに最適なパフォーマンスを発揮します。 トランザクション ワークロードでは、テーブル スキャンではなく主にテーブル シークを必要とする傾向があるため、行ストア インデックスを使用してください。  
  
列ストア インデックスは、特に大規模なテーブルで、大量のデータをスキャンする分析クエリを実行するときにパフォーマンスが高くなります。  この列ストア インデックスは、特にファクト テーブルのデータ ウェアハウスと分析のワークロードで使用します。ファクト テーブルでは、テーブル シークではなくテーブル全体のスキャンが必要になることが多いためです。  
  
### <a name="can-i-combine-rowstore-and-columnstore-on-the-same-table"></a>行ストアと列ストアを同じテーブルで結合できますか。  
可能。 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降、更新可能な非クラスター化列ストア インデックスを、行ストア テーブルに作成できます。 列ストア インデックスには、選択された列のコピーが格納されるため追加の空き領域が必要ですが、圧縮機能が平均で 10 に倍向上します。 これにより、同時に、列ストア インデックスの分析と行ストア インデックスのトランザクションを同時に実行できます。 行ストア テーブルでデータが変更されると列ストアが更新されます。したがって、両方のインデックスが、同じデータに対して作業を行うことになります。  
  
[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降、列ストア インデックスでは、1 つ以上の非クラスター化行ストア インデックスを使用できます。 これにより、基になる列ストアで、効率的なテーブル シークを実行できます。 他のオプションも使用できます。 たとえば、行ストア テーブルで UNIQUE 制約を使用することで、主キー制約を適用できます。 一意でない値は行ストア テーブルに挿入できないため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でその値を列ストアに挿入することはできません。  
  
## <a name="metadata"></a>メタデータ  
列ストア インデックス内のすべての列は、付加列としてメタデータに格納されます。 列ストア インデックスにキー列はありません。  

|||
|-|-|  
|[sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)|[sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)|  
|[sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)|[sys.internal_partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md)|  
|[sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)|[sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)|  
|[sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)|[sys.dm_db_column_store_row_group_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)|  
|[sys.dm_db_column_store_row_group_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md)|[sys.dm_column_store_object_pool &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-column-store-object-pool-transact-sql.md)|  
|[sys.dm_db_column_store_row_group_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)|[sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)|  
|[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)||  
  
## <a name="related-tasks"></a>Related Tasks  
クラスター化列ストア インデックスとしてリレーショナル テーブルを指定していない限り、そのリレーショナル テーブルでは、行ストアが、基になるデータ形式として使用されます。 `WITH CLUSTERED COLUMNSTORE INDEX` オプションを指定しない場合、`CREATE TABLE` によって行ストア テーブルが作成されます。  
  
`CREATE TABLE` ステートメントでテーブルを作成するとき、そのテーブルを列ストアとして作成するには、`WITH CLUSTERED COLUMNSTORE INDEX` オプションを指定します。 既に、行ストア テーブルがある場合、その行ストアは、`CREATE COLUMNSTORE INDEX` ステートメントを使用して列ストアに変換できます。  
  
|タスク|参照トピック|注|  
|----------|----------------------|-----------|  
|テーブルを列ストアとして作成する。|[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降、テーブルをクラスター化列ストア インデックスとして作成できます。 最初に行ストア テーブルを作成して列ストアに変換する必要はありません。|  
|列ストア インデックスを持つメモリ テーブルを作成します。|[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降、列ストア インデックスを持つ、メモリ最適化テーブルを作成できます。 列ストア インデックスは、テーブルの作成後に、ALTER TABLE ADD INDEX 構文を使用して追加することもできます。|  
|行ストア テーブルを列ストアに変換する。|[CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)|既存のヒープまたはバイナリ ツリーを列ストアに変換します。 この変換を実行するときの既存のインデックスとインデックス名の処理方法を例示します。|  
|列ストア テーブルを行ストアに変換する。|[CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)|通常、これは必要ありませんが、状況によっては、この変換を実行しなければならないことがあります。 列ストアをヒープまたはクラスター化インデックスに変換する方法を例示します。|  
|行ストア テーブルで列ストア インデックスを作成する。|[CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)|行ストア テーブルでは列ストア インデックスを 1 つ使用できます。  [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降、列ストア インデックスにフィルター条件を指定できるようになりました。 基本構文を例示します。|  
|運用分析のパフォーマンスの高いインデックスを作成する。|[列ストアを使用したリアルタイム運用分析の概要](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)|補完的な列ストア インデックスと btree インデックスを作成する方法について説明します。OLTP クエリでは btree インデックスが使用され、分析クエリでは列ストア インデックスが使用されます。|  
|データ ウェアハウス用のパフォーマンスの高い列ストア インデックスを作成する。|[データ ウェアハウスの列ストア インデックス](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md)|列ストア テーブルで btree インデックスを使用して、パフォーマンスの高いデータ ウェアハウス クエリを作成する方法について説明します。|  
|btree インデックスを使用して列ストア インデックスに主キー制約を適用する|[データ ウェアハウスの列ストア インデックス](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md)|btree インデックスと列ストア インデックスを組み合わせて、列ストア インデックスに主キー制約を適用する方法を示します。|  
|列ストア インデックスを削除する|[DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)|列ストア インデックスは、btree インデックスが使用する標準の DROP INDEX 構文を使って削除します。 クラスター化列ストア インデックスを削除すると、列ストア テーブルがヒープに変換されます。|  
|列ストア インデックスから行を削除する|[DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)|[DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md) を使用して行を削除します。<br /><br /> **列ストア** 行: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は行を論理的に削除されたとしてマークしますが、インデックスが再構築されるまで行の物理ストレージを再確保することはありません。<br /><br /> **デルタストア** 行: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は論理的および物理的に行を削除します。|  
|列ストア インデックスの行を更新する|[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)|[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md) を使用して行を更新します。<br /><br /> **列ストア** 行:  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は行を論理的に削除されたとしてマークし、更新された行をデルタストアに挿入します。<br /><br /> **デルタストア** 行: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、デルタストアの行を更新します。|  
|データを列ストア インデックスに読み込む|[列ストア インデックス データの読み込み](~/relational-databases/indexes/columnstore-indexes-data-loading-guidance.md)||  
|デルタストアのすべての行を強制的に列ストアに移動します。|[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md) ...REBUILD<br /><br /> [列ストア インデックスの最適化](~/relational-databases/indexes/columnstore-indexes-defragmentation.md)|ALTER INDEX に REBUILD オプションを指定すると、すべての行が列ストアに強制的に移動されます。|  
|列ストア インデックスを最適化する|[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)|ALTER INDEX … REORGANIZE は、列ストア インデックスをオンラインで最適化します。|  
|テーブルと列ストア インデックスをマージする。|[MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)||  
  
## <a name="see-also"></a>参照  
 [列ストア インデックス データの読み込み](~/relational-databases/indexes/columnstore-indexes-data-loading-guidance.md)   
 [列ストア インデックスのバージョン管理機能の概要](~/relational-databases/indexes/columnstore-indexes-what-s-new.md)   
 [列ストア インデックスのクエリ パフォーマンス](~/relational-databases/indexes/columnstore-indexes-query-performance.md)   
 [列ストアを使用したリアルタイム運用分析の概要](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 [データ ウェアハウスの列ストア インデックス](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md)   
 [列ストア インデックスの最適化](~/relational-databases/indexes/columnstore-indexes-defragmentation.md)   
 [SQL Server インデックス デザイン ガイド](../../relational-databases/sql-server-index-design-guide.md)   
 [列ストア インデックスのアーキテクチャ](../../relational-databases/sql-server-index-design-guide.md#columnstore_index)   
  
  
