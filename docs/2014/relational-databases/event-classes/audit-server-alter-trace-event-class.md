---
title: Audit Server Alter Trace イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Server Alter Trace event class
ms.assetid: 967586bf-d5f1-466c-82ab-8c461bfb6222
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10c3556edb5c58e281db2dcaf5c05e9a202a3091
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63012510"
---
# <a name="audit-server-alter-trace-event-class"></a>Audit Server Alter Trace イベント クラス
  **Audit Server Alter trace**イベントクラスは、alter trace 権限をチェックするすべてのステートメントで発生します。 ALTER TRACE をチェックするステートメントには、トレースの作成や構成、またはトレースへのフィルターの設定に使用するステートメントがあります。  
  
## <a name="audit-server-alter-trace-event-class-data-columns"></a>Audit Server Alter Trace イベント クラスのデータ列  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|のインスタンスへの[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続を作成したクライアントアプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|はい|  
|**DatabaseID**|**int**|USE *database*ステートメントで指定されたデータベースの ID、または特定のインスタンスに対して use *database*ステートメントが発行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]では、 **ServerName**データ列がトレースにキャプチャされ、そのサーバーが使用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|はい|  
|**DatabaseName**|**nvarchar**|ユーザーのステートメントが実行されているデータベースの名前。|35|はい|  
|**DBUserName**|**nvarchar**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザー名。|40|はい|  
|**EventSequence**|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|**名**|**nvarchar**|クライアントが実行されているコンピューターの名前。 このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|はい|  
|**Issystem で**|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|はい|  
|**ログイン**|**nvarchar**|ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログイン、または DOMAIN\username の形式で表された [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。|11|はい|  
|**LoginSid**|**絵**|ログイン ユーザーのセキュリティ ID 番号 (SID)。 この情報は、 **sys.server_principals** カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|はい|  
|**NTDomainName**|**nvarchar**|ユーザーが所属する Windows ドメイン。|7|はい|  
|**NTUserName**|**nvarchar**|Windows のユーザー名。|6|はい|  
|**ObjectName**|**nvarchar**|参照されているオブジェクトの名前。|34|はい|  
|**ObjectType**|**int**|イベントに関係するオブジェクトの種類を表す値。 この値は、 **sys. objects**カタログビューの type 列に対応しています。 値については、「 [ObjectType トレース イベント列](objecttype-trace-event-column.md)」を参照してください。|28|はい|  
|**OwnerName**|**nvarchar**|オブジェクト所有者のデータベース ユーザー名。|37|はい|  
|**RequestID**|**int**|ステートメントが含まれている要求の ID。|49|はい|  
|**Server**|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|**SessionLoginName**|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に接続し、Login2 としてステートメントを実行すると、 **Sessionloginは**Login1 と**loginLogin2**を表示します。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|はい|  
|**調べる**|**int**|イベントが発生したセッションの ID。|12|はい|  
|**StartTime**|**DATETIME**|イベントの開始時刻 (取得できた場合)。|14|はい|  
|**成功**|**int**|1 = 成功。 0 = 失敗。 たとえば、値 1 は権限チェックの成功を示し、値 0 は失敗を示します。|23|はい|  
|**TextData**|**ntext**|トレースでキャプチャされたイベント クラスに依存するテキスト値。|1 で保護されたプロセスとして起動されました|はい|  
|**TransactionID**|**bigint**|システムによって割り当てられたトランザクション ID。|4|はい|  
|**XactSequence**|**bigint**|現在のトランザクションを説明するトークン。|50|はい|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
