---
title: 登録する完全なパスを使用して拡張ストアド プロシージャ DLL 名 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- registering DLL names
- extended stored procedures [SQL Server], registering
- DLL names [SQL Server]
- full path DLL name registration [SQL Server]
ms.assetid: f648d57c-af32-4c71-9882-47b6766f3c2b
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cf09e25eb1a07e7714969fb3838859586cf6d763
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303662"
---
# <a name="use-the-full-path-to-register-extended-stored-procedure-dll-names"></a>完全なパスを使用して、拡張ストアド プロシージャ DLL の名前を登録する
  DLL 名の完全なパスを使用せずに登録されていた拡張ストアド プロシージャは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で機能しない可能性があります。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 DLL 名の完全なパスを使用せずに登録されていた拡張ストアド プロシージャは、アップグレードした後に機能しない可能性があります。 アップグレード プロセス中に古い BINN ディレクトリが新しいパスに追加されないためです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって拡張ストアド プロシージャを見つけることができなくなる可能性があります。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードする前に、登録に完全なパス名を使用していない各拡張ストアド プロシージャに対して、次の手順を実行します。  
  
1.  sp_dropextendedproc を実行して、拡張ストアド プロシージャを削除します。  
  
2.  sp_addextendedproc を実行して、完全なパス名で拡張ストアド プロシージャを登録します。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
