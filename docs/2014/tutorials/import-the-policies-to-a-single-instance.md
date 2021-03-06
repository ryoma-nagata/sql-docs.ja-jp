---
title: 1 つのインスタンスにポリシーのインポート |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: bc5bcd87-663f-41d9-bb7b-b3e083cd63df
caps.latest.revision: 8
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 4c45508880948c3ce1cb4814eca918278a66aacb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177149"
---
# <a name="import-the-policies-to-a-single-instance"></a>単一インスタンスへのポリシーのインポート
  ここでは、スケジュールするベスト プラクティス ポリシーを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の単一インスタンス上のポリシー ベースの管理にインポートします。  
  
## <a name="prerequisites"></a>前提条件  
 この手順は、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 以降のバージョンを実行しているサーバー上で実行する必要があります。  
  
### <a name="import-the-best-practices-policies-for-the-database-engine"></a>データベース エンジンのベスト プラクティス ポリシーのインポート  
  
1.  開始[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]に接続し、[!INCLUDE[ssDE](../includes/ssde-md.md)]します。  
  
2.  オブジェクト エクスプ ローラーで、**管理**、順に展開**ポリシーの管理**します。  
  
3.  右クリックして**ポリシー**、 をクリックし、**ポリシーのインポート**します。  
  
4.  **インポート** ダイアログ ボックスの横に、**ファイルをインポートする**ボックスで、省略記号ボタンをクリックします (**.**) ボタンをクリックします。  
  
5.  **ファイルの場所**一覧で、ベスト プラクティス ポリシーを格納している次のフォルダーに移動します。  
  
     **ある C:\Program Files (x86) \Microsoft SQL server \110\tools\policies\databaseengine\1033**  
  
    > [!NOTE]  
    >  ファイル パスは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プログラム ファイルのインストール先、32 ビットまたは 64 ビットのどちらのオペレーティング システムを実行しているか、および言語識別子によって異なることがあります。  
  
6.  **ポリシーの選択**ダイアログ ボックスで、1 つまたは複数のポリシー ファイルを選択します。  
  
     隣接していない複数のファイルを選択するには、ファイルをクリックし、Ctrl キーを押しながら他のファイルをそれぞれクリックします。 隣接する複数のファイルを選択するには、最初のファイルをクリックし、Shift キーを押しながら最後のファイルをクリックします。  
  
7.  ファイルの選択が完了したら、クリックして**オープン**します。  
  
8.  **インポート** ダイアログ ボックスで、ことを確認します、**ポリシーの状態**に設定されている一覧**インポート時にポリシーの状態を保持する**(既定)、順にクリックします**ok**.  
  
     ポリシーのインポート、**ポリシー**ノードの下**ポリシーの管理**します。 既定では、インポートされたポリシーは "要求時" 評価モードに設定されます。  
  
## <a name="next-steps"></a>次の手順  
 [ポリシーのスケジュール設定](../../2014/tutorials/schedule-the-policies.md)  
  
  
