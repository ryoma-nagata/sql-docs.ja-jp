---
title: SQL Server 管理ツールのアップグレード | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- management tools, upgrading
ms.assetid: 1dab50b9-d16c-49a1-9ecc-af72adb6c378
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2895efa338745f8935674ff42620c1f8d6272652
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289424"
---
# <a name="upgrade-sql-server-management-tools"></a>SQL Server 管理ツールのアップグレード
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降からのアップグレードがサポートされています。 このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理ツールと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント、データベース メール、メンテナンス プラン、XPStar、XPWeb などの管理コンポーネントのアップグレードのサポートおよび動作について説明します。  
  
> [!IMPORTANT]  
>  ローカルでのインストールの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップをリモート共有から実行する場合は、リモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。  
  
## <a name="known-upgrade-issues"></a>アップグレードに関する既知の問題  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にアップグレードする前に、以下の問題点を考慮してください。  
  
### <a name="for-all-upgrade-scenarios"></a>すべてのアップグレード シナリオに共通  
  
-   MSX サーバーをアップグレードする前に、すべての TSX サーバーをアップグレードする必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の MSX と TSX の詳細については、「 [エンタープライズ全体の管理の自動化](../../ssms/agent/automated-administration-across-an-enterprise.md)」を参照してください。  
  
-   1 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのコンポーネントはすべて同時にアップグレードする必要があります。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントのバージョン番号は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインスタンス内で同一であることが必要です。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] へのアップグレード時に、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の既存のインストールにコンポーネントを追加できます。 詳細については、次を参照してください。[インストール ウィザードを SQL Server 2014 を使用するアップグレード&#40;セットアップ&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] チューニング アドバイザー、sqlcmd、osql などの  クライアント ツールは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にアップグレードされません。 代わりに、クライアント ツールは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のツールとサイド バイ サイドで実行されます。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアント ツールから設定をインポートできます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への認証は、アップグレード時に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証から Windows 認証に更新されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ではサポートされません。  
  
-   ジョブや警告のデータは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]へのアップグレード時にも保持されます。  
  
-   アップグレード対象のインスタンスで SQL Mail が使用されている場合、関連する XPs はアップグレード後もサポートされ、有効になります。 SQL Mail が使用されていない場合、XPs はオフになります。  
  
-   SQLiMail とも呼ばれるデータベース メールは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]コンポーネントと共にアップグレードされます。 既定では、データベース メールは後からアップグレードされます。 スキーマの更新は、アップグレード後に更新スクリプトを使用して調整する必要があります。  
  
## <a name="see-also"></a>参照  
 [サポートされているバージョンとエディションのアップグレード](supported-version-and-edition-upgrades.md)   
 [旧バージョンとの互換性](../../getting-started/backward-compatibility.md)   
 [アップグレードする SQL Server 2014 のインストール ウィザードを使用して&#40;セットアップ&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
