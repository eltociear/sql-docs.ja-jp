---
title: Scan:Stopped イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Scan:Stopped event class
ms.assetid: b6b20ae9-aebb-454a-b639-6b7bb2f9339b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e287ae5f70ebe325e207d7c1fe593b60a1223f44
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63044244"
---
# <a name="scanstopped-event-class"></a>Scan:Stopped イベント クラス
  Scan:Stopped イベント クラスは、テーブルやインデックスのスキャンが停止されたときに発生します。  
  
## <a name="scanstopped-event-class-data-columns"></a>Scan:Stopped イベント クラスのデータ列  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|はい|  
|ClientProcessID|`int`|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。 クライアントでクライアント プロセス ID が指定されると、このデータ列が作成されます。|9|はい|  
|DatabaseID|`int`|USE *database*ステートメントで指定されたデータベースの ID、または特定のインスタンスに対して use *database*ステートメントが発行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]では、ServerName データ列がトレースにキャプチャされ、そのサーバーが使用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|はい|  
|DatabaseName|`nvarchar`|ユーザーのステートメントが実行されているデータベースの名前。|35|はい|  
|EventClass|`int`|イベントの種類 = 52。|27|いいえ|  
|EventSequence|`int`|要求内の特定のイベントのシーケンス。|51|いいえ|  
|GroupID|`int`|SQL トレース イベントが発生したワークロード グループの ID。|66|はい|  
|HostName|`nvarchar`|クライアントが実行されているコンピューターの名前。 このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|はい|  
|IndexID|`int`|スキャンされているインデックス。|24|はい|  
|IsSystem|`int`|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|はい|  
|LoginName|`nvarchar`|ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。|11|はい|  
|LoginSid|`image`|ログイン ユーザーのセキュリティ ID 番号 (SID)。 この情報は、sys.server_principals カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|はい|  
|NTDomainName|`nvarchar`|ユーザーが所属する Windows ドメイン。|7|はい|  
|NTUserName|`nvarchar`|Windows のユーザー名。|6|はい|  
|ObjectID|`int`|スキャンされているオブジェクトのシステム割り当て ID。|22|はい|  
|読み取り|`bigint`|(論理的に) 読み取られたページ数。|16|はい|  
|RequestID|`int`|ステートメントが含まれている要求の ID。|49|はい|  
|ServerName|`nvarchar`|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|SessionLoginName|`nvarchar`|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|はい|  
|SPID|`int`|イベントが発生したセッションの ID。|12|はい|  
|StartTime|`datetime`|イベントの開始時刻 (取得できた場合)。|14|はい|  
|TransactionID|`bigint`|システムによって割り当てられたトランザクション ID。|4|はい|  
|XactSequence|`bigint`|現在のトランザクションを説明するトークン。|50|はい|  
  
## <a name="see-also"></a>参照  
 [sp_trace_setevent &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
