---
title: sysarticleupdates (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticleupdates_TSQL
- sysarticleupdates
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticleupdates system table
ms.assetid: 11a53bcd-a215-4d0b-9db8-233981d3ef5d
author: stevestein
ms.author: sstein
ms.openlocfilehash: d2e710bdbe8f026624ea71357afb6d204b333c91
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68130492"
---
# <a name="sysarticleupdates-transact-sql"></a>sysarticleupdates (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  即時更新サブスクリプションをサポートするアーティクルごとに1行のレコードを格納します。 このテーブルは、レプリケートされたデータベースに保存されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|アーティクルの一意な ID 番号を示す ID 列。|  
|**pubid**|**int**|アーティクルが属しているパブリケーションの ID。|  
|**sync_ins_proc**|**int**|挿入同期トランザクションを処理するストアドプロシージャの ID。|  
|**sync_upd_proc**|**int**|更新同期トランザクションを処理するストアドプロシージャの ID。|  
|**sync_del_proc**|**int**|削除同期トランザクションを処理するストアドプロシージャの ID。|  
|**autogen**|**bit**|ストアドプロシージャが自動的に生成されることを示します。<br /><br /> **0** = False、自動ではありません。<br /><br /> **1** = True、自動。|  
|**sync_upd_trig**|**int**|アーティクルテーブルの自動バージョン管理トリガーの ID です。|  
|**conflict_tableid**|**int**|競合テーブルの ID。|  
|**ins_conflict_proc**|**int**|競合を**conflict_table**に書き込むために使用されるプロシージャの ID。|  
|**identity_support**|**bit**|キュー更新を使用するときに、自動 id 範囲処理を有効にするかどうかを指定します。 **0**は、id 範囲がサポートされていないことを示します。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
