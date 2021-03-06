---
title: レッスン 1 のダウンロードのサンプル データとスクリプトの埋め込み R (SQL Server Machine Learning) |Microsoft Docs
description: SQL Server に R を埋め込む方法を示すチュートリアルはストアド プロシージャと T-SQL 関数
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 74a60a95da4fb701f3862c36e35a4bada6ef933b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38030380"
---
# <a name="lesson-1-download-data-and-scripts"></a>レッスン 1: データとスクリプトをダウンロードします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server で R を使用する方法に関する SQL 開発者向けのチュートリアルの一部です。

この手順では、サンプル データセットをダウンロードします、[!INCLUDE[tsql](../../includes/tsql-md.md)]このチュートリアルで使用されるファイルのスクリプトを作成します。 データとスクリプト ファイルの両方が、GitHub で共有しますが、PowerShell スクリプトは独自のローカル ディレクトリにデータとスクリプト ファイルをダウンロードします。

## <a name="download-tutorial-files-from-github"></a>Github からのチュートリアル ファイルをダウンロードします。

1.  Windows PowerShell コマンド コンソールを開きます。
  
    保存先のディレクトリの作成や、指定した宛先へのファイルの書き込みに管理者特権が必要な場合、**[管理者として実行]** オプションを使用します。
  
2.  パラメーター *DestDir* の値を任意のローカル ディレクトリに変更し、次の PowerShell コマンドを実行します。  ここで使用した既定値は **TempRSQL**です。
  
    ```ps
    $source = ‘https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_SQL_Walkthrough.ps1’  
    $ps1_dest = “$pwd\Download_Scripts_SQL_Walkthrough.ps1”
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir ‘C:\tempRSQL’
    ```
  
    *DestDir* で指定したフォルダーが存在しない場合、PowerShell スクリプトによって作成されます。
  
    > [!TIP]
    > エラーが発生した場合は、このチュートリアルで使用するためのみに PowerShell スクリプトの実行ポリシーを、Bypass 引数を使用し、変更を現在のセッションにスコープして、一時的に **unrestricted** に設定できます。
    >   
    >````
    > Set\-ExecutionPolicy Bypass \-Scope Process
    >````
    > このコマンドを実行しても、構成は変更されません。
  
    インターネット接続によっては、ダウンロードに時間がかかる場合があります。
  
3.  すべてのファイルがダウンロードされると、  *DestDir*で指定したフォルダーが PowerShell スクリプトによって開かれます。 PowerShell コマンド プロンプトで次のコマンドを実行し、ダウンロードされたファイルを確認します。
  
    ```
    ls
    ```
  
    **結果:**
  
    ![PowerShell スクリプトによってダウンロードされたファイルの一覧](media/rsql-devtut-filelist.png "PowerShell スクリプトによってダウンロードされたファイルの一覧")
  
## <a name="next-lesson"></a>次のレッスン

[レッスン 2: PowerShell を使用して SQL server のデータをインポートします。](../r/sqldev-import-data-to-sql-server-using-powershell.md)

## <a name="previous-lesson"></a>前のレッスン

[SQL 開発者向けの埋め込みの R 分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)
