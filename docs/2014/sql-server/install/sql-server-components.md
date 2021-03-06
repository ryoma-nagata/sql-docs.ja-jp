---
title: SQL Server コンポーネント |Microsoft Docs
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
- SQL Server Upgrade Advisor, components
- listing components to analyze
- Upgrade Advisor [SQL Server], components
- component analysis [Upgrade Advisor]
- finding components to analyze
- locating components to analyze
- detecting components to analyze
- server names [Upgrade Advisor]
- analyzing system [Upgrade Advisor], component list
- identifying components to analyze
ms.assetid: 539b9525-ce3f-4950-9146-5527a5a297ee
caps.latest.revision: 41
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 99998b5b9e24de92f826a73941bf6b86e5ad4318
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177125"
---
# <a name="sql-server-components"></a>SQL Server のコンポーネント
  アップグレード アドバイザー分析ウィザードを実行するにを持つローカルまたはリモート コンピューターに対して[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、または[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]インストールされています。 アップグレード前の分析における最初の手順は、分析対象のコンピューターとコンポーネントを特定することです。  
  
## <a name="options"></a>および  
 **コンピューター名**  
 分析するコンピューターの名前を指定します。 アップグレード アドバイザーの設定、**サーバー名**ボックスに、ローカル コンピューターの名前。 ローカル コンピューターに接続する場合は、"." および "localhost" も使用できます。  
  
 別のコンピューターを分析するには、次のガイドラインに従ってください。  
  
-   クラスター化されていないインスタンスをスキャンするには、コンピューター名を入力します。  
  
-   クラスター化されたインスタンスをスキャンするには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスの名前を入力します。  
  
-   クラスターのノードにインストールされているクラスター化されていないコンポーネントをスキャンするには、フェールオーバー クラスター ノードのコンピューター名を入力します。  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス名は含めないでください。  
  
 コンピューター名を指定する代わりに、IP アドレスを指定できます。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をスキャンする場合、ローカル サーバーの名前を指定する必要があります。 アップグレード アドバイザーでは、ローカル レポート サーバーだけがスキャンされます。  
  
 **検出**  
 **検出**ボタンは、指定したコンピューターにアクセスして、分析するコンポーネントを検出します。  
  
-   リモート コンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを分析する場合は、リモート コンピューター上でリモート レジストリ サービスを有効にする必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のインスタンスがコンピューターのレジストリで見つかった場合に検出されます。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスがコンピューターのレジストリで見つかった場合に検出されます。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がコンピューターのレジストリで見つかった場合に検出されます。 ただし、アップグレード アドバイザーでは、ローカル レポート サーバーだけがスキャンされます。  
  
 **コンポーネント**  
 分析するコンポーネントを選択します。 クリックすることができます、**検出**コンピューターにインストールされているすべてのコンポーネントを選択するボタンをクリックします。 このコンピューターにインストールされていることが検出されたコンポーネントの横に、チェック マークが表示されます。 各コンポーネントの横にあるチェック ボックスをオンまたはオフにして、分析するコンポーネントを手動で選択することもできます。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [アップグレード アドバイザーのユーザー インターフェイス リファレンス](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
