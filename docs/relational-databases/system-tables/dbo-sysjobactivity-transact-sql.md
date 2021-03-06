---
title: dbo. sysjobactivity (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobactivity_TSQL
- dbo.sysjobactivity
- sysjobactivity
- sysjobactivity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobactivity system table
ms.assetid: fd17cac9-5d1f-4b44-b2dc-ee9346d8bf1e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52d929496bf3db83dc63cdde6d86bf1a2ee1a3f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67902219"
---
# <a name="dbosysjobactivity-transact-sql"></a>dbo.sysjobactivity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの利用状況と状態を記録します。  このテーブルは、 **msdb**データベースに格納されます。
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|**Msdb**データベースの**syssessions**テーブルに格納されているセッションの ID。|  
|**job_id**|**UNIQUEIDENTIFIER**|ジョブの ID。|  
|**run_requested_date**|**DATETIME**|ジョブの実行が要求された日付と時刻。|  
|**run_requested_source**|**sysname (nvarchar (128))**|ジョブの実行要求の発生元。<br /><br /> **1** = SOURCE_SCHEDULER<br /><br /> **2** = SOURCE_ALERTER<br /><br /> **3** = SOURCE_BOOT<br /><br /> **4** = SOURCE_USER<br /><br /> **6** = SOURCE_ON_IDLE_SCHEDULE|  
|**queued_date**|**DATETIME**|ジョブがキューに格納された日時。 ジョブが直接実行された場合、この列は NULL になります。|  
|**start_execution_date**|**DATETIME**|ジョブの実行がスケジュールされている日付と時刻。|  
|**last_executed_step_id**|**int**|実行された最後のジョブ ステップの ID。|  
|**last_executed_step_**<br /><br /> **date**|**DATETIME**|前回のジョブステップが実行を開始した日付と時刻。|  
|**stop_execution_date**|**DATETIME**|ジョブの実行が終了した日付と時刻。|  
|**job_history_id**|**int**|**Sysjobhistory**テーブル内の行を識別するために使用されます。|  
|**next_scheduled_run_date**|**DATETIME**|ジョブを実行する予定の次の日付と時刻。|  

## <a name="example"></a>例
この例では、すべての SQL Server エージェントジョブの実行時の状態を返します。  
  [!INCLUDE[tsql](../../includes/tsql-md.md)] で次の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を実行します。
```sql
SELECT sj.Name, 
    CASE
        WHEN sja.start_execution_date IS NULL THEN 'Not running'
        WHEN sja.start_execution_date IS NOT NULL AND sja.stop_execution_date IS NULL THEN 'Running'
        WHEN sja.start_execution_date IS NOT NULL AND sja.stop_execution_date IS NOT NULL THEN 'Not running'
    END AS 'RunStatus'
FROM msdb.dbo.sysjobs sj
JOIN msdb.dbo.sysjobactivity sja
ON sj.job_id = sja.job_id
WHERE session_id = (
    SELECT MAX(session_id) FROM msdb.dbo.sysjobactivity); 
```
  
## <a name="see-also"></a>参照  
 [dbo. sysjobhistory &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-sysjobhistory-transact-sql.md)  
  
  
