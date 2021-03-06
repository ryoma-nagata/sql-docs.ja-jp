---
title: optimize for ad hoc workloads サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- optimize for ad hoc workloads option
ms.assetid: 0972e028-3a8e-454b-a186-e814a1d431f2
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: deb22ba7681910d47483054fc43d38baf9ecae0d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293152"
---
# <a name="optimize-for-ad-hoc-workloads-server-configuration-option"></a>optimize for ad hoc workloads サーバー構成オプション
  **optimize for ad hoc workloads** オプションを使用すると、1 回のみ使用するアドホック バッチが多数含まれているワークロードのプラン キャッシュの効率を高めることができます。 このオプションを 1 に設定すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] では、バッチが初めてコンパイルされるときに、完全なコンパイル済みプランではなく、コンパイル済みプランの小さいスタブをプラン キャッシュに格納します。 これにより、再利用されないコンパイル済みプランでプラン キャッシュがいっぱいにならないようにして、メモリの負荷を下げることができます。  
  
 コンパイル済みプランのスタブを使用すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、このアドホック バッチが既にコンパイルされているが、コンパイル済みプランのスタブしか格納していないと認識します。そのため、このバッチが再度呼び出される (コンパイルまたは実行される) と、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] では、バッチがコンパイルされ、コンパイル済みプランのスタブがプラン キャッシュから削除され、完全なコンパイル済みプランがプラン キャッシュに追加されます。  
  
 **optimize for ad hoc workloads** を 1 に設定すると、新しいプランのみに影響します。プラン キャッシュ内の既存のプランには影響しません。  
  
 コンパイル済みプランのスタブは、sys.dm_exec_cached_plans カタログ ビューによって表示される cacheobjtype の 1 つです。 これには、一意の SQL ハンドルとプラン ハンドルが含まれています。 コンパイル済みプランのスタブには、関連付けられた実行プランがないため、プラン ハンドルに対してクエリを実行しても、XML プラン表示は返されません。  
  
 トレース フラグ 8032 は、キャッシュ制限パラメーターを [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] RTM の設定に戻します。これにより、一般に、より大きいキャッシュに対応できるようになります。 この設定は、頻繁に再利用されるキャッシュ エントリがキャッシュに収まらない場合や、サーバー構成オプション *[アドホック ワークロードの最適化]* でプラン キャッシュの問題を解決できない場合に使用します。  
  
> [!WARNING]  
>  トレース フラグ 8032 を使用した場合、キャッシュが大きいために他のメモリ コンシューマー (バッファー プールなど) で利用できるメモリが少なくなると、パフォーマンスが低下することがあります。  
  
## <a name="see-also"></a>参照  
 [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql)   
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
