---
title: レプリケーション ログ リーダー エージェント | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Log Reader Agent, executables
- Log Reader Agent, parameter reference
- agents [SQL Server replication], Log Reader Agent
- command prompt [SQL Server replication]
ms.assetid: 5487b645-d99b-454c-8bd2-aff470709a0e
caps.latest.revision: 50
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ff0ad36402857082e069a322e4519d64b13f7e65
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215342"
---
# <a name="replication-log-reader-agent"></a>レプリケーション ログ リーダー エージェント
  レプリケーション ログ リーダー エージェントは、トランザクション レプリケーション用に構成した各データベースのトランザクション ログを監視し、レプリケーションのマークが付けられたトランザクションをトランザクション ログからディストリビューション データベースにコピーする実行可能ファイルです。  
  
> [!NOTE]  
>  パラメーターは任意の順序で指定できます。 オプション パラメーターを指定しなかった場合、既定のエージェント プロファイルの定義済みの値が使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
      logread [-?]   
-Publisherserver_name[\instance_name]   
-PublisherDBpublisher_database   
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-ExtendedEventConfigFileconfiguration_path_and_file_name]  
[-HistoryVerboseLevel [0|1|2]]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-LogScanThresholdscan_threshold]  
[-MaxCmdsInTrannumber_of_commands]  
[-MessageIntervalmessage_interval]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2|3|4]]  
[-PacketSizepacket_size]  
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]   
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherSecurityMode [0|1]]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-QueryTimeOutquery_time_out_seconds]  
[-ReadBatchSizenumber_of_transactions]   
[-ReadBatchThresholdread_batch_threshold]  
[-RecoverFromDataErrors]  
```  
  
## <a name="arguments"></a>引数  
 **-?**  
 使用方法についての情報を表示します。  
  
 **-Publisher** *server_name*[**\\***instance_name*]  
 パブリッシャーの名前です。 サーバー上の *server_name* の既定のインスタンスの場合は、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。 サーバー上の *server_name***\\***instance_name* instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。  
  
 **-PublisherDB** *publisher_database*  
 パブリッシャー データベースの名前です。  
  
 **-Continuous**  
 エージェントがレプリケートされたトランザクションの呼び出しを継続的に試みるかどうかを指定します。 このパラメーターを指定する場合は、保留されているトランザクションがなくても、エージェントはポーリング間隔でレプリケートされたトランザクションをソースから呼び出します。  
  
 **-DefinitionFile** *def_path_and_file_name*  
 エージェント定義ファイルのパスです。 エージェント定義ファイルには、エージェントのコマンド ライン引数が含まれます。 ファイルの内容は実行可能ファイルとして解析されます。 二重引用符 (") を使用して、任意の文字を含む引数値を指定します。  
  
 **-Distributor** *server_name*[**\\***instance_name*]  
 ディストリビューターの名前です。 サーバー上の *の既定のインスタンスの場合は、* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。 サーバー上の *server_name***\\***instance_name* instance_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。  
  
 **-DistributorLogin** *distributor_login*  
 ディストリビューターのログイン名です。  
  
 **-DistributorPassword** *distributor_password*  
 ディストリビューターのパスワードです。  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 ディストリビューターのセキュリティ モードを指定します。 **0** の値は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定値) を示し、 **1** の値は [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 認証モードを示します。  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 ログ リーダー エージェントが接続を行うときに使用する SSL (Secure Sockets Layer) 暗号化レベルです。  
  
|EncryptionLevel の値|説明|  
|---------------------------|-----------------|  
|**0**|SSL は使用されません。|  
|**1**|SSL は使用されますが、信頼できる発行者によって SSL サーバー証明が署名されているかどうかを検証しません。|  
|**2**|SSL が使用され、証明書の確認が行われます。|  
  
 詳細については、「[Security Overview &#40;Replication&#41;](../security/security-overview-replication.md)」(セキュリティの概要 (レプリケーション)) を参照してください。  
  
 **-ExtendedEventConfigFile** *configuration_path_and_file_name*  
 拡張イベントの XML 構成ファイルのパスとファイル名を指定します。 拡張イベントの構成ファイルによって、追跡に必要なセッションを構成し、イベントを有効にすることができます。  
  
 **-HistoryVerboseLevel** [ **0**| **1**| **2**]  
 ログ リーダー操作中にログに記録する履歴の量を指定します。 **1**を選択すれば、ログへの履歴の記録がパフォーマンスに与える影響を最小限に抑えることができます。  
  
|HistoryVerboseLevel の値|説明|  
|-------------------------------|-----------------|  
|**0**||  
|**1**|既定値です。 同じ状態 (startup、progress、success など) を示している以前の履歴メッセージを常に更新します。 前回の記録に同じ状態がない場合は、新しい記録を挿入します。|  
|**2**|アイドル状態や長時間実行を示すメッセージでない場合、新しい履歴レコードを挿入します。アイドル状態などを示すメッセージの場合には、以前のレコードを更新します。|  
  
 **-KeepAliveMessageInterval** *keep_alive_message_interval_seconds*  
 既存の接続がサーバーからの応答を待機しているかどうかを、履歴スレッドがチェックするまでの秒数です。 長時間実行のときに、照合エージェントによってログ リーダー エージェントに SUSPECT とマークされないようにするには、この値を小さくします。 既定では 300 秒です。  
  
 **-LoginTimeOut** *login_time_out_seconds*  
 ログインがタイムアウトになるまでの秒数です。既定値は 15 秒です。  
  
 **-LogScanThreshold** *scan_threshold*  
 内部使用のみです。  
  
 **-MaxCmdsInTran** *number_of_commands*  
 ログ リーダーがディストリビューション データベースにコマンドを書き込む際に、トランザクションにグループ化されるステートメントの最大数を指定します。 このパラメーターを使用すると、ログ リーダー エージェントおよびディストリビューション エージェントは、サブスクライバーでコマンドを適用するときに、パブリッシャーで (多数のコマンドで構成される) 大きなトランザクションを複数の小さなトランザクションに分割できます。 このパラメーターを指定すると、ディストリビューターでの競合を減らし、パブリッシャーとサブスクライバーの間の待機時間を減らすことができます。 元のトランザクションはより小さな単位で適用されるため、サブスクライバーは元のトランザクションが終了する前に、大きな論理パブリッシャー トランザクションの行にアクセスし、トランザクションの厳密な原子性を損なうことがあります。 既定値は **0**です。この場合、パブリッシャーのトランザクション境界が保護されます。  
  
> [!NOTE]  
>  このパラメーターは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリケーション以外では無視されます。 詳細については、「 [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md)」の「トランザクション セット ジョブの構成」を参照してください。  
  
 **-MessageInterval** *message_interval*  
 履歴をログに記録する間隔です。 最後の履歴イベントがログに記録された後で **MessageInterval** 値に到達すると、次の履歴イベントがログに記録されます。  
  
 ソースに利用可能なレプリケートされたトランザクションがない場合、エージェントはディストリビューターに対してトランザクションなしのメッセージを報告します。 このオプションは、エージェントが次にトランザクションなしのメッセージを報告するまでの待ち時間を指定します。 前回レプリケートされたトランザクションを処理した後で、ソースに利用可能なトランザクションがないことを検出すると、エージェントは必ずトランザクションなしのメッセージを報告します。 既定値は 60 秒です。  
  
 **-Output** *output_path_and_file_name*  
 エージェントの出力ファイルのパスです。 ファイル名が指定されていない場合、出力はコンソールに送られます。 指定された名前のファイルが存在する場合、出力はそのファイルに追加されます。  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2** | **3** | **4** ]  
 出力を詳細表示にするかどうかを指定します。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|エラー メッセージのみが記録されます。|  
|**1**|すべてのエージェント進行状況レポート メッセージが出力されます。|  
|**2** (既定値)|すべてのエラー メッセージおよびエージェント進行状況レポート メッセージが出力されます。|  
|**3**|レプリケートされた各コマンドの最初の 100 バイトが出力されます。|  
|**4**|すべてのレプリケートされたコマンドが出力されます。|  
  
 値 2 ～ 4 はデバッグ時に有用です。  
  
 **-PacketSize** *packet_size*  
 パケット サイズをバイト単位で指定します。 既定値は 4096 (バイト) です。  
  
 **-PollingInterval** *polling_interval*  
 ログを対象としてレプリケートされたトランザクションをクエリする間隔を表す秒単位の値です。 既定値は 5 秒です。  
  
 **-ProfileName** *profile_name*  
 エージェント パラメーターに使用するエージェント プロファイルを指定します。 **ProfileName** が NULL の場合、このエージェント プロファイルは無効になります。 **ProfileName** を指定しない場合、エージェントの種類に応じた既定のプロファイルが使われます。 詳細については、「[レプリケーション エージェント プロファイル](replication-agent-profiles.md)」を参照してください。  
  
 **-PublisherFailoverPartner** *server_name*[**\\***instance_name*]  
 パブリケーション データベースとのデータベース ミラーリング セッションに参加する、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー パートナー インスタンスを指定します。 詳細については、「 [データベース ミラーリングとレプリケーション &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)」をご覧ください。  
  
 **-PublisherSecurityMode** [ **0**| **1**]  
 パブリッシャーのセキュリティ モードを指定します。 値 **0** は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証モード (既定値) を示し、値 **1** は Windows 認証モードを示します。  
  
 **-PublisherLogin** *publisher_login*  
 パブリッシャーのログイン名です。  
  
 **-PublisherPassword** *publisher_password*  
 パブリッシャーのパスワードです。  
  
 **-QueryTimeOut** *query_time_out_seconds*  
 クエリがタイムアウトになるまでの秒数です。既定値は 1800 秒です。  
  
 **-ReadBatchSize** *number_of_transactions*  
 パブリッシング データベースのトランザクション ログから読み取られるトランザクションの処理サイクルあたりの最大数であり、既定値は 500 です。 エージェントは、すべてのトランザクションをログから読み取るまで、トランザクションの読み取りをバッチ処理で継続します。 このパラメーターは、Oracle パブリッシャーに対してサポートされていません。  
  
 **-ReadBatchThreshold** *number_of_commands*  
 ディストリビューション エージェントによってサブスクライバーに発行される前に、トランザクション ログから読み取られるレプリケーション コマンドの数です。 既定値は 0 です。 このパラメーターが指定されていない場合、ログ リーダー エージェントは、ログの最後まで読み取るか、または **-ReadBatchSize** (トランザクション数) で指定された数だけ読み取ります。  
  
 **-RecoverFromDataErrors**  
 SQL Server 以外のパブリッシャーからパブリッシュされる列データでエラーが発生しても、ログ リーダー エージェントを継続して実行することを指定します。 既定では、このようなエラーが発生するとログ リーダー エージェントは失敗します。 **-RecoverFromDataErrors**を使用する場合、エラーのある列データは NULL または適切な NULL 以外の値としてレプリケートされ、警告メッセージが [MSlogreader_history](/sql/relational-databases/system-tables/mslogreader-history-transact-sql) テーブルに記録されます。 このパラメーターは、Oracle パブリッシャーに対してのみサポートされます。  
  
## <a name="remarks"></a>コメント  
  
> [!IMPORTANT]  
>  ドメイン ユーザー アカウント (既定値) ではなくローカル システム アカウントで実行するように [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントをインストールした場合、サービスはローカル コンピューターにのみアクセスできます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントから実行されるログ リーダー エージェントで、Windows 認証モードを使用するように構成すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]へのログイン時にログ リーダー エージェントは異常終了します。 既定の設定は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証です。 セキュリティ アカウント変更の詳細については、「 [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md)」を参照してください。  
  
 ログ リーダー エージェントを開始するには、コマンド プロンプトから **logread.exe** を実行します。 詳細については、「[レプリケーション エージェント実行可能ファイルの概念](../concepts/replication-agent-executables-concepts.md)」を参照してください。  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|**-ExtendedEventConfigFile** パラメーターを追加しました。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェントの管理](replication-agent-administration.md)  
  
  
