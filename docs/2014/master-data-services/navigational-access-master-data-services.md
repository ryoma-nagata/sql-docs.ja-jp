---
title: ナビゲーション アクセス (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
caps.latest.revision: 4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: da85747e9fe4a35eb4e86bb0fa07f677b35ea5c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169079"
---
# <a name="navigational-access-master-data-services"></a>ナビゲーション アクセス (マスター データ サービス)
  ナビゲーション アクセスは、**[モデル]** タブで割り当てられるモデル オブジェクト セキュリティに適用されます。  
  
 ナビゲーション アクセスは、セキュリティを割り当てたレベルよりも高いレベルへのアクセスです。  
  
 この例では、権限がエンティティに割り当てられているため、ナビゲーション アクセスがモデル レベルで付与されます。  
  
 ![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
 **エンティティ**  
  
 エンティティ、リーフ メンバー、またはその統合メンバーに権限を割り当てた場合、ナビゲーション アクセスにより、すべてのメンバーの名前およびコードの読み取りまたは更新を実行できます。 また、モデル名を読み取ることもできます。  
  
 **Attributes**  
  
 属性に権限を割り当てた場合、ナビゲーション アクセスにより、エンティティのすべてのメンバーの名前およびコードの読み取りまたは更新を実行できます。 また、モデル名を読み取ることもできます。  
  
 **コレクション**  
  
 コレクションに権限を割り当てた場合、名前、コード、説明、および所有者 ID の読み取りまたは更新を実行できます。 また、モデル名を読み取ることもできます。  
  
## <a name="see-also"></a>参照  
 [権限の決定方法&#40;マスター データ サービス&#41;](how-permissions-are-determined-master-data-services.md)  
  
  
