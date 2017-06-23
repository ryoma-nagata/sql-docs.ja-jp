---
title: "配信拡張機能を実装する準備 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- interfaces [Reporting Services]
- delivery extensions [Reporting Services], implementing
ms.assetid: aee1608d-374f-4ad3-bc23-fe07fdaa52b7
caps.latest.revision: 34
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f560fa7b7947849d8f9d5d1072d692a0f28dca37
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="preparing-to-implement-a-delivery-extension"></a>配信拡張機能を実装する準備
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能を実装する前に、実装するインターフェイスを定義しておく必要があります。 最初に配信拡張機能の使用方法、配信拡張機能に必要な設定、およびレポート通知を配信するために実装が必要な特定の機能を決定する必要があります。  
  
 各 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能は、次の機能を提供する必要があります。  
  
-   <xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイスの実装。拡張機能とローカライズされた拡張機能名を表します。  
  
-   <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> の実装。レポート通知をエンド ユーザーに配信するために使用できる配信拡張機能を作成します。  
  
-   サブスクリプション用の特定のユーザー データを処理する機能。  
  
 各配信拡張機能は、次の機能を含むように強化することができます。  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ユーザー コントロールの実装。エンド ユーザーがレポート マネージャーを使用して、配信拡張機能を使用するレポート サブスクリプションを作成できます。  
  
 次の表では、配信拡張機能で使用できるインターフェイスとクラスについて説明します。  
  
|インターフェイスまたはクラス|Description|  
|------------------------|-----------------|  
|<xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイス|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の拡張機能を表します。|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> インターフェイス|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の配信拡張機能を表します。|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイス|配信拡張機能に必要なレポート サーバーに関する情報を含みます (使用可能な表示拡張機能の一覧など)。|  
|<xref:Microsoft.ReportingServices.Interfaces.Setting>クラス|拡張機能の設定を表します。|  
|<xref:Microsoft.ReportingServices.Interfaces.Notification>クラス|配信拡張機能がレポートの配信に使用するサブスクリプション情報を含みます。|  
|<xref:Microsoft.ReportingServices.Interfaces.Report>クラス|配信拡張機能によるユーザーへのレポート配信を可能にする、レポート固有の情報とメソッドを表します。|  
|<xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>クラス|表示拡張機能からの出力を表します。 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトには、表示拡張機能によって返されたストリームを処理するために、配信拡張機能に必要な関連付けられたファイルの名前と種類の情報を含みます。|  
|<xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイス|レポート マネージャーのユーザーから配信拡張機能固有のサブスクリプション情報を取得する方法を表すユーザー コントロール (電子メール アドレスやファイル共有ディレクトリへのパスなど)。|  
  
## <a name="see-also"></a>参照  
 [Reporting Services 拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementing a Delivery Extension](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  