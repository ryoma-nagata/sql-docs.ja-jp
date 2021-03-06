---
title: メモリ最適化テーブル | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 14dddf81-b502-49dc-a6b6-d18b1ae32d2b
caps.latest.revision: 65
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6427878b5c032e0560859ab7ba68af8d06fb40e1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276548"
---
# <a name="memory-optimized-tables"></a>メモリ最適化テーブル
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインメモリ OLTP は、メモリ最適化された効率的なデータ アクセス、ビジネス ロジックのネイティブ コンパイル、ロック フリーおよびラッチ フリーのアルゴリズムによって OLTP アプリケーションのパフォーマンスを高めます。 インメモリ OLTP 機能には、メモリ最適化テーブルおよびテーブル型と、これらのテーブルに効率的にアクセスするための [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャのネイティブ コンパイルが含まれます。  
  
 メモリ最適化テーブルの詳細については、以下を参照してください。  
  
-   [メモリ最適化テーブルの概要](memory-optimized-tables.md)  
  
     メモリ最適化テーブルについて詳述し、データの耐久性、メモリ最適化テーブルのデータへのアクセス、パフォーマンス、スケーラビリテに関する情報を提供します。  
  
-   [テーブルとストアド プロシージャのネイティブ コンパイル](../in-memory-oltp/natively-compiled-stored-procedures.md)  
  
     どのようにメモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャが DLL にコンパイルされるかについて詳述し、関連するセキュリティ上の考慮事項を示します。  
  
-   [メモリ最適化テーブルの変更](altering-memory-optimized-tables.md)  
  
     メモリ最適化テーブルの更新 (テーブルの列、索引、および bucket_count の変更など) に関するガイドラインです。  
  
-   [メモリ最適化テーブルを対象にするトランザクションについて](../../database-engine/understanding-transactions-on-memory-optimized-tables.md)  
  
     このセクションには、メモリ最適化テーブルでのトランザクションの実行に関連するいくつかのトピック (トランザクション分離レベル、クロスコンテナーなど) があります。  
  
-   [メモリ最適化テーブルのパーティション分割に関するアプリケーションのパターン](application-pattern-for-partitioning-memory-optimized-tables.md)  
  
     メモリ最適化テーブルの使用時にパーティション テーブルをエミュレートする方法を示す詳細なコード サンプルです。  
  
-   [メモリ最適化テーブルの統計](statistics-for-memory-optimized-tables.md)  
  
     メモリ最適化テーブルで統計をまとめる方法とメモリ最適化テーブルで統計を保守および手動更新する方法について詳述します。  
  
-   [照合順序とコード ページ](../../database-engine/collations-and-code-pages.md)  
  
     メモリ最適化テーブルでサポートされる照合およびコード ページに関する制限について詳述します。  
  
-   [メモリ最適化テーブルのテーブルと行のサイズ](table-and-row-size-in-memory-optimized-tables.md)  
  
     メモリ最適化テーブルの行に関する 8060 バイトの制限について詳述し、テーブルおよび行のサイズの計算例を提供します。  
  
-   [メモリ最適化テーブルのクエリ処理のガイド](a-guide-to-query-processing-for-memory-optimized-tables.md)  
  
     メモリ最適化テーブルとネイティブ コンパイル ストアド プロシージャの両方に対するクエリ処理の概要について説明します。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](in-memory-oltp-in-memory-optimization.md)  
  
  
