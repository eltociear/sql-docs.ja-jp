---
title: dm_os_memory_brokers (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_brokers
- dm_os_memory_brokers_TSQL
- sys.dm_os_memory_brokers_TSQL
- dm_os_memory_brokers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_brokers dynamic management view
ms.assetid: 48dd6ad9-0d36-4370-8a12-4921d0df4b86
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8e131e2550ffa5078df5e284898ffe936128b7e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265875"
---
# <a name="sysdm_os_memory_brokers-transact-sql"></a>sys.dm_os_memory_brokers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  メモリマネージャーを使用する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内部の割り当て。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Dm_os_process_memory**と内部カウンターのプロセスメモリカウンターの差を追跡することで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリ空間内の外部コンポーネントからのメモリ使用を示すことができます。  
  
 メモリブローカーは、現在および予想される使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]量に基づいて、内のさまざまなコンポーネント間のメモリ割り当てをかなり均等に分散します。 メモリ ブローカーは割り当てを実行しません。 コンピューティングディストリビューションの割り当てを追跡するだけです。  
  
 次の表は、メモリ ブローカーに関する情報を示しています。  
  
> [!NOTE]  
>  またはから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]これを[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]呼び出すには、 **dm_pdw_nodes_os_memory_brokers**という名前を使用します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**pool_id**|**int**|リソース ガバナー プールに関連付けられているリソース プールの ID。|  
|**memory_broker_type**|**nvarchar (60)**|メモリ ブローカーの種類。 現在、に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は3種類のメモリブローカーがあります。以下にその説明を示します。<br /><br /> **MEMORYBROKER_FOR_CACHE** : キャッシュされたオブジェクトによって使用されるために割り当てられたメモリ (バッファープールキャッシュではありません)。<br /><br /> **MEMORYBROKER_FOR_STEAL** : バッファープールから盗まれたメモリ。 このメモリは、現在の所有者によって解放されるまで、他のコンポーネントで再利用することはできません。<br /><br /> **MEMORYBROKER_FOR_RESERVE** : 現在実行中の要求で今後使用するために予約されているメモリ。|  
|**allocations_kb**|**bigint**|この種類のブローカーに割り当てられているメモリの量 (KB 単位)。|  
|**allocations_kb_per_sec**|**bigint**|1秒あたりのメモリ割り当て率 (KB 単位)。 この値は、メモリ割り当て解除では負の値になります。|  
|**predicted_allocations_kb**|**bigint**|ブローカーによるメモリの予想割り当て量。 これは、メモリ使用パターンに基づいています。|  
|**target_allocations_kb**|**bigint**|推奨されるメモリ割り当て量 (KB 単位)。現在の設定とメモリの使用パターンに基づいて決定されます。 このブローカーは、この数まで拡大または縮小する必要があります。|  
|**future_allocations_kb**|**bigint**|次の数秒で実行される、割り当ての予測数 (KB 単位)。|  
|**overall_limit_kb**|**bigint**|ブローカーが割り当てることができるメモリの最大量 (KB 単位)。|  
|**last_notification**|**nvarchar (60)**|メモリ使用量の推奨値。現在の設定と使用パターンに基づいて決定されます。 有効な値は次のとおりです。<br /><br /> 拡張<br /><br /> 伸縮<br /><br /> 安定した|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> このディストリビューションが配置されているノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可  

で[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]は、 `VIEW SERVER STATE`権限が必要です。   
Premium [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルでは、データベース`VIEW DATABASE STATE`の権限が必要です。 Standard [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルおよび Basic レベルでは、**サーバー管理**者または**Azure Active Directory 管理者**アカウントが必要です。   
  
## <a name="see-also"></a>参照  

  [SQL Server オペレーティングシステム関連の動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


