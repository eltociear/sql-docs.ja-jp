---
title: dm_fts_fdhosts (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_fts_fdhosts
- dm_fts_fdhosts_TSQL
- sys.dm_fts_fdhosts
- sys.dm_fts_fdhosts_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_fdhosts dynamic management view
- troubleshooting [SQL Server], full-text search
ms.assetid: d42a6334-4362-4361-83da-f8324fe55ec7
author: pmasl
ms.author: pelopes
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 77bf96ee1cea4356e26d33fab9ab519e99ae0a60
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265960"
---
# <a name="sysdm_fts_fdhosts-transact-sql"></a>sys.dm_fts_fdhosts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  サーバー インスタンス上のフィルター デーモン ホストの現在のアクティビティに関する情報を返します。  
  
 
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**fdhost_id**|**int**|フィルターデーモンホストの ID。|  
|**fdhost_name**|**nvarchar (120)**|フィルターデーモンホストの名前。|  
|**fdhost_process_id**|**int**|フィルター デーモン ホストの Windows プロセス ID。|  
|**fdhost_type**|**nvarchar (120)**|フィルター デーモン ホストで処理されるドキュメントの種類。次のいずれかです。<br /><br /> シングルスレッド<br /><br /> マルチスレッド<br /><br /> 巨大なドキュメント|  
|**max_thread**|**int**|フィルター デーモン ホストのスレッドの最大数。|  
|**batch_count**|**int**|フィルター デーモン ホストで処理中のバッチ数。|  
  
## <a name="permissions"></a>アクセス許可  

で[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]は、 `VIEW SERVER STATE`権限が必要です。   
Premium [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルでは、データベース`VIEW DATABASE STATE`の権限が必要です。 Standard [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルおよび Basic レベルでは、**サーバー管理**者または**Azure Active Directory 管理者**アカウントが必要です。   

## <a name="examples"></a>例  
 次の例では、フィルター デーモン ホストの名前とフィルター デーモン ホストのスレッドの最大数を返します。 また、フィルターデーモンで現在処理されているバッチの数も監視します。 この情報は、パフォーマンスを診断するために使用できます。  
  
```  
SELECT fdhost_name, batch_count, max_thread FROM sys.dm_fts_fdhosts;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のフルテキスト検索とセマンティック検索の動的管理ビューおよび関数](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)  
  
  
