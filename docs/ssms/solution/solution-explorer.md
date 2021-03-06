---
title: ソリューション エクスプローラー | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-solutions
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], solutions
- projects [SQL Server Management Studio], about projects
- SQL Server Management Studio [SQL Server], projects
- solutions [SQL Server Management Studio], about solutions
- SQL Server Management Studio [SQL Server], items
- items [SQL Server]
ms.assetid: 0df09843-0d4f-4925-bc6c-99265035a0c1
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 02ac675f7dd209cb538e90142f6b9049068e2ad7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38045960"
---
# <a name="solution-explorer"></a>ソリューション エクスプローラー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] のソリューション エクスプローラー ペインには、データベースのスクリプト、クエリ、データ接続、ファイルなどの項目を管理するための "プロジェクト" と呼ばれるコンテナーが用意されています。 互いに関連する 1 つまたは複数のプロジェクトは、"ソリューション" と呼ばれるコンテナーにまとめることができます。  
  
ソリューションには、1 つ以上のプロジェクトと、ソリューションを全体として定義するためのファイルおよびメタデータが含まれています。 プロジェクトとは、一式のファイルに、接続情報などの関連メタデータを加えたもののことです。 ソリューションおよびプロジェクトには項目が含まれています。項目とは、データベース ソリューションの作成に必要なスクリプト、クエリ、接続情報、およびファイルを表しています。  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid_md.md)]  
  
## <a name="benefits-of-using-solutions"></a>ソリューションを使用する利点  
これらのコンテナーの用途は次のとおりです。  
  
-   クエリおよびスクリプトに対するソース管理を実現します。  
  
-   ソリューション全体の設定や個別のプロジェクトの設定を管理します。  
  
-   データベース ソリューションを構成する項目に注目しながらファイル管理の詳細を扱います。  
  
-   各プロジェクト内の項目を参照することなく、役立つ項目をソリューション内の複数のプロジェクトへ、あるいはソリューションへ追加します。  
  
-   ソリューションまたはプロジェクトに属さないその他のファイルも作業できます。  
  
プロジェクトに含まれる項目は、プロジェクトの種類と、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]を使用しているかどうかによって異なります。  
  
## <a name="related-tasks"></a>Related Tasks  
SQL Server のソリューションの基礎知識については、次の各トピックを参照してください。  
  
|||  
|-|-|  
|**[説明]**|**トピック**|  
|ソリューション内の 1 つまたは複数のプロジェクトを収集する方法について説明します。|[ソリューション (SQL Server Management Studio)](../../ssms/solution/solutions-sql-server-management-studio.md)|  
|プロジェクトを作成し、スクリプトや接続などの項目を追加する方法について説明します。|[プロジェクト (SQL Server Management Studio)](../../ssms/solution/projects-sql-server-management-studio.md)|  
|ソリューションおよびファイルを管理するために [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] によって使用されるファイルに関する情報を提供します。|[ソリューションとプロジェクトを管理するためのファイル](../../ssms/solution/files-that-manage-solutions-and-projects.md)|  
  
