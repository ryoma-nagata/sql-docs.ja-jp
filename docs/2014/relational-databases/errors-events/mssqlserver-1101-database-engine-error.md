---
title: MSSQLSERVER_1101 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 1101 (Database Engine error)
ms.assetid: d63b67d5-59f5-4f77-904e-5ba67f2dd850
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1043e24d95731faafa4dcd074bd5a6bb2257c47a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413141"
---
# <a name="mssqlserver1101"></a>MSSQLSERVER_1101
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1101|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|NOALLOCPG|  
|メッセージ テキスト|データベース '%.*ls' の新しいページを割り当てられませんでした。ファイル グループ '%.\*ls' のディスク領域が不足しています。 ファイル グループ内のオブジェクトの削除、ファイル グループへの新しいファイルの追加、またはファイル グループの既存のファイルの自動拡張の設定のいずれかを行って、必要な領域を作成してください。|  
  
## <a name="explanation"></a>説明  
 ファイル グループでディスク領域が不足しています。  
  
## <a name="user-action"></a>ユーザーの操作  
 次の操作により、ファイル グループで領域を使用できるようになることがあります。  
  
-   AUTOGROW をオンにする。  
  
-   ファイル グループにファイルをさらに追加する。  
  
-   ファイル グループ内の不要なインデックスやテーブルを削除することにより、ディスク領域を解放する。  
  
  
