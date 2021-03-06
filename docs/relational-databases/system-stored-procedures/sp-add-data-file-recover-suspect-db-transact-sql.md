---
title: sp_add_data_file_recover_suspect_db (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_data_file_recover_suspect_db
- sp_add_data_file_recover_suspect_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_data_file_recover_suspect_db
ms.assetid: b25262aa-a228-48b7-8739-6581c760b171
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2c95b74b5c1875f2a1f1db40ec42e3f3ada87a63
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67942364"
---
# <a name="sp_add_data_file_recover_suspect_db-transact-sql"></a>sp_add_data_file_recover_suspect_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ファイル グループの領域が不足していたため (エラー 1105)、データベースの復旧を完了できなかったときに、データ ファイルをファイル グループに追加します。 ファイルが追加された後、このストアド プロシージャは未復旧の設定をオフにして、データベースの復旧を完了します。 パラメーターは、ALTER DATABASE *database_name* ADD FILE のパラメーターと同じです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_data_file_recover_suspect_db [ @dbName= ] 'database'   
    , [ @filegroup = ] 'filegroup_name'   
    , [ @name = ] 'logical_file_name'   
    , [ @filename= ] 'os_file_name'   
    , [ @size = ] 'size'   
    , [ @maxsize = ] 'max_size'   
    , [ @filegrowth = ] 'growth_increment'  
```  
  
## <a name="arguments"></a>引数  
`[ @dbName = ] 'database_ '`データベースの名前を指定します。 *データベースのデータ*型は**sysname**で、既定値はありません。  
  
`[ @filegroup = ] 'filegroup_name_ '`ファイルを追加するファイルグループを指定します。 *filegroup_name*は**nvarchar (260)**,、既定値は NULL の場合、プライマリファイルを示します。  
  
`[ @name = ] 'logical_file_name_ '`ファイル[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照するためにで使用される名前を指定します。 サーバー内で一意な名前を指定する必要があります。 *logical_file_name*は**nvarchar (260)**,、既定値はありません。  
  
`[ @filename = ] 'os_file_name_ '`は、ファイルのオペレーティングシステムによって使用されるパスとファイル名です。 ファイルは[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンス上に存在している必要があります。 *os_file_name*は**nvarchar (260)**,、既定値はありません。  
  
`[ @size = ] 'size_ '`ファイルの初期サイズです。 *サイズ*は**nvarchar (20)**,、既定値は NULL です。 整数を指定します。小数を含めないでください。 サフィックス MB、KB を使用してメガバイト、キロバイトを指定できます。 既定値は MB です。 最小値は 512 KB です。 *Size*が指定されていない場合の既定値は 1 MB です。  
  
`[ @maxsize = ] 'max_size_ '`ファイルの拡張可能な最大サイズを指定します。 *max_size*は**nvarchar (20)**,、既定値は NULL です。 整数を指定します。小数を含めないでください。 サフィックス MB、KB を使用してメガバイト、キロバイトを指定できます。 既定値は MB です。  
  
 *Max_size*が指定されていない場合、ファイルはディスクがいっぱいになるまで拡張されます。 ディスク容量の上限まで近づくと、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーション ログが管理者に対して警告を発します。  
  
`[ @filegrowth = ] 'growth_increment_ '`新しい領域が必要になるたびにファイルに追加される領域のサイズです。 *growth_increment*は**nvarchar (20)**,、既定値は NULL です。 値0は、増加していないことを示します。 整数を指定します。小数を含めないでください。 値は MB、KB、またはパーセント (%) の単位で指定できます。 % が指定されている場合、増加率は、増分が発生した時点でのファイルのサイズに対して指定された割合になります。 サフィックス MB、KB、または % を付けないで数値を指定した場合の既定値は MB です。  
  
 *Growth_increment*が NULL の場合、既定値は10% で、最小値は 64 KB です。 指定されたサイズは、最も近い 64 KB 単位の値に切り上げられます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 実行権限は、既定では**sysadmin**固定サーバーロールのメンバーに与えています。 これらのアクセス許可は転送できません。  
  
## <a name="examples"></a>例  
 次の例では、 `db1`データベースは、ファイルグループ`fg1`の領域が不足しているため (エラー 1105)、回復中に suspect とマークされています。  
  
```  
USE master;  
GO  
EXEC sp_add_data_file_recover_suspect_db db1, fg1, file2,  
    'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\db1_file2.mdf', '1MB';  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-sql&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_add_log_file_recover_suspect_db &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-log-file-recover-suspect-db-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
