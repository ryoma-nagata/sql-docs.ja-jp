---
title: レポートのキャッシュ (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-server
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- cache [Reporting Services]
- cached reports [Reporting Services]
- schedules [Reporting Services], report expiration
- expiration [Reporting Services]
ms.assetid: 723d1cb0-c2e7-4763-8690-a6a7a8bbbb90
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 45d43330bae118628a50dec3f8f3ac47f2721e76
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33025019"
---
# <a name="cache-a-report-report-manager"></a>レポートのキャッシュ (レポート マネージャー)
  パフォーマンスを向上させる方法の 1 つに、レポートのキャッシュ プロパティを構成するという方法があります。 レポートをキャッシュに格納した場合、表示されたレポートのコピーが短時間、保存されます。 レポートを要求した 1 人目のユーザーは、すべての処理が完了しないとレポートを閲覧できませんが、 それ以降、同じレポートを要求したユーザーは、キャッシュの保持時間内であれば、処理が既に完了しているため、すぐにレポートを閲覧できます。  
  
 キャッシュできるレポートの種類には制限があります。 たとえば、レポート出力がユーザー ID によって異なる場合や、レポートを要求したユーザーのセキュリティ トークンを使ってデータが取得される場合、レポートをキャッシュすることはできません。 詳細については、「 [レポートのキャッシュ (SSRS)](../../reporting-services/report-server/caching-reports-ssrs.md)」を参照してください。  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a>キャッシュされたレポートの有効期限をスケジュールするには  
  
1.  [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896) を開始します。  
  
2.  レポート マネージャーで **[コンテンツ]** ページに移動します。 キャッシュ プロパティを設定するレポートに移動し、アイテムの上にマウス ポインターを移動して、下矢印をクリックします。  
  
3.  ドロップダウン メニューの **[管理]** をクリックします。  
  
4.  左フレームの **[処理オプション]** をクリックします。  
  
5.  このページで、 **[常に最新データを使用して、このレポートを実行する]** を選択します。  
  
6.  次の 2 つのキャッシュ オプションのいずれかを選択し、以下のように有効期限を構成します。  
  
    -   キャッシュされたコピーが、特定の期間が過ぎた後で有効期限が切れるように構成するには、**レポートの一時コピーをキャッシュします。レポートのコピーの有効期限は数分後に切れます** をクリックします。 レポートの有効期限を分単位で入力します。  
  
    -   キャッシュされたコピーが、スケジュールに基づいて有効期限が切れるように構成するには、**[レポートの一時コピーをキャッシュします。次のスケジュールでレポートのコピーの有効期限は切れます。]** をクリックします。 **[構成]** をクリックするか、レポートの有効期限を制御する共有スケジュールを選択します。  
  
7.  **[適用]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [レポート処理プロパティの設定](../../reporting-services/report-server/set-report-processing-properties.md)   
 [レポートのキャッシュ &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)  
  
  
