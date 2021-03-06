---
title: システム バージョン管理されたテンポラル テーブルでシステム バージョン管理を停止する | Microsoft Docs
ms.custom: ''
ms.date: 10/11/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: dddd707e-bfb1-44ff-937b-a84c5e5d1a94
caps.latest.revision: 10
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4e29857b52e2845599ea35dda7b4bb39b6ec1bd2
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38044262"
---
# <a name="stopping-system-versioning-on-a-system-versioned-temporal-table"></a>システム バージョン管理されたテンポラル テーブルでシステム バージョン管理を停止する
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  一時的または永続的に、テンポラル テーブルでバージョン管理を停止する場合があります。   
その場合は、 **SYSTEM_VERSIONING** 句を **OFF**に設定します。  
  
## <a name="setting-systemversioning--off"></a>SYSTEM_VERSIONING = OFF を設定する  
 テンポラル テーブルで特定のメンテナンス操作を実行する場合、またはバージョン管理されたテーブルを今後必要としない場合は、システム バージョン管理を停止します。 この操作により、次の 2 つの独立したテーブルが得られます。  
  
-   期間が定義された現在のテーブル  
  
-   通常のテーブルとしての履歴テーブル  
  
### <a name="important-remarks"></a>重要な解説  
  
-   **SYSTEM_VERSIONING = OFF** を設定するか、または **SYSTEM_TIME** 期間を削除すると、データ損失が発生しません。  
  
-   **SYSTEM_VERSIONING = OFF** を設定し、 **SYSTEM_TIME** 期間を削除しない場合、システムでは挿入および更新操作ごとに期間列が引き続き更新されます。 現在のテーブルでの削除は永続的なものになります。  
  
-   期間列を完全に削除するには、 **SYSTEM_TIME** 期間を削除します。  
  
-   **SYSTEM_VERSIONING = OFF**を設定すると、十分な権限を持つすべてのユーザーが、履歴テーブルのスキーマおよび内容を変更したり、履歴テーブルを完全に削除したりできます。  
  
### <a name="permanently-remove-systemversioning"></a>SYSTEM_VERSIONING を完全に削除する  
 この例では、SYSTEM_VERSIONING を完全に削除し、期間列を完全に削除します。 期間の列の削除は省略可能です。  
  
```  
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);   
/*Optionally, DROP PERIOD if you want to revert temporal table to a non-temporal*/   
ALTER TABLE dbo.Department   
DROP PERIOD FOR SYSTEM_TIME;  
  
```  
  
### <a name="temporarily-remove-systemversioning"></a>SYSTEM_VERSIONING を一時的に削除する  
 次に、システム バージョン管理を **OFF**に設定する必要がある操作を示します。  
  
-   履歴から不要なデータを削除する (**DELETE** または **TRUNCATE**)  
  
-   バージョン管理を行わずに現在のテーブルからデータを削除する (**DELETE**、 **TRUNCATE**)  
  
-   現在のテーブルから **SWITCH OUT** をパーティション分割する  
  
-   現在のテーブルに **SWITCH IN** をパーティション分割する  
  
 この例では、特定のメンテナンス操作を実行できるように SYSTEM_VERSIONING を一時的に停止します。 テーブル メンテナンスの前提条件としてバージョン管理を一時的に停止する場合は、データの整合性を保つために、トランザクション内で行うことを強くお勧めします。  
  
```  
BEGIN TRAN   
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);   
TRUNCATE TABLE [History].[DepartmentHistory]   
WITH (PARTITIONS (1,2))   
ALTER TABLE dbo.Department SET    
(   
SYSTEM_VERSIONING = ON (HISTORY_TABLE = History.DepartmentHistory)   
);   
COMMIT ;  
  
```  
  
## <a name="see-also"></a>参照  
 [テンポラル テーブル](../../relational-databases/tables/temporal-tables.md)   
 [システム バージョン管理されたテンポラル テーブルの概要](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [システム バージョン管理されたテンポラル テーブルの履歴データの保有期間管理](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [メモリ最適化テーブルでのシステム バージョン管理されたテンポラル テーブル](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [システム バージョン管理されたテンポラル テーブルの作成](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)   
 [システム バージョン管理のテンポラル テーブルのデータの変更](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)   
 [システム バージョン管理されたテンポラル テーブルのデータのクエリ](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)   
 [システム バージョン管理されたテンポラル テーブルのスキーマを変更する](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)  
  
  
