---
title: setWorkstationID メソッド (SQLServerDataSource) |Microsoft ドキュメント
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
- SQLServerDataSource.setWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c1093615-90bf-4918-9f05-8abd765ffb03
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae8a5eeefcad88ae35c2ce4388d09b555a495a30
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845607"
---
# <a name="setworkstationid-method-sqlserverdatasource"></a>setWorkstationID メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データ ソースへの接続に使用されるコンピューター名、クライアントの名前を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setWorkstationID(java.lang.String workstationID)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *workstationID*  
  
 A**文字列**クライアント コンピューター名を格納しています。  
  
## <a name="remarks"></a>解説  
 workstationID は、クライアント コンピューターまたはワークステーションの名前です。 WorkstationID プロパティが設定されていない場合、既定値は InetAddress.getLocalHost().getHostName() メソッドを呼び出すことによって構築されます。 GetHostName が空白の値を返す場合は、getHostAddress().toString() メソッドが呼び出されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
