---
title: '[データベースの変更を確認] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.schema.databasechangesdetected
- vdtsql.chm:65543
- vdtsql.chm:65554
ms.assetid: 91f13086-371f-46a2-9f46-804c1415f3ed
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 958f892df463533138b722e16a61eeccd0e06b19
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244042"
---
# <a name="database-changes-detected-dialog-box-visual-database-tools"></a>[データベースの変更を確認] ダイアログ ボックス (Visual Database Tools)
  このダイアログは、データベース ダイアグラムまたは選択したテーブルを保存しようとしたときに、保存によって影響を受けるデータベース オブジェクトの一部がデータベースの最新の内容と異なる場合に表示されます。 このダイアログ ボックスに表示された変更を受け入れると、ダイアグラムに一致するようにデータベースが更新され、他のユーザーが加えた変更が上書きされます。  
  
> [!NOTE]  
>  テーブルやデータベース ダイアグラムに加えた変更を元に戻すことはできませんが、テーブルやダイアグラムを保存するまでは、変更はデータベースに保存されません。 **[いいえ]** を選択して、すべての開いているダイアグラムの変更を保存せずに閉じると、まだ保存していない変更を破棄できます。  
  
## <a name="options"></a>および  
 **[相違点の検出に関する警告]**  
 データベース ダイアグラムまたは選択したテーブルを次に保存しようとするときにこのダイアログ ボックスを表示するかどうかを指定します。 このチェック ボックスをオンにすると、データベースの最新の内容と異なるダイアグラムやテーブルを保存しようとするたびにダイアログ ボックスが表示されます。 オフにすると、ダイアログ ボックスが表示されなくなります。 既定では、このチェック ボックスはオンです。 このオプションをオフにした場合は、 **[オプション]** ダイアログ ボックスで再びオンにできます。  
  
 **はい**  
 一覧に表示されているすべての変更を適用してデータベースを更新します。  
  
 **[いいえ]**  
 保存操作を取り消します。  
  
> [!NOTE]  
>  データベースに一致するようにダイアグラムを最新表示するには、変更を保存せずにダイアグラムを閉じて、サーバー エクスプローラーでダイアグラムを右クリックし、[最新の情報に更新] をクリックして、ダイアグラムを再度開きます。  
  
 **[テキスト ファイルを保存]**  
 **[名前を付けて保存]** ダイアログ ボックスが表示され、データベースへの変更の一覧を保存するテキスト ファイルの場所を指定できます。  
  
## <a name="see-also"></a>参照  
 [データベースの変更のデータベース ダイアグラムへの反映&#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [マルチユーザー環境 (Visual Database Tools)](multiuser-environments-visual-database-tools.md)  
  
  
