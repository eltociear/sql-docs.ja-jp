---
title: sp_dbremove (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbremove
- sp_dbremove_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbremove
ms.assetid: a8513f4a-c025-49c8-99c3-4c83cb7f51ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea264c48332f6e72a5f26b330e42cfb1e3d3ff8d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68061249"
---
# <a name="sp_dbremove-transact-sql"></a>sp_dbremove (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースおよびそのデータベースと関連付けられているすべてのファイルを削除します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに[DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md)を使用することをお勧めします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dbremove [ @dbname = ] 'database' [ , [ @dropdev = ] 'dropdev' ]   
```  
  
## <a name="arguments"></a>引数  
`[ @dbname = ] 'database'`削除するデータベースの名前を指定します。 *データベースのデータ*型は**sysname**で、既定値は NULL です。  
  
`[ @dropdev = ] 'dropdev'`旧バージョンとの互換性を保つために指定されたフラグであり、現在は無視されています。 *dropdev*の値は**dropdev**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 
  **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、と`sales`いう名前のデータベースと、それに関連付けられているすべてのファイルを削除します。  
  
```  
EXEC sp_dbremove sales;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-sql&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-sql&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DBCC &#40;Transact-sql&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)   
 [sp_detach_db &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  
