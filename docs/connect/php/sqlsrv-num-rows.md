---
title: sqlsrv_num_rows |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- API Reference, sqlsrv_num_rows
- sqlsrv_num_rows
ms.assetid: c832210e-bb2a-47b5-a505-160b02d1d95e
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 670d9b8f4e708fac264b8520a6a1ee6f183181a5
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35309011"
---
# <a name="sqlsrvnumrows"></a>sqlsrv_num_rows
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

結果セットの行数をレポートします。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_num_rows( resource $stmt )  
```  
  
#### <a name="parameters"></a>パラメーター  
*$stmt*: 行数を取得する結果セット。  
  
## <a name="return-value"></a>戻り値  
行数の計算中にエラーが発生した場合は**false** 。 それ以外の場合は、結果セットの行数をレポートします。  
  
## <a name="remarks"></a>コメント  
sqlsrv_num_rows がクライアント側、スタティック、またはキーセット カーソルが必要であり、戻ります**false**順方向カーソルまたは動的カーソルを使用する場合。 (順方向カーソルが既定値です。)カーソルの詳細については、次を参照してください。 [sqlsrv_query](../../connect/php/sqlsrv-query.md)と[カーソルの種類&#40;SQLSRV ドライバー&#41;](../../connect/php/cursor-types-sqlsrv-driver.md)です。  
  
## <a name="example"></a>例  
  
```  
<?php  
   $server = "server_name";  
   $conn = sqlsrv_connect( $server, array( 'Database' => 'Northwind' ) );  
  
   $stmt = sqlsrv_query( $conn, "select * from orders where CustomerID = 'VINET'" , array(), array( "Scrollable" => SQLSRV_CURSOR_KEYSET ));  
  
   $row_count = sqlsrv_num_rows( $stmt );  
  
   if ($row_count === false)  
      echo "\nerror\n";  
   else if ($row_count >=0)  
      echo "\n$row_count\n";  
?>  
```  
  
次の例では、複数の結果セットがある場合 (バッチ クエリ) は、クライアント側カーソルを使用した場合にのみ行数を取得できることを示します。  
  
```  
<?php  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
$tsql = "select * from HumanResources.Department";  
  
// Client-side cursor and batch statements  
$tsql = "select top 2 * from HumanResources.Employee;Select top 3 * from HumanResources.EmployeeAddress";  
  
// works  
$stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"buffered"));  
  
// fails  
// $stmt = sqlsrv_query($conn, $tsql);  
// $stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"forward"));  
// $stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"static"));  
// $stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"keyset"));  
// $stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"dynamic"));  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for first result set = $row_count\n";  
  
sqlsrv_next_result($stmt);  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for second result set = $row_count\n";  
?>  
```  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
  
