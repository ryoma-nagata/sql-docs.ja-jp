---
title: setServerName メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 70920828-eda0-4064-be9f-c1e460db8f00
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8843d601229fc8db7e374857857841eb5e3fc52a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32844807"
---
# <a name="setservername-method-sqlserverdatasource"></a>setServerName メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  実行しているコンピューターの名前を設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setServerName(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *サーバー名*  
  
 A**文字列**サーバー名を格納しています。  
  
## <a name="remarks"></a>解説  
 サーバー名を実行しているターゲット コンピューターのホスト名[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。 ServerName プロパティが設定されていない場合[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)既定値は null を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
