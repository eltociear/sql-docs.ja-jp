---
title: sp_defaultdb (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_defaultdb_TSQL
- sp_defaultdb
dev_langs:
- TSQL
helpviewer_keywords:
- sp_defaultdb
ms.assetid: 663b859f-c6da-4942-95a6-60b93d05654e
author: stevestein
ms.author: sstein
ms.openlocfilehash: aec951ea8a0397c39c57619609264596aec9a648
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68085819"
---
# <a name="sp_defaultdb-transact-sql"></a>sp_defaultdb (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインの[!INCLUDE[msCoName](../../includes/msconame-md.md)]既定のデータベースを変更します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに[ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)を使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_defaultdb [ @loginame = ] 'login', [ @defdb = ] 'database'   
```  
  
## <a name="arguments"></a>引数  
`[ @loginame = ] 'login'`ログイン名を指定します。 *login*は**sysname**,、既定値はありません。 *ログイン*には、既存[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のログインまたは Windows ユーザーまたはグループを指定できます。 Windows ユーザーまたはグループのログインがに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]存在しない場合は、自動的に追加されます。  
  
`[ @defdb = ] 'database'`新しい既定のデータベースの名前を指定します。 *データベースのデータ*型は**sysname**で、既定値はありません。 *データベース*は既に存在している必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **SP_DEFAULTDB** ALTER LOGIN を呼び出します。 このステートメントでは、追加のオプションがサポートされています。 既定のデータベースの変更の詳細については、「 [ALTER LOGIN &#40;transact-sql&#41;](../../t-sql/statements/alter-login-transact-sql.md)」を参照してください。  
  
 **sp_defaultdb**は、ユーザー定義のトランザクション内では実行できません。  
  
## <a name="permissions"></a>アクセス許可  
 ALTER ANY LOGIN 権限が必要です。  
  
## <a name="examples"></a>例  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] ログイン [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のデータベースとして `Victoria` を設定します。  
  
```  
EXEC sp_defaultdb 'Victoria', 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [sp_addlogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
