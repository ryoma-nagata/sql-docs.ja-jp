---
title: Microsoft SQL Operations Studio (プレビュー) のダウンロードおよびインストール | Microsoft ドキュメント
description: Windows、macOS、そして Linux に対応する Microsoft SQL Operations Studio (プレビュー) のダウンロードおよびインストール
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 421b22fd1489561ff04a69e23ecac15d1d52be5a
ms.sourcegitcommit: d3432a37b23b61c37092daf7519b30fc42fc0538
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36270993"
---
# <a name="download-and-install-sql-operations-studio-preview"></a>SQL Operations Studio (プレビュー) のダウンロードおよびインストール

[!INCLUDE[name-sos](../includes/name-sos.md)] Windows、macOS、および Linux で動作します。

ダウンロードし、最新のリリースをインストール、*年 6 月のパブリック プレビュー*:

|プラットフォーム|ダウンロード|リリース日| バージョン |
|:---|:---|:---|:---|
|Windows|[インストーラー](https://go.microsoft.com/fwlink/?linkid=875602)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=875603)|2018 年 6 月 20日 |0.30.6|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=875604)|2018 年 6 月 20日 |0.30.6|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=875607)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=875606)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=875605)|2018 年 6 月 20日 |0.30.6|

最新のリリースに関する詳細は、次の [リリース ノート](release-notes.md) を参照してください。

## <a name="get-sql-operations-studio-preview-for-windows"></a>SQL Operations Studio (プレビュー) for Windows の取得

[!INCLUDE[name-sos](../includes/name-sos-short.md)]のこのリリースは標準的な Windows インストーラーと .zip を含んでいます。 

**インストーラー**

1. [Windows 用の [!INCLUDE[name-sos](../includes/name-sos-short.md)] インストーラー](https://go.microsoft.com/fwlink/?linkid=875602) ダウンロードして実行します。
1. [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]のアプリを開始します。


**.zip ファイル**

1. [[!INCLUDE[name-sos](../includes/name-sos-short.md)]for Windows .zip](https://go.microsoft.com/fwlink/?linkid=875603) をダウンロードします。
2. ダウンロードしたファイルを参照し、展開します。
3. `\sqlops-windows\sqlops.exe`を実行します。


## <a name="get-sql-operations-studio-preview-for-macos"></a>SQL Operations Studio (プレビュー) for MacOS の取得

1. [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] for macOS](https://go.microsoft.com/fwlink/?linkid=875604) をダウンロードします。
2. zip のコンテンツを展開するには、ダブルクリックします。
3. [!INCLUDE[name-sos](../includes/name-sos-short.md)] を *Launchpad* で有効にするため *sqlops.app* を *アプリケーション* フォルダーへドラッグします。


## <a name="get-sql-operations-studio-preview-for-linux"></a>SQL Operations Studio (プレビュー) for Linux の取得

1. ダウンロード[!INCLUDE[name-sos](../includes/name-sos-short.md)]for Linux のインストーラーまたは tar.gz アーカイブのいずれかを使用します。
    - [.deb](https://go.microsoft.com/fwlink/?linkid=875607)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=875606)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=875605)
1. ファイルを展開し、[!INCLUDE[name-sos](../includes/name-sos-short.md)] を起動するため、新しいターミナル ウィンドウを開いて次のコマンドを入力します。

   **Debian のインストール:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
   ```

   **rpm インストール:**
   ```bash
   cd ~
   yum install ./Downloads/sqlops-linux-<version string>.rpm

   sqlops
   ```

   **tar.gz インストール:**
   ```bash 
   cd ~ 
   cp ~/Downloads/sqlops-linux-<version string>.tar.gz ~ 
   tar -xvf ~/sqlops-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/sqlops-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   sqlops 
   ``` 

   > [!NOTE]
   > Debian、Redhat、および Ubuntu で、依存関係が見つからないことがあります。 これらの依存関係をインストールするために、Linux のバージョンに応じて、次のコマンドを使用してください。
   

   **Debian:** 
   ```bash
   sudo apt-get install libuwind8
   ```

   **Redhat:** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```


## <a name="uninstall-sql-operations-studio-preview"></a>SQL Operations Studio (プレビュー)</a> のアンインストール

Windows インストーラーを使用して[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]をインストールした場合、他の Windows アプリケーションの削除と同じ方法でアンインストールしてください。

.zip またはその他のアーカイブから [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] をインストールした場合、ファイルを削除してください。

## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム

[!INCLUDE[name-sos](../includes/name-sos-short.md)] は Windows、macOS、そして Linux で動作し、次のプラットフォームでサポートされています。

### <a name="windows"></a>Windows
- Windows 10 (64 ビット)
- Windows 8.1 (64 ビット)
- Windows 8 (64 ビット)
- Windows 7 (SP1) (64 ビット) - [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767) が必要です
- Windows Server 2016
- Windows Server 2012 R2 (64 ビット)
- Windows Server 2012 (64 ビット)
- Windows Server 2008 R2 (64 ビット)

### <a name="macos"></a>macOS
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="check-for-updates"></a>更新を確認する
最新の更新を確認するには、ウィンドウの左下にある歯車アイコンをクリックして **更新を確認する** をクリックしてください。

## <a name="next-steps"></a>次の手順

作業を開始する次のクイック スタートのいずれかを参照してください。
- [接続し、クエリの SQL Server](quickstart-sql-server.md)
- [接続し、Azure SQL データベースの照会](quickstart-sql-database.md)
- [接続し、Azure データ ウェアハウスのクエリ](quickstart-sql-dw.md)

投稿[!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Microsoft のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)と[使用状況データ収集](usage-data-collection.md)です。
