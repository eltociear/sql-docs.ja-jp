---
title: dm_exec_cached_plan_dependent_objects (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_cached_plan_dependent_objects
- dm_exec_cached_plan_dependent_objects_TSQL
- sys.dm_exec_cached_plan_dependent_objects_TSQL
- dm_exec_cached_plan_dependent_objects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_cached_plan_dependent_objects dynamic management function
ms.assetid: 9b6cf5f7-b267-44fb-aac8-f49c9aa10cc1
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ca4499645846dacc762d8d3bf130ccc44a7f3155
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68097897"
---
# <a name="sysdm_exec_cached_plan_dependent_objects-transact-sql"></a>sys.dm_exec_cached_plan_dependent_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  各 [!INCLUDE[tsql](../../includes/tsql-md.md)] 実行プラン、共通言語ランタイム (CLR) 実行プラン、およびプランに関連付けられたカーソルの行を返します。  
  
## <a name="syntax"></a>構文  
  
```  
sys.dm_exec_cached_plan_dependent_objects(plan_handle)  
```  
  
## <a name="arguments"></a>引数  
*plan_handle*  
は、実行され、そのプランがプランキャッシュ内に存在するバッチのクエリ実行プランを一意に識別するトークンです。 *plan_handle*は**varbinary (64)** です。   

*Plan_handle*は、次の動的管理オブジェクトから取得できます。  
  
-   [dm_exec_cached_plans &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [dm_exec_query_stats &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [dm_exec_requests &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [dm_exec_procedure_stats &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [dm_exec_trigger_stats &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**usecounts**|**int**|実行コンテキストまたはカーソルが使用された回数。<br /><br /> NULL 値は許可されません。|  
|**memory_object_address**|**varbinary (8)**|実行コンテキストまたはカーソルのメモリアドレス。<br /><br /> NULL 値は許可されません。|  
|**cacheobjtype**|**nvarchar(50)**|プランキャッシュオブジェクトの種類です。 NULL 値は許可されません。 次のいずれかの値になります。<br /><br /> 実行プラン<br /><br /> CLR コンパイル済みの関数<br /><br /> CLR コンパイルプロシージャ<br /><br /> カーソル|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する `VIEW SERVER STATE` 権限が必要です。  
  
## <a name="physical-joins"></a>物理結合  
 ![リレーションシップダイアグラム](../../relational-databases/system-dynamic-management-views/media/dm-dependent-objects.gif "関係図")  
  
## <a name="relationship-cardinalities"></a>リレーションシップ基数  
  
|移行元|To|反対に、|リレーションシップ|  
|----------|--------|--------|------------------|  
|**dm_exec_cached_plan_dependent_objects**|**dm_os_memory_objects**|**memory_object_address**|一対一|  
  
## <a name="see-also"></a>参照  
 [実行関連の動的管理ビューおよび関数 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [syscacheobjects &#40;Transact-sql&#41;](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md)  
  
  
