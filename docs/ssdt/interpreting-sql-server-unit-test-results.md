---
title: SQL Server の単体テストの結果の解釈 | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fde3c95b-2f68-483d-a197-0f7161b72fa3
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1709d7ca64eedf5e4f0dd170606082e7f99f3e31
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083864"
---
# <a name="interpreting-sql-server-unit-test-results"></a>SQL Server の単体テストの結果の解釈
SQL Server 単体テストを実行すると、テスト結果が自動的に生成されて、ディスクに保存され、**[テスト結果]** ウィンドウに概要が表示されます。 テストの実行を開始するとすぐに、**[テスト結果]** ウィンドウが表示され、テスト実行の進行状況が表示されます。 この表示には、実行中のテストと完了したテストが含まれます。  
  
テスト結果に関する詳細情報を表示するには、**[テスト結果]** ウィンドウでテスト結果をダブルクリックして、**[テスト結果の詳細]** ページを表示します。 テスト結果の詳細を表示するには、テスト結果をダブルクリックします。  
  
**[テスト結果]** ウィンドウの表示を変更する方法について詳しくは、「[方法: テスト ウィンドウで列を追加または削除する (Visual Studio 2010)](http://msdn.microsoft.com/library/ms182508(VS.100).aspx)」または「[方法: テスト ウィンドウで列を追加または削除する (Visual Studio 2012)](http://msdn.microsoft.com/library/ms182508.aspx)」をご覧ください。  
  
## <a name="storing-test-results"></a>テスト結果の保存  
単体テストの結果は、拡張子が .trx のファイルとしてハード ディスクに自動的に保存されます。 .trx ファイルは、テスト実行の詳細を含む XML ファイルです。 以前のテスト実行の .trx ファイルを読み込み、テスト実行の結果を確認したり、以前のテストを再実行したりできます。 詳しくは、「[方法: テストを再実行する (Visual Studio 2010)](http://msdn.microsoft.com/library/ms182472(VS.100).aspx)」をご覧ください。  
  
> [!NOTE]  
> リモートで単体テストを実行することはできません。  
  
Visual Studio Team Foundation Server チーム プロジェクトを使用して作業の管理を補助している場合は、操作ストアと呼ばれる SQL Server データベースにテスト データを発行することもできます。  
  
テスト結果の保存、再利用、およびチームでの共有の方法について詳しくは、「[方法: Visual Studio でテスト結果を保存して開く (Visual Studio 2010)](http://msdn.microsoft.com/library/ms404662(VS.100).aspx)」または「[方法: Visual Studio でテスト結果を保存して開く (Visual Studio 2012)](http://msdn.microsoft.com/library/ms404662.aspx)」をご覧ください。  
  
## <a name="see-also"></a>参照  
[SQL Server の単体テストの実行](../ssdt/running-sql-server-unit-tests.md)  
  
