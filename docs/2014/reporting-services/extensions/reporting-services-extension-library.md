---
title: Reporting Services 拡張機能ライブラリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- namespaces [Reporting Services]
- Reporting Services, extending
- extensions [Reporting Services], library
- library [Reporting Services]
ms.assetid: e8eff470-64d6-41c3-b98b-5ec916c121c3
caps.latest.revision: 33
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ea7edf14017fc8f382705397ce5bd5763b7c02bf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246422"
---
# <a name="reporting-services-extension-library"></a>Reporting Services 拡張機能ライブラリ
  Reporting Services 拡張機能ライブラリは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に含まれているクラス、インターフェイス、および値の型のセットです。 このライブラリは、システムの機能にアクセスし、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] アプリケーションを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントを拡張するための土台となるように設計されています。  
  
## <a name="namespaces"></a>名前空間  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 拡張機能ライブラリには次の名前空間があります。  
  
 <xref:Microsoft.ReportingServices.DataProcessing>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のデータ処理機能を拡張するコンポーネントの構築に使用できるクラスとインターフェイスが含まれています。  
  
 <xref:Microsoft.ReportingServices.Interfaces>  
 カスタム通知を作成し、独自の配信拡張機能を通じてユーザーに送信したり、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のカスタム セキュリティ拡張機能を構築したりすることを可能にする、クラスとインターフェイスが含まれています。  
  
 `Microsoft.ReportingServices.ReportRendering`  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の表示機能を拡張できるクラスとインターフェイスが含まれています。 この名前空間のメンバーを <xref:Microsoft.ReportingServices.Interfaces> 名前空間のメンバーと共に使用することで、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] で使用する独自のカスタム表示拡張機能を作成できます。  
  
## <a name="see-also"></a>参照  
 [Reporting Services の拡張機能](reporting-services-extensions.md)  
  
  
