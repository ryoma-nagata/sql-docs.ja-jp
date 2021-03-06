---
title: クエリ言語 (SQL) の構造 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC]
- SQL [ODBC], about SQL
- ODBC [ODBC], SQL
ms.assetid: bebfd93e-0dc0-46b3-a531-518beb7ea976
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a32983b1dd4faaa64c09f5ccc773fd4ce78f3533
ms.sourcegitcommit: 731c5aed039607a8df34c63e780d23a8fac937e1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909552"
---
# <a name="structured-query-language-sql"></a>構造化照会言語 (SQL) (Structured Query Language) (SQL)
一般的な DBMS では、格納、アクセス、および整理された、効率的な方法でデータを変更することができます。 最初に、Dbms のユーザーには、プログラマがでした。 格納されているデータにアクセスするには、COBOL などのプログラミング言語でプログラムの作成が必要です。 これらのプログラムは、技術面以外のユーザーにわかりやすいインターフェイスを提供する多くの場合、書き込まれた、データ自体へのアクセスでは、知識の豊富なプログラマのサービスが必要です。 データへのアクセスをカジュアルが実用的でした。  
  
 ユーザーがこのような状況に完全に満足でした。 データにアクセスすることが、中に多くの場合、特別なソフトウェアを記述するプログラマは DBMS を納得させることが必要です。 たとえば、営業部門では、その販売員ごと、前の月の売上合計を表示して、会社のサービスの各販売員の長さによって順番ランク付けされたこの情報が必要、その 2 つの選択肢: のいずれかのプログラムが既に存在します。これにより、正確にアクセスする情報を許可または部門は、このようなプログラムを記述するプログラマを依頼する必要があります。 多くの場合、これは、価値があると、常に 1 回だけ、または、アドホックの問い合わせに関して、コストのソリューションがより多くの作業です。 ますます多くのユーザーには、簡単にアクセスが必要で、この問題はより大きな成長しました。  
  
 アドホックのデータにアクセスするユーザーを許可するには、express の要求を使用する言語を与えることが必要です。 データベースに 1 つの要求が; クエリとして定義されています。このような言語には、クエリ言語が呼び出されます。 このため、多くのクエリ言語が開発されましたが、最も人気のあるこれらのいずれかのようになりました。 構造化照会言語、1970 年代に IBM に考案されました。 SQL では、その頭字語では、既知のより一般的なと、"ess キュー ell"と「続編」の両方に発揮されます。 SQL は、標準 1986 年に ANSI および ISO 1987; で標準的なようになりました。優れた多くのデータベース管理システムで今すぐに使用されます。  
  
 SQL は、アドホック ユーザーのニーズを解決したら、コンピューター プログラムによるデータ アクセスの必要はなくなっていません。 実際には、ほとんどのデータベースへのアクセスもされました (とは) プログラムを定期的にスケジュールされたレポートおよび統計分析の形式で、データ入力プログラムなど、口座の調整に使用されるものなどの操作プログラム注文エントリでは、データの使用、および作業指示を生成します。  
  
 これらのプログラムは、次の 3 つの手法の 1 つを使用して、SQL を使用しても。  
  
-   **埋め込み SQL**C や COBOL などのホスト言語で SQL ステートメントが埋め込まれます。  
  
-   **SQL モジュール**では、どの SQL ステートメントは、DBMS にコンパイルされ、ホスト言語から呼び出されます。  
  
-   **コールレベル インターフェイス**、または CLI で、SQL ステートメントを DBMS に渡すと、DBMS から結果を取得するという関数で構成されます。  
  
> [!NOTE]  
>  アプリケーションのプログラミングではなく呼び出しレベルのインターフェイスが使用される用語のインターフェイス (API) を偶然が同じ別の用語。 データベースの世界では、SQL そのものを記述する API を使用します。 SQL は、DBMS に API。  
  
 これらの選択肢の embedded SQL は最もよく使用されるほとんどの主要な Dbms が独自の Cli をサポートです。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQL ステートメントの処理](../../odbc/reference/processing-a-sql-statement.md)  
  
-   [埋め込み SQL](../../odbc/reference/embedded-sql.md)  
  
-   [SQL モジュール](../../odbc/reference/sql-modules.md)  
  
-   [コールレベル インターフェイス](../../odbc/reference/call-level-interfaces.md)
