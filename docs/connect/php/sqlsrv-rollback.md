---
title: sqlsrv_rollback |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_rollback
apitype: NA
helpviewer_keywords:
- transaction support
- API Reference, sqlsrv_rollback
- sqlsrv_rollback
ms.assetid: 6e6bac39-45af-428c-bc32-f773482562ee
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c8be6ead0f7da39718ab77ec98af3bcfbcad041
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35309471"
---
# <a name="sqlsrvrollback"></a>sqlsrv_rollback
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

指定した接続で現在のトランザクションをロールバックし、接続を自動コミット モードに戻します。 現在のトランザクションには、 [sqlsrv_begin_transaction](../../connect/php/sqlsrv-begin-transaction.md) の呼び出しの後、 **sqlsrv_rollback** または [sqlsrv_commit](../../connect/php/sqlsrv-commit.md)の呼び出しの前に指定した接続で実行されたすべてのステートメントが含まれています。  
  
> [!NOTE]  
> [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]既定で自動コミット モードにします。 これは、すべてのクエリは、 **sqlsrv_begin_transaction**を使用してトランザクションを開始します。  
  
> [!NOTE]  
> 場合**sqlsrv_rollback**を使用して開始されたアクティブなトランザクションに含まれていない接続で呼び出される**sqlsrv_begin_transaction**、呼び出しから戻る**false**および*Not in Transaction*エラーがエラー コレクションに追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_rollback( resource $conn)  
```  
  
#### <a name="parameters"></a>パラメーター  
*$conn*: トランザクションがアクティブな接続です。  
  
## <a name="return-value"></a>戻り値  
ブール値: トランザクションが正常にロールバックされた場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="example"></a>例  
次の例では、トランザクションの一部として 2 つのクエリを実行します。 両方のクエリが成功すると、トランザクションはコミットされます。 いずれか (または両方) のクエリが失敗した場合、トランザクションはロールバックされます。  
  
この例の最初のクエリは、新しい販売注文を AdventureWorks データベースの *Sales.SalesOrderDetail* テーブルに挿入します。 これは、製品 ID 709 の製品 5 つに対する注文です。 2 番目のクエリは、製品 ID 709 の在庫量を 5 つ分減らします。 これらのクエリはどちらも、データベースに注文および製品の可用性の状態を正確に反映する目的で成功する必要があるため、トランザクションに含まれています。  
  
例では、SQL Server および[AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works)データベースがローカル コンピューターにインストールされています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true ));  
}  
  
/* Initiate transaction. */  
/* Exit script if transaction cannot be initiated. */  
if ( sqlsrv_begin_transaction( $conn) === false )  
{  
     echo "Could not begin transaction.\n";  
     die( print_r( sqlsrv_errors(), true ));  
}  
  
/* Initialize parameter values. */  
$orderId = 43659; $qty = 5; $productId = 709;  
$offerId = 1; $price = 5.70;  
  
/* Set up and execute the first query. */  
$tsql1 = "INSERT INTO Sales.SalesOrderDetail   
                     (SalesOrderID,   
                      OrderQty,   
                      ProductID,   
                      SpecialOfferID,   
                      UnitPrice)  
          VALUES (?, ?, ?, ?, ?)";  
$params1 = array( $orderId, $qty, $productId, $offerId, $price);  
$stmt1 = sqlsrv_query( $conn, $tsql1, $params1 );  
  
/* Set up and executee the second query. */  
$tsql2 = "UPDATE Production.ProductInventory   
          SET Quantity = (Quantity - ?)   
          WHERE ProductID = ?";  
$params2 = array($qty, $productId);  
$stmt2 = sqlsrv_query( $conn, $tsql2, $params2 );  
  
/* If both queries were successful, commit the transaction. */  
/* Otherwise, rollback the transaction. */  
if( $stmt1 && $stmt2 )  
{  
     sqlsrv_commit( $conn );  
     echo "Transaction was committed.\n";  
}  
else  
{  
     sqlsrv_rollback( $conn );  
     echo "Transaction was rolled back.\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_close( $conn);  
?>  
```  
  
トランザクションの動作を重視するため、いくつかの推奨されるエラー処理は前の例には含まれていません。 実稼働アプリケーションでは、 **sqlsrv** 関数のすべての呼び出しは、エラーを確認し、それに応じて処理することをお勧めします。  
  
> [!NOTE]  
> トランザクションの実行に、埋め込みの Transact SQL を使用しないでください。 たとえば、トランザクションを開始するために、"BEGIN TRANSACTION" を Transact-SQL クエリとして使用してステートメントを実行しないでください。 埋め込みの Transact SQL を使用してトランザクションを実行するときに、必要なトランザクションの動作は保証できません。  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)

[方法: トランザクションを実行する](../../connect/php/how-to-perform-transactions.md)

[Microsoft Drivers for PHP for SQL Server の概要](../../connect/php/overview-of-the-php-sql-driver.md) 
  
