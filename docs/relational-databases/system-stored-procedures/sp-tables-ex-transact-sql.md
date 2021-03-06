---
title: sp_tables_ex (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_tables_ex
- sp_tables_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tables_ex
ms.assetid: 33755c33-7e1e-4ef7-af14-a9cebb1e2ed4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 77d1512c472005e59909342c94a88c4464c4fe5c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096073"
---
# <a name="sp_tables_ex-transact-sql"></a>sp_tables_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたリンクサーバーからテーブルに関するテーブル情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_tables_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]  
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @table_type = ] 'table_type' ]   
     [ , [@fUsePattern = ] 'fUsePattern' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @table_server = ] 'table_server'`テーブル情報を返すリンクサーバーの名前を指定します。 *table_server*は**sysname**であり、既定値はありません。  
  
``[ , [ @table_name = ] 'table_name']``データ型情報を返すテーブルの名前を指定します。 *table_name*は**sysname**,、既定値は NULL です。  
  
`[ @table_schema = ] 'table_schema']`テーブルスキーマを示します。 *table_schema*は**sysname**,、既定値は NULL です。  
  
`[ @table_catalog = ] 'table_catalog'`指定した*table_name*が存在するデータベースの名前を指定します。 *table_catalog*は**sysname**,、既定値は NULL です。  
  
`[ @table_type = ] 'table_type'`返されるテーブルの型を示します。 *table_type*は**sysname**で、既定値は NULL です。次のいずれかの値を指定できます。  
  
|値|[説明]|  
|-----------|-----------------|  
|**エイリアス**|エイリアスの名前。|  
|**GLOBAL TEMPORARY**|システム全体で使用可能な一時テーブルの名前。|  
|**LOCAL TEMPORARY**|現在のジョブでのみ使用可能な一時テーブルの名前。|  
|**SYNONYM**|シノニムの名前。|  
|**システムテーブル**|システム テーブルの名前です。|  
|**システムビュー**|システムビューの名前。|  
|**TABLE**|ユーザーテーブルの名前。|  
|**VIEW**|ビューの名前。|  
  
`[ @fUsePattern = ] 'fUsePattern'`**_**、 **%**、 **[**、および **]** 文字をワイルドカード文字として解釈するかどうかを決定します。 有効な値は 0 (パターン一致がオフ) および 1 (パターン一致がオン) です。 *Fusepattern*は**ビット**,、既定値は1です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|テーブル修飾子の名前。 さまざまな DBMS 製品では、3つの要素で構成するテーブル (_修飾子_) がサポート**しています。**_所有者_**。**_名前_)。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、この列はデータベース名を表します。 その他の製品では、テーブルのデータベース環境のサーバー名を表します。 このフィールドは NULL にすることができます。|  
|**TABLE_SCHEM**|**sysname**|テーブル所有者の名前。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、この列は、テーブルを作成したデータベースユーザーの名前を表します。 このフィールドは常に値を返します。|  
|**TABLE_NAME**|**sysname**|テーブル名。 このフィールドは常に値を返します。|  
|**TABLE_TYPE**|**varchar(32)**|テーブル、システムテーブル、またはビュー。|  
|**」**|**varchar (254)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はこの列の値を返しません。|  
  
## <a name="remarks"></a>解説  
 **sp_tables_ex**は、 *table_server*に対応する OLE DB プロバイダーの**IDBSchemaRowset**インターフェイスのテーブル行セットを照会することによって実行されます。 返される行を制限するために、 *table_name*、 *table_schema*、 *table_catalog*、および*列*の各パラメーターがこのインターフェイスに渡されます。  
  
 指定されたリンクサーバーの OLE DB プロバイダーが**IDBSchemaRowset**インターフェイスの tables 行セットをサポートしていない場合、 **sp_tables_ex**は空の結果セットを返します。  
  
## <a name="permissions"></a>アクセス許可  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="examples"></a>例  
 次の例では、 `HumanResources` [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] `LONDON2`リンクサーバー上のデータベースのスキーマに含まれているテーブルに関する情報を返します。  
  
```  
EXEC sp_tables_ex @table_server = 'LONDON2',   
@table_catalog = 'AdventureWorks2012',   
@table_schema = 'HumanResources',   
@table_type = 'TABLE';  
```  
  
## <a name="see-also"></a>参照  
 [分散クエリストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_columns_ex &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [sp_column_privileges &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_table_privileges &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
