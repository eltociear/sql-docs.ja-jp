---
title: レプリケーション キュー リーダー エージェント | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], Queue Reader Agent
- command prompt [SQL Server replication]
- Queue Reader Agent, parameter reference
- Queue Reader Agent, executables
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d92a15ae855c5521319abd252b1f5a7efc2bf300
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63191657"
---
# <a name="replication-queue-reader-agent"></a>Replication Queue Reader Agent
  レプリケーションキューリーダーエージェントは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]キューまたは[!INCLUDE[msCoName](../../../includes/msconame-md.md)]メッセージキューに格納されているメッセージを読み取り、それらのメッセージをパブリッシャーに適用する実行可能ファイルです。 キュー リーダー エージェントは、スナップショット、およびキュー更新を許可するトランザクション パブリケーションで使用されます。  
  
> [!NOTE]  
>  パラメーターは任意の順序で指定できます。 オプション パラメーターを指定しなかった場合、既定のエージェント プロファイルの定義済みの値が使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
      qrdrsvc [-?]  
[-Continuous]  
[-DefinitionFiledefinition_file]  
[-Distributorserver_name[\instance_name]]  
[-DistributionDBdistribution_database]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-LoginTimeOutlogin_time_out_seconds]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PollingIntervalpolling_interval]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-ProfileNameagent_profile_name]  
[-QueryTimeOutquery_time_out_seconds]  
[-ResolverState [1|2|3]]  
```  
  
## <a name="arguments"></a>引数  
 **-?**  
 使用方法に関する情報を表示します。  
  
 **-連続**  
 キューに格納されたトランザクションの処理を、エージェントが継続的に試みるかどうかを指定します。 指定した場合、エージェントは、サブスクライバーから受け取った保留中のトランザクションがキューに存在しない場合でも、実行を継続します。  
  
 **-Definitionfile** _def_path_and_file_name_  
 エージェント定義ファイルのパスです。 エージェント定義ファイルには、エージェントのコマンド ライン引数が含まれます。 ファイルの内容は実行可能ファイルとして解析されます。 二重引用符 (") を使用して、任意の文字を含む引数値を指定します。  
  
 **-ディストリビューター** _server_name_[**\\**_instance_name_]  
 ディストリビューターの名前です。 サーバー上の *の既定のインスタンスの場合は、* server_name [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定します。 サーバー上のの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]名前付きインスタンスの*server_name*\\*instance_name*を指定します。 指定しなかった場合、既定値はローカル コンピューターの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のインスタンスの名前になります。  
  
 **-** _Distribution_database_の場合は、  
 ディストリビューション データベース名です。  
  
 **-DistributorLogin** _distributor_login_  
 ディストリビューターのログイン名です。  
  
 **-DistributorPassword** _distributor_password_  
 ディストリビューターのパスワードです。  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 ディストリビューターのセキュリティ モードを指定します。 値**0**は認証モード[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (既定値) を示し、値**1**は Windows 認証モードを示します。  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 接続確立時にキュー リーダー エージェントが使用する SSL (Secure Sockets Layer) の暗号化レベルです。  
  
|EncryptionLevel の値|[説明]|  
|---------------------------|-----------------|  
|**0**|SSL は使用されません。|  
|**1**|SSL は使用されますが、信頼できる発行者によって SSL サーバー証明が署名されているかどうかを検証しません。|  
|**2**|SSL が使用され、証明書の確認が行われます。|  

 > [!NOTE]  
 >  有効な SSL 証明書には、SQL Server の完全修飾ドメイン名が定義されます。 -EncryptionLevel を 2 に設定したときにエージェントが正しく接続されるようにするには、ローカルの SQL Server 上に別名を作成します。 'Alias Name' パラメーターはサーバー名にし、'Server' パラメーターは SQL Server の完全修飾名に設定する必要があります。
  
 詳細については、「 [SQL Server レプリケーションセキュリティ](../security/view-and-modify-replication-security-settings.md)」を参照してください。  
  
 **-HistoryVerboseLevel** [ **0**| **1**| **2**| **3**]  
 キュー リーダー操作中にログに記録する履歴の量を指定します。 
  **1**を選択すれば、ログへの履歴の記録がパフォーマンスに与える影響を最小限に抑えることができます。  
  
|HistoryVerboseLevel の値|[説明]|  
|-------------------------------|-----------------|  
|**0**|履歴はログに記録されません。この設定はお勧めできません。|  
|**1**|既定。 同じ状態 (startup、progress、success など) を示している以前の履歴メッセージを常に更新します。 前回の記録に同じ状態がない場合は、新しい記録を挿入します。|  
|**2**|アイドル状態のメッセージや長時間実行されるジョブのメッセージを含む新しい履歴レコードを挿入します。|  
|**番**|トラブルシューティングに役立つ補足的な情報を含む新しい履歴レコードを挿入します。|  
  
 **-Logintimeout** _login_time_out_seconds_  
 ログインがタイムアウトするまでの秒数です。既定値は15秒です。  
  
 **-出力** _output_path_and_file_name_  
 エージェントの出力ファイルのパスです。 ファイル名が指定されていない場合、出力はコンソールに送られます。 指定された名前のファイルが存在する場合、出力はそのファイルに追加されます。  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 出力を詳細表示にするかどうかを指定します。 詳細レベルが **0**の場合、エラー メッセージだけが出力されます。 詳細レベルが **1**の場合、すべての実行状況報告メッセージが出力されます。 詳細レベルが **2** (既定値) の場合、すべてのエラー メッセージと実行状況報告メッセージが出力されます。これはデバッグ時に便利です。  
  
 **-PollingInterval** _polling_interval_  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ベースのキューを使用したサブスクリプションの更新時にのみ適用されます。 保留中のトランザクションがキューに格納されているかどうかを確認するために、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のキューをポーリングする頻度を秒数で指定します。 有効値は、0 ～ 240 秒です。 既定値は 5 秒です。  
  
 **-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]  
 パブリケーション データベースとのデータベース ミラーリング セッションに参加する、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー パートナー インスタンスを指定します。 詳細については、「 [データベース ミラーリングとレプリケーション &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)」をご覧ください。  
  
 **-ProfileName** _agent_profile_name_  
 エージェントに対して既定値を提供するエージェント プロファイルの名前です。 詳細については、「[レプリケーション エージェント プロファイル](replication-agent-profiles.md)」を参照してください。  
  
 **-** _Query_time_out_seconds_  
 クエリがタイムアウトするまでの秒数です。既定値は1800秒です。  
  
 **-Resolverstate** [ **1**| **2**| **3**]  
 キュー更新における競合の解決方法を指定します。 
  **1** はパブリッシャーが優先されることを示します。この場合、現在キューの中で競合しているトランザクションはパブリッシャー側、およびキューを更新しようとしたサブスクライバー側でロールバックされます。キューに格納されている、それ以降のトランザクションについては、処理が継続されます。 
  **2** はサブスクライバーがオーバーライドされることを示します。つまり、キューに格納されたトランザクションの方がパブリッシャー側の値をオーバーライドします。 
  **3** は、競合が発生した場合は常にサブスクライバーが再初期化されることを示します (つまり、パブリッシャーが優先されます)。この場合、キューに格納された後続のトランザクションは強制的に終了され、サブスクリプションが再初期化されます。 既定の設定は、トランザクション パブリケーションの場合は **1** に、スナップショット パブリケーションの場合は **3** になります。  
  
## <a name="remarks"></a>解説  
 キュー リーダー エージェントを起動するには、コマンド プロンプトから **qrdrsvc.exe** を実行します。 詳細については、「 [レプリケーション エージェント実行可能ファイルのプログラミング](../concepts/replication-agent-executables-concepts.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レプリケーションエージェントの管理](replication-agent-administration.md)  
  
  
