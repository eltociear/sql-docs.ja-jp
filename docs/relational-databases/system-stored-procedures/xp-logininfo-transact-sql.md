---
title: xp_logininfo (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_logininfo_TSQL
- xp_logininfo
dev_langs:
- TSQL
helpviewer_keywords:
- xp_logininfo
ms.assetid: ee7162b5-e11f-4a0e-a09c-1878814dbbbd
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 2b3af47a1c09160faab97494d9749fd67c051cd4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67898408"
---
# <a name="xp_logininfo-transact-sql"></a>xp_logininfo (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Windows ユーザーおよび Windows グループに関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_logininfo [ [ @acctname = ] 'account_name' ]   
     [ , [ @option = ] 'all' | 'members' ]   
     [ , [ @privilege = ] variable_name OUTPUT]  
```  
  
## <a name="arguments"></a>引数  
`[ @acctname = ] 'account_name'`に対するアクセスを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]許可された Windows ユーザーまたはグループの名前を指定します。 *account_name*は**sysname**,、既定値は NULL です。 *Account_name*が指定されていない場合は、明示的にログイン権限が付与されているすべての windows グループと windows ユーザーがレポートされます。 *account_name*は完全修飾名である必要があります。 たとえば、' ADVWKS4\macraes '、' BUILTIN\Administrators ' のようになります。  
  
 **' all '** | **' メンバー '**  
 アカウントのすべてのアクセス許可パスに関する情報をレポートするか、Windows グループのメンバーに関する情報を報告するかを指定します。 オプションは**varchar (10)**,、既定値は NULL です。 ** \@** **All**を指定しない限り、最初のアクセス許可パスのみが表示されます。  
  
`[ @privilege = ] variable_name`は、指定された Windows アカウントの特権レベルを返す出力パラメーターです。 *variable_name*は**varchar (10)**,、既定値は ' 不要 ' です。 返される特権レベルは**user**、 **admin**、または**null**です。  
  
 OUTPUT  
 指定した場合、出力パラメーターに*variable_name*を配置します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**アカウント名**|**sysname**|完全修飾 Windows アカウント名。|  
|**type**|**char (8)**|Windows アカウントの種類。 有効な値は、**ユーザー**または**グループ**です。|  
|**持っ**|**char (9)**|の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アクセス特権。 有効な値は、 **admin**、 **user**、または**null**です。|  
|**mapped login name**|**sysname**|ユーザー特権を持つユーザーアカウントの場合、[マップされた**ログイン名**] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]には、このアカウントを使用してログインするときに、その前に追加したドメイン名を持つマップされた規則を使用してログインするときに使用する、マップされたログイン名が表示されます。|  
|**permission path**|**sysname**|アカウントへのアクセスが許可されているグループメンバーシップ。|  
  
## <a name="remarks"></a>解説  
 *Account_name*が指定されている場合、 **xp_logininfo**は、指定された Windows ユーザーまたはグループの最上位の特権レベルを報告します。 Windows ユーザーがシステム管理者とドメインユーザーの両方としてアクセス権を持っている場合は、システム管理者として報告されます。 ユーザーが同じ権限レベルの複数の Windows グループのメンバーである場合、へのアクセスが最初に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]許可されたグループのみがレポートされます。  
  
 *Account_name*が[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインに関連付けられていない有効な Windows ユーザーまたはグループである場合は、空の結果セットが返されます。 *Account_name*が有効な Windows ユーザーまたはグループとして識別できない場合は、エラーメッセージが返されます。  
  
 *Account_name*と**all**が指定されている場合は、Windows ユーザーまたはグループのすべてのアクセス許可パスが返されます。 *Account_name*が複数のグループのメンバーであり、そのすべてにへ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のアクセスが許可されている場合は、複数の行が返されます。 **Admin**特権の行は、**ユーザー**特権行の前に返されます。特権レベルでは、対応する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインが作成された順序で行が返されます。  
  
 *Account_name*と**メンバー**が指定されている場合は、グループの次のレベルのメンバーの一覧が返されます。 *Account_name*がローカルグループの場合、一覧にはローカルユーザー、ドメインユーザー、およびグループを含めることができます。 *Account_name*がドメインアカウントの場合、一覧はドメインユーザーで構成されます。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではドメイン コントローラーに接続してグループのメンバーシップ情報を取得する必要があります。 サーバーがドメインコントローラに接続できない場合、情報は返されません。  
  
 **xp_logininfo**は、ユニバーサルグループではなく Active Directory グローバルグループからの情報のみを返します。  
  
## <a name="permissions"></a>アクセス許可  
 **Sysadmin**固定サーバーロールのメンバーシップ、または実行権限が付与された**master**データベースの**public**固定データベースロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、 `BUILTIN\Administrators` Windows グループに関する情報を表示します。  
  
```  
EXEC xp_logininfo 'BUILTIN\Administrators';  
```  
  
## <a name="see-also"></a>参照  
 [sp_denylogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Transact-sql&#41;&#40;の一般的な拡張ストアドプロシージャ](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  
