---
title: sp_delete_database_backuphistory (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_database_backuphistory
- sp_delete_database_backuphistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_database_backuphistory
ms.assetid: 4c237944-453d-49fb-8d0e-4596945ac147
author: stevestein
ms.author: sstein
ms.openlocfilehash: ff85b52e0b0ed6715b64287f0c0e5abd5a0ae9c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68085814"
---
# <a name="sp_delete_database_backuphistory-transact-sql"></a>sp_delete_database_backuphistory (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたデータベースに関する情報をバックアップ履歴テーブルと復元履歴テーブルから削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_delete_database_backuphistory [ @database_name = ] 'database_name'  
```  
  
## <a name="arguments"></a>引数  
`[ @database_name = ] database_name`バックアップ操作と復元操作に関係するデータベースの名前を指定します。 *database_name*は**sysname**であり、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_delete_database_backuphistory**は、 **msdb**データベースから実行する必要があります。  
  
 このストアド プロシージャは次のテーブルに影響します。  
  
-   [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)  
  
-   [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
  
-   [backupmediafamily](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
  
-   [backupmediaset](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
  
-   [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)  
  
-   [restorefile](../../relational-databases/system-tables/restorefile-transact-sql.md)  
  
-   [restorefilegroup](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)  
  
-   [restorehistory](../../relational-databases/system-tables/restorehistory-transact-sql.md)  
  
## <a name="permissions"></a>アクセス許可  
 
  **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、バックアップと[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]復元の履歴テーブルで、データベースのすべてのエントリを削除します。  
  
```  
USE msdb;  
GO  
EXEC sp_delete_database_backuphistory @database_name = 'AdventureWorks2012';  
  
```  
  
## <a name="see-also"></a>参照  
 [sp_delete_backuphistory &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)   
 [SQL Server&#41;&#40;のバックアップ履歴とヘッダー情報](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  
