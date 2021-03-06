---
title: fn_hadr_backup_is_preferred_replica (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_backup_is_preferred_replica_TSQL
- sys.fn_hadr_backup_is_preferred_replica
- fn_hadr_backup_is_preferred_replica_TSQL
- fn_hadr_backup_is_preferred_replica
dev_langs:
- TSQL
helpviewer_keywords:
- backup on secondary replicas
- active secondary replicas [SQL Server], backup on secondary replicas
- sys.fn_hadr_backup_is_preferred_replica function
ms.assetid: 61b9be77-e2f6-4da1-b2ae-a62cbe226145
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4e343e7e9657b69ebd06a147cb99fa19e3c36aab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68120253"
---
# <a name="sysfn_hadr_backup_is_preferred_replica--transact-sql"></a>fn_hadr_backup_is_preferred_replica (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  現在のレプリカが推奨されるバックアップ レプリカであるかどうかを決定するために使用されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_hadr_backup_is_preferred_replica ( 'dbname' )  
```  
  
## <a name="arguments"></a>引数  
 '*dbname*'  
 バックアップするデータベースの名前です。 *dbname*の型は sysname です。  
  
## <a name="returns"></a>戻り値  
 現在のインスタンス上のデータベースが優先レプリカに存在する場合は 1 を返します。 それ以外の場合は 0 を返します。  
  
## <a name="remarks"></a>解説  
 バックアップスクリプトでこの関数を使用して、現在のデータベースがバックアップに適したレプリカに存在するかどうかを確認します。 すべての可用性レプリカでスクリプトを実行できます。 これらの各ジョブは、どのジョブを実行するかを決定するために同じデータを確認するので、スケジュールされたジョブの1つだけがバックアップステージに進みます。 サンプル コードは次のようになります。  
  
```  
If sys.fn_hadr_backup_is_preferred_replica( @dbname ) <> 1   
BEGIN  
-- If this is not the preferred replica, exit (probably without error).  
END  
-- If this is the preferred replica, continue to do the backup.  
  
```  
  
## <a name="examples"></a>例  
  
### <a name="a-using-sysfn_hadr_backup_is_preferred_replica"></a>A. sys.fn_hadr_backup_is_preferred_replica を使用する  
 次の例では、現在のデータベースが推奨されるバックアップレプリカである場合、1を返します。  
  
```  
SELECT sys.fn_hadr_backup_is_preferred_replica ('TestDB');  
GO  
```  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [Always On 可用性グループの関数 &#40;Transact-sql&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [Always On 可用性グループ &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-sql&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [アクティブなセカンダリ: セカンダリレプリカでのバックアップ &#40;Always On 可用性グループ&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) [Always On 可用性グループのカタログビュー &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)      
  
  
