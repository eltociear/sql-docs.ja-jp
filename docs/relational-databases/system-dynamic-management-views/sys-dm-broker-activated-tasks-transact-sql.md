---
title: dm_broker_activated_tasks (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_broker_activated_tasks
- sys.dm_broker_activated_tasks_TSQL
- dm_broker_activated_tasks
- dm_broker_activated_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_activated_tasks dynamic management view
ms.assetid: 17e6f87f-8f56-489d-9aed-216afc8ef310
author: stevestein
ms.author: sstein
ms.openlocfilehash: f80ec78e37707058a354a03bb2605a38abdfa803
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68099189"
---
# <a name="sysdm_broker_activated_tasks-transact-sql"></a>sys.dm_broker_activated_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Service Broker によってアクティブ化されるストアドプロシージャごとに1行の値を返します。  
 

|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**調べる**|**int**|アクティブ化されたストアドプロシージャのセッションの ID。 NULLABLE.|  
|**database_id**|**smallint**|キューが定義されているデータベースの ID。 NULLABLE.|  
|**queue_id**|**int**|ストアドプロシージャがアクティブ化されたキューのオブジェクトの ID。 NULLABLE.|  
|**procedure_name**|**nvarchar (650)**|アクティブ化されたストアドプロシージャの名前。 NULLABLE.|  
|**execute_as**|**int**|ストアドプロシージャを実行するユーザーの ID。 NULLABLE.|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="physical-joins"></a>物理結合  
 ![sys.dm_broker_activated_tasks の結合](../../relational-databases/system-dynamic-management-views/media/join-dm-broker-activated-tasks-1.gif "sys.dm_broker_activated_tasks の結合")  
  
## <a name="relationship-cardinalities"></a>リレーションシップ基数  
  
|移行元|To|リレーションシップ|  
|----------|--------|------------------|  
|dm_broker_activated_tasks。|dm_exec_sessions。 session_id|一対一|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Service Broker 関連する動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

