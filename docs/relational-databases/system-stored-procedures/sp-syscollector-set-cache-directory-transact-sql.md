---
title: sp_syscollector_set_cache_directory (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_set_cache_directory_TSQL
- sp_syscollector_set_cache_directory
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_set_cache_directory stored procedure
ms.assetid: df56d5a5-8961-494f-a745-d752ca63805a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 03236c2882cad61e42ffa0fcdeb322d4ada53c2a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "76910045"
---
# <a name="sp_syscollector_set_cache_directory-transact-sql"></a>sp_syscollector_set_cache_directory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  収集したデータが管理データウェアハウスにアップロードされる前に保存されるディレクトリを指定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syscollector_set_cache_directory [ @cache_directory = ] 'cache_directory'  
```  
  
## <a name="arguments"></a>引数  
`[ @cache_directory = ] 'cache_directory'`収集したデータが一時的に格納されるファイルシステム内のディレクトリ。 *cache_directory*は**nvarchar (255)**,、既定値は NULL です。 この値を指定しなかった場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定の一時ディレクトリが使用されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 キャッシュ ディレクトリの構成を変更する前に、データ コレクターを無効にする必要があります。 データ コレクターが有効になっている場合、このストアド プロシージャは失敗します。 詳細については、「[データコレクションの有効化または無効化](../../relational-databases/data-collection/enable-or-disable-data-collection.md)」と「[データコレクションの管理](../../relational-databases/data-collection/manage-data-collection.md)」を参照してください。  
  
 指定されたディレクトリは、sp_syscollector_set_cache_directory の実行時に存在する必要はありません。ただし、ディレクトリが作成されるまで、データを正常にキャッシュおよびアップロードすることはできません。 このストアド プロシージャを実行する前に、ディレクトリを作成することをお勧めします。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャを実行するには、dc_admin (EXECUTE 権限を持つ) 固定データベースロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、データコレクターを無効にし、データコレクターのキャッシュ`D:\tempdata`ディレクトリをに設定してから、データコレクターを有効にします。  
  
```sql  
USE msdb;  
GO  
EXECUTE dbo.sp_syscollector_disable_collector;  
GO  
EXEC dbo.sp_syscollector_set_cache_directory N'D:\tempdata';  
GO  
EXECUTE dbo.sp_syscollector_enable_collector;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データコレクターストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [sp_syscollector_set_cache_window &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-set-cache-window-transact-sql.md)  
  
  
