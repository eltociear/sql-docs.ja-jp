---
title: sp_pkeys (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_pkeys
- sp_pkeys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_pkeys
ms.assetid: e614c75d-847b-4726-8f6f-cd18de688eda
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8ed0e041a6aa36027613059f16f3902bdb664aeb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68056426"
---
# <a name="sp_pkeys-transact-sql"></a>sp_pkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在の環境における、単一のテーブルに関する主キーの情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_pkeys [ @table_name = ] 'name'       
    [ , [ @table_owner = ] 'owner' ]   
    [ , [ @table_qualifier = ] 'qualifier' ]  
```  
  
## <a name="arguments"></a>引数  
 [ @table_name= ]'*name*'  
 情報を返すテーブルを指定します。 *名前*は**sysname**,、既定値はありません。 ワイルドカードのパターンマッチングはサポートされていません。  
  
 [ @table_owner= ]'*owner*'  
 指定したテーブルのテーブル所有者を指定します。 *owner*は**sysname**,、既定値は NULL です。 ワイルドカードのパターンマッチングはサポートされていません。 *Owner*が指定されていない場合、基になる DBMS の既定のテーブル可視性ルールが適用されます。  
  
 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、指定された名前のテーブルが現在のユーザーによって所有されている場合、そのテーブルの列が返されます。 *所有者*が指定されておらず、現在のユーザーが指定された*名前*のテーブルを所有していない場合、このプロシージャは、データベース所有者が所有する、指定された*名前*のテーブルを検索します。 そのテーブルが存在する場合、そのテーブルの列が返されます。  
  
 [ @table_qualifier= ]'*qualifier*'  
 テーブル修飾子を示します。 *修飾子*は**sysname**,、既定値は NULL です。 さまざまな DBMS 製品では、3つの要素で構成するテーブル (_修飾子_) がサポート**しています。**_所有者_**。**_名前_)。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、この列はデータベース名を表します。 一部の製品では、テーブルのデータベース環境のサーバー名を表します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|TABLE_QUALIFIER|**sysname**|テーブル修飾子の名前。 このフィールドは NULL にすることができます。|  
|TABLE_OWNER|**sysname**|テーブル所有者の名前。 このフィールドは常に値を返します。|  
|TABLE_NAME|**sysname**|テーブルの名前。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この列は、sysobjects テーブルに記録されているテーブル名を表します。 このフィールドは常に値を返します。|  
|COLUMN_NAME|**sysname**|返される TABLE_NAME の各列の列名。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この列は、sys.columns テーブルに記録されている列名を表します。 このフィールドは常に値を返します。|  
|KEY_SEQ|**smallint**|複数列の主キーの列のシーケンス番号。|  
|PK_NAME|**sysname**|主キー識別子。 データソースに該当しない場合は NULL を返します。|  
  
## <a name="remarks"></a>解説  
 sp_pkeys では、PRIMARY KEY 制約で明示的に定義された列に関する情報が返されます。 すべてのシステムが明示的に名前が付けられた主キーをサポートしているわけではないため、ゲートウェイの実装者が主キーの構成を決定します。 "主キー" という用語は、テーブルの論理主キーを指していることに注意してください。 論理主キーとして示されているすべてのキーには、一意のインデックスが定義されている必要があります。 sp_statistics には、この一意なインデックスも返されます。  
  
 sp_pkeys ストアド プロシージャは、ODBC の SQLPrimaryKeys に相当します。 返される結果は、TABLE_QUALIFIER、TABLE_OWNER、TABLE_NAME、および KEY_SEQ の値で並べ替えられます。  
  
## <a name="permissions"></a>アクセス許可  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="examples"></a>例  
 次の例では、`HumanResources.Department` データベースの `AdventureWorks2012` テーブルの主キーを取得します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_pkeys @table_name = N'Department'  
    ,@table_owner = N'HumanResources';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、`DimAccount` データベースの `AdventureWorksPDW2012` テーブルの主キーを取得します。 このメソッドは、テーブルに主キーがないことを示すゼロ行を返します。  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_pkeys @table_name = N'DimAccount;  
```  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のカタログストアドプロシージャ](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

