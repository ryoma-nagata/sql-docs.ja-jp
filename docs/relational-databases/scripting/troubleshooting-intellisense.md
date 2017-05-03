---
title: "IntelliSense のトラブルシューティング (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unavailable options [IntelliSense]
- IntelliSense [SQL Server], troubleshooting
- IntelliSense [SQL Server], unavailable options
- troubleshooting [IntelliSense]
ms.assetid: 4b72ffc6-aea2-4e11-ab36-fa2de4d7bcc5
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d5926bbe8569ed88f2697d17cd754cf0fd081f05
ms.lasthandoff: 04/11/2017

---
# <a name="troubleshooting-intellisense"></a>IntelliSense のトラブルシューティング
  IntelliSense オプションが正しく機能しないことがあります。  
  
## <a name="conditions-that-affect-intellisense"></a>IntelliSense が影響を受ける状況  
 次の場合に IntelliSense の動作が影響を受ける可能性があります。  
  
-   カーソルよりも上にコード エラーがある場合  
  
     挿入ポイントの位置よりも上に不完全なステートメントや他のコーディング エラーがあると、IntelliSense は、コードの要素を解析できないので正しく機能しないことがあります。 IntelliSense を再び有効にするために、該当するコードをコメント化できます。  
  
-   コードのコメント内に挿入ポイントがある場合  
  
     挿入ポイントがソース ファイルのコメント内にある場合は、IntelliSense オプションを使用できません。  
  
-   文字列リテラル内に挿入ポイントがある場合  
  
     挿入ポイントが引用符で囲んだ文字列リテラル内にある場合は、IntelliSense オプションを使用できません。以下はその例です。  
  
     `WHERE FirstName LIKE 'Patri%|'`  
  
-   自動オプションがオフになっている場合  
  
     既定では、IntelliSense の多くの機能が自動的に実行されるようになっていますが、各機能を無効にすることもできます。  
  
     自動入力候補機能を無効にしている場合でも、IntelliSense 機能を使用することは可能です。 詳細については、「[IntelliSense の構成 &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/configure-intellisense-sql-server-management-studio.md)」を参照してください。  
  
## <a name="database-engine-query-intellisense"></a>データベース エンジン クエリの IntelliSense  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] クエリ エディターに関しては、次の点に注意してください。  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターの IntelliSense 機能では、すべての [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文要素がサポートされているわけではありません。 パラメーターのヘルプでは、拡張ストアド プロシージャなど、一部のオブジェクトのパラメーターがサポートされていません。 詳細については、「 [IntelliSense でサポートされている Transact-SQL 構文](../../relational-databases/scripting/transact-sql-syntax-supported-by-intellisense.md)」を参照してください。  
  
-   IntelliSense は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のクエリ エディターが [!INCLUDE[ssDE](../../includes/ssde-md.md)] 以降の [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] のインスタンスに接続されている場合にのみ使用できます。 Intellisense は、クエリ エディターが以前のバージョンの [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続されているときは使用できません。  
  
-   SQLCMD モードを有効にすると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターの IntelliSense が無効になります。  
  
-   IntelliSense 機能は、現在のエディター ウィンドウがデータベースに接続された後に別の接続で作成されたデータベース オブジェクトには対応していません。 入力候補一覧などの IntelliSense 機能からオブジェクトが欠落している場合、エディター ウィンドウのオブジェクトのキャッシュを更新するには、次の 3 つのメカニズムのいずれかを選択します。  
  
    -   **[編集]** メニューの **[IntelliSense]**をポイントし、 **[ローカル キャッシュの更新]**をクリックします。  
  
    -   Ctrl キーと Shift キーを押しながら R キーを押します。  
  
    -   現在のエディター ウィンドウを [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスから切断して再接続します。  
  
-   権限のないデータベース オブジェクトは入力候補一覧に表示されません。 IntelliSense は、権限のあるオブジェクトへの参照にフラグを付けます。 たとえば、別のユーザーが記述したスクリプトを開いた場合、そのユーザーには権限があるものの自分には権限のないオブジェクトへの参照には無効のフラグが付けられます。  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスへの接続が失われると、入力候補一覧が機能しなくなることがあります。 インスタンスに再接続してください。  
  
  