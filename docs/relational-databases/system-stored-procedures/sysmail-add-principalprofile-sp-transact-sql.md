---
title: sysmail_add_principalprofile_sp (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_principalprofile_sp_TSQL
- sysmail_add_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_principalprofile_sp
ms.assetid: b2a0b313-abb9-4c23-8511-db77ca8172b3
author: stevestein
ms.author: sstein
ms.openlocfilehash: fedc7e0dd7fe71feb0b0da1f00f2a7f996c6129c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "72305053"
---
# <a name="sysmail_add_principalprofile_sp-transact-sql"></a>sysmail_add_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Msdb データベースプリンシパルにデータベースメールプロファイルを使用する権限を許可します。 データベースプリンシパルは、SQL Server 認証ユーザー、Windows ユーザー、または Windows グループにマップされている必要があります。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_add_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
    [ , [ @is_default ] = 'is_default' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @principal_id = ] principal_id`関連付けの**msdb**データベースのデータベースユーザーまたはロールの ID。 *principal_id*は**int**,、既定値は NULL です。 *Principal_id*または*principal_name*のいずれかを指定する必要があります。 *Principal_id*が**0**の場合、このプロファイルはパブリックプロファイルになり、データベース内のすべてのプリンシパルにアクセス権が付与されます。  
  
`[ @principal_name = ] 'principal_name'`関連付けの**msdb**データベースのデータベースユーザーまたはロールの名前。 *principal_name*は**sysname**,、既定値は NULL です。 *Principal_id*または*principal_name*のいずれかを指定する必要があります。 *Principal_name*が **' public '** の場合、このプロファイルはパブリックプロファイルになり、データベース内のすべてのプリンシパルにアクセス権が付与されます。  
  
`[ @profile_id = ] profile_id`関連付けのプロファイルの id。 *profile_id*は**int**,、既定値は NULL です。 *Profile_id*または*profile_name*のいずれかを指定する必要があります。  
  
`[ @profile_name = ] 'profile_name'`関連付けに使用するプロファイルの名前。 *profile_name*は**sysname**であり、既定値はありません。 *Profile_id*または*profile_name*のいずれかを指定する必要があります。  
  
`[ @is_default = ] is_default`このプロファイルがプリンシパルの既定のプロファイルであるかどうかを指定します。 プリンシパルには、既定のプロファイルが1つだけ含まれている必要があります。 *is_default*は**ビット**,、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 プロファイルを公開するには、 ** \@principal_id**を**0**または**public**の** \@principal_name**として指定します。 パブリックプロファイルは、 **msdb**データベース内のすべてのユーザーが使用できます。ただし、ユーザーは**sp_send_dbmail**を実行するために、 **databasemailuserrole**のメンバーでもある必要があります。  
  
 データベースユーザーは、既定のプロファイルを1つだけ持つことができます。 ** \@Is_default**が '**1**' で、ユーザーが既に1つ以上のプロファイルに関連付けられている場合、指定されたプロファイルがユーザーの既定のプロファイルになります。 それまで既定のプロファイルであったプロファイルは、引き続きこのユーザーに関連付けられますが、既定のプロファイルではなくなります。  
  
 ** \@Is_default**が '**0**' で、他のアソシエーションが存在しない場合、ストアドプロシージャはエラーを返します。  
  
 ストアドプロシージャ**sysmail_add_principalprofile_sp**は**msdb**データベースにあり、 **dbo**スキーマが所有しています。 現在のデータベースが**msdb**でない場合は、3つの部分で構成される名前を使用してプロシージャを実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの実行権限は、既定では**sysadmin**固定サーバーロールのメンバーに与えています。  
  
## <a name="examples"></a>例  
 **A. 関連付けを作成し、既定のプロファイルを設定する**  
  
 次の例では、という名前`AdventureWorks Administrator Profile`のプロファイルと**msdb**データベースユーザー `ApplicationUser`の間の関連付けを作成します。 プロファイルは、ユーザーの既定のプロファイルです。  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @is_default = 1 ;  
```  
  
 **B. プロファイルを既定のパブリック プロファイルにする**  
  
 次の例では、 `AdventureWorks Public Profile`プロファイルを、 **msdb**データベース内のユーザーの既定のパブリックプロファイルにします。  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'AdventureWorks Public Profile',  
    @is_default = 1 ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベースメール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースメール](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
