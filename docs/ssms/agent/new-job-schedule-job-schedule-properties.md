---
title: '[新しいジョブ スケジュール] - [ジョブ スケジュールのプロパティ] | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.scheduleproperties.f1
- sql13.swb.maint.editrecurringjobsched.f1
ms.assetid: 5c0b1bc9-dd87-49cc-b0dd-75d0d922b177
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8ece6ac37eabdaa3a0c92035eda3ac880480fa6a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38000484"
---
# <a name="new-job-schedule---job-schedule-properties"></a>[新しいジョブ スケジュール] - [ジョブ スケジュールのプロパティ]
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> 
  [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このページを使用すると、スケジュールのプロパティを表示したり、変更したりできます。  
  
## <a name="options"></a>[変数]  
**名前**  
スケジュールの新しい名前を入力します。  
  
**[スケジュール済みのジョブ]**  
このスケジュールを使用するジョブを表示します。  
  
**[スケジュールの種類]**  
スケジュールの種類を選択します。  
  
**有効**  
スケジュールを有効または無効にします。  
  
## <a name="recurring-schedule-types-options"></a>定期スケジュールのオプション  
**[実行]**  
スケジュールが定期的に実行される間隔を選択します。  
  
**[間隔]**  
スケジュールを実行する間隔を日数または週数で選択します。 このオプションは、毎月実行のスケジュールでは使用できません。  
  
**月曜日**  
月曜日にジョブを実行するように設定します。 毎週実行のスケジュールでのみ選択できます。  
  
**火曜日**  
火曜日にジョブを実行するように設定します。 毎週実行のスケジュールでのみ選択できます。  
  
**水曜日**  
水曜日にジョブを実行するように設定します。 毎週実行のスケジュールでのみ選択できます。  
  
**木曜日**  
木曜日にジョブを実行するように設定します。 毎週実行のスケジュールでのみ選択できます。  
  
**金曜日**  
金曜日にジョブを実行するように設定します。 毎週実行のスケジュールでのみ選択できます。  
  
**土曜日**  
土曜日にジョブを実行するように設定します。 毎週実行のスケジュールでのみ選択できます。  
  
**日曜日**  
日曜日にジョブを実行するように設定します。 毎週実行のスケジュールでのみ選択できます。  
  
**日**  
スケジュールが発生する日を選択します。 毎月実行のスケジュールでのみ選択できます。  
  
**[間隔]**  
スケジュールを実行する間隔を月数で選択します。 毎月実行のスケジュールでのみ選択できます。  
  
**[曜日]**  
月の特定の週における特定の曜日をスケジュールに指定します。 毎月実行のスケジュールでのみ選択できます。  
  
**[1 回]**  
毎日実行するジョブの開始時刻を設定します。  
  
**[間隔]**  
ジョブの実行間隔を時間と分と秒の単位で設定します。  
  
**開始日**  
設定したスケジュールの適用開始日を指定します。  
  
**終了日**  
設定したスケジュールを適用する期間の最終日を指定します。  
  
**[終了日なし]**  
スケジュールを無期限に適用するように指定します。  
  
## <a name="one-time-schedule-types-options"></a>指定日時スケジュールのオプション  
**日付**  
ジョブを実行する日付を選択します。  
  
**[時刻]**  
ジョブを実行する時刻を選択します。  
  
## <a name="see-also"></a>参照  
[スケジュールの作成とジョブへのアタッチ](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[ジョブのスケジュール設定](../../ssms/agent/schedule-a-job.md)  
  
