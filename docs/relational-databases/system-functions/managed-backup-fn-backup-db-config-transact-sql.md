---
title: managed_backup.fn_backup_db_config (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- smart_admin.fn_backup_db_config
- smart_admin.fn_backup_db_config_TSQL
- fn_backup_db_config
- fn_backup_db_config_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_backup_db_config
- fn_backup_db_config
ms.assetid: 7c755d8a-64dd-44b2-be5e-735d30758900
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5c4e752c1d8c88a4b0f9dadc129213a6f2ac8951
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37978954"
---
# <a name="managedbackupfnbackupdbconfig-transact-sql"></a>managed_backup.fn_backup_db_config (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  0、1 つ以上の行を返す[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]構成設定。 指定されたデータベースに対して 1 行を返すか、インスタンス上で [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]によって構成されたすべてのデータベースの情報を返します。  
  
 このストアド プロシージャを使用すると、SQL Server のインスタンス上の特定のデータベースまたはすべてのデータベースの現在の [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の構成設定を確認または決定することができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
managed_backup.fn_backup_db_config (‘database_name’ | ‘’ | NULL)  
```  
  
##  <a name="Arguments"></a> 引数  
 @db_name  
 データベースの名前。 @db_nameパラメーターが**SYSNAME**します。 このパラメーターに空の文字列または NULL 値が渡されると、SQL Server のインスタンス上にあるすべてのデータベースに関する情報が返されます。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|db_name|SYSNAME|データベース名。|  
|db_guid|UNIQUEIDENTIFIER|データベースを一意に識別する識別子。|  
|is_availability_database|BIT|データベースが可用性グループに参加しているかどうか。 値が 1 の場合は、データベースが可用性データベースであることを示します。0 の場合は、可用性データベースではないことを示します。|  
|is_dropped|BIT|値が 1 の場合は、削除されたデータベースであることを示します。|  
|credential_name|SYSNAME|ストレージ アカウントへの認証に使用された SQL 資格情報の名前。 NULL 値は、SQL 資格情報が設定されていないことを示します。|  
|retention_days|INT|現在の保有期間 (日数)。 NULL 値が示す[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]このデータベース用に構成されたことはありません。|  
|is_managed_backup_enabled|INT|示すかどうか[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]このデータベースが現在有効です。 値 1 では、ことを示します[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]現在有効になって 0 の値と[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]はこのデータベースを無効になります。|  
|storage_url|NVARCHAR (1024)|ストレージ アカウントの URL。|  
|Encryption_algorithm|NCHAR (20) 型|バックアップを暗号化するときに使用する、現在の暗号化アルゴリズムを返します。|  
|Encryptor_type|NCHAR(15)|暗号化機能の設定 (証明書または非対称キー) を返します。|  
|Encryptor_name|NCHAR(max_length_of_cert/asymm_key_name)|証明書または非対称キーの名前。|  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **db_backupoperator**を持つデータベース ロール**ALTER ANY CREDENTIAL**アクセス許可。 ユーザーが拒否されていない必要があります**VIEW ANY DEFINITION**アクセス許可。  
  
## <a name="examples"></a>使用例  
 次の例では、"TestDB" の [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]の構成が返されます。  
  
 各コードでは、言語属性フィールドで "tsql" を選択します。  
  
```  
Use msdb  
GO  
SELECT * FROM managed_backup.fn_backup_db_config('TestDB')  
```  
  
 次の例を返します、[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]で実行される SQL Server のインスタンス上のすべてのデータベースに構成します。  
  
```  
Use msdb  
GO  
SELECT * FROM managed_backup.fn_backup_db_config (NULL)  
```  
  
  
