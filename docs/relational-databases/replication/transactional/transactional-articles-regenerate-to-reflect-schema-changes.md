---
title: カスタム トランザクション プロシージャの再生成によるスキーマ変更の反映 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- custom procedures [SQL Server replication]
- transactional replication, replicating schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: ccf68a13-e748-4455-8168-90e6d2868098
caps.latest.revision: 29
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e1d588dc1634c240951dec79251f520b76360ac0
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37359244"
---
# <a name="transactional-articles---regenerate-to-reflect-schema-changes"></a>トランザクション アーティクル - 再生成によるスキーマ変更の反映
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  既定では、トランザクション レプリケーションがサブスクライバー上のデータを変更する際、パブリケーション内の各テーブル アーティクルに対して内部プロシージャが生成したストアド プロシージャが必ず使われます。 3 つのプロシージャ (挿入、更新、削除用に 1 つずつ) はサブスクライバーにコピーされ、挿入、更新、削除がサブスクライバーにレプリケートされた時点で実行されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリッシャー上のテーブルでスキーマが変更されると、レプリケーションがスクリプト作成内部プロシージャの同じセットを呼び出すことで、これらのプロシージャが自動的に再生成され、新しいプロシージャと新しいスキーマが一致します (スキーマ変更のレプリケーションは、Oracle パブリッシャーではサポートされていません)。  
  
 カスタム プロシージャを指定して、1 つ以上の既定のプロシージャを置き換えることもできます。 スキーマ変更によってカスタム プロシージャが影響を受ける場合は、そのプロシージャを変更する必要があります。 たとえば、スキーマ変更によって削除される列をプロシージャが参照している場合には、その列への参照をプロシージャから削除する必要があります。 レプリケーションで新しいカスタム プロシージャをサブスクライバーに反映するには、2 つの方法があります。  
  
-   1 つ目のオプションは、カスタム スクリプト作成プロシージャを使用して、レプリケーションで使用する既定のプロシージャを置き換える方法です。  
  
    1.  [sp_addarticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) を実行する場合は、**@schema_option** 0x02 ビットが **true** であることを確認します。  
  
    2.  [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md) を実行し、**@type** パラメーターの値に 'insert'、'update'、または 'delete' を指定し、**@value** パラメーターにカスタム スクリプト作成プロシージャの名前を指定します。  
  
     次回にスキーマが変更されると、レプリケーションによってこのストアド プロシージャが呼び出され、新しくユーザーが定義したカスタム ストアド プロシージャの定義がスクリプト化されて、プロシージャが各サブスクライバーに反映されます。  
  
-   2 つ目のオプションは、新しいカスタム プロシージャの定義を含むスクリプトを使用する方法です。  
  
    1.  [sp_addarticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) を実行する際に、**@schema_option** 0x02 ビットに **false** を設定し、レプリケーションによってカスタム プロシージャがサブスクライバーで自動的に生成されないようにします。  
  
    2.  各スキーマ変更の前に、新しいスクリプト ファイルを作成し、[sp_register_custom_scripting &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md) を実行してスクリプトをレプリケーションに登録します。 **@type** パラメーターの値として 'custom_script' を指定し、**@value** パラメーターにパブリッシャー上のスクリプトのパスを指定します。  
  
     次回に関連スキーマが変更されると、各サブスクライバーでは、DDL コマンドと同じトランザクション内でこのスクリプトが実行されます。 スキーマ変更が完了すると、スクリプトの登録が解除されます。 以降のスキーマ変更でこのスクリプトを実行するには、スクリプトを再登録する必要があります。  
  
## <a name="see-also"></a>参照  
 [トランザクション アーティクルに変更を反映する方法の指定](../../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)   
 [パブリケーション データベースでのスキーマの変更](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  
