---
title: sp_monitor (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_monitor_TSQL
- sp_monitor
dev_langs:
- TSQL
helpviewer_keywords:
- sp_monitor
ms.assetid: cb628496-2f9b-40e4-b018-d0831c4cb018
author: stevestein
ms.author: sstein
ms.openlocfilehash: d91f774973588096ea73675d9b0e9ebf6368f1ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022319"
---
# <a name="sp_monitor-transact-sql"></a>sp_monitor (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  に関する[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]統計情報を表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_monitor  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|[説明]|  
|-----------------|-----------------|  
|**last_run**|**Sp_monitor**前回の実行時刻。|  
|**current_run**|**Sp_monitor**の実行時間。|  
|**待ち時間**|**Sp_monitor**が実行されてから経過した秒数。|  
|**cpu_busy**|サーバーコンピューターの CPU が[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]処理している秒数。|  
|**io_busy**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が入出力操作に費やした秒数|  
|**退席**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がアイドル状態だった秒数|  
|**packets_received**|によって[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]読み取られた入力パケットの数。|  
|**packets_sent**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が書き込んだ出力パケット数|  
|**packet_errors**|パケットの読み取りおよび書き込み[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中にによって発生したエラーの数。|  
|**total_read**|によって[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]読み取られた回数。|  
|**total_write**|による[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]書き込み回数。|  
|**total_errors**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の読み書き中に発生したエラー数|  
|**数**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] へのログインまたはログイン試行の回数|  
  
## <a name="remarks"></a>解説  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、いくつかの関数によって処理量が追跡されます。 **Sp_monitor**を実行すると、これらの関数によって返された現在の値が表示され、最後にプロシージャが実行されてから変更された量が表示されます。  
  
 各列について、統計情報は*number*(*number)-**number*% または*number*(*number*) の形式で出力されます。 最初の*数値*は、が再起動されて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からの秒数 ( **cpu_busy**、 **io_busy**、および**アイドル**の場合) または合計数 (他の変数の場合) を表します。 かっこ内の*数値*は、最後に**sp_monitor**が実行されてからの秒数または合計数を表します。 割合は**sp_monitor**が最後に実行されてからの時間の割合です。 たとえば、レポートに**cpu_busy** (215)-68% と表示されている場合、cpu は、前回の起動[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以降に4250秒、 **sp_monitor**が最後に実行されてから215秒、 **sp_monitor**が最後に実行されてからの合計時間の68% に達しています。  
  
## <a name="permissions"></a>アクセス許可  
 
  **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のビジー状況に関する情報をレポートします。  
  
```  
USE master  
EXEC sp_monitor  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
||||  
|-|-|-|  
|**last_run**|**current_run**|**待ち時間**|  
|1998 年 3 月 29 日午前 11:55|1998 年 4 月 4 日午後 2:22|561|  
  
||||  
|-|-|-|  
|**cpu_busy**|**io_busy**|**退席**|  
|190 (0)-0%|187 (0)-0%|148 (556)-99%|  
  
||||  
|-|-|-|  
|**packets_received**|**packets_sent**|**packet_errors**|  
|16 (1)|20 (2)|0 (0)|  
  
|||||  
|-|-|-|-|  
|**total_read**|**total_write**|**total_errors**|**数**|  
|141 (0)|54920 (127)|0 (0)|4 (0)|  
  
## <a name="see-also"></a>参照  
 [sp_who &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
