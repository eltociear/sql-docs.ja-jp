---
title: sql_modules (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 11/06/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sql_modules_TSQL
- sql_modules
- sql_modules_TSQL
- sys.sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_modules catalog view
ms.assetid: 23d3ccd2-f356-4d89-a2cd-bee381243f99
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8f3e007a0676afd507af54e3b3406297cf40042e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108988"
---
# <a name="syssql_modules-transact-sql"></a>sys.sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ネイティブコンパイルのスカラーユーザー定義関数を含む、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SQL 言語定義モジュールであるオブジェクトごとに1行の値を返します。 型 P、RF、V、TR、FN、IF、TF、および R のオブジェクトには、SQL モジュールが関連付けられています。 スタンドアロンの既定値である種類 D のオブジェクトにも、このビューで SQL モジュール定義が関連付けられています。 これらの型の詳細については、「 [sys. objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)カタログビューの**type**列」を参照してください。  
  
 詳しくは、「[インメモリ OLTP でのユーザー定義のスカラー関数](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)」をご覧ください。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|このオブジェクトが属するオブジェクトの ID です。 データベース内で一意です。|  
|**カスタム**|**nvarchar(max)**|このモジュールを定義する SQL テキスト。 この値は[OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md)組み込み関数を使用して取得することもできます。<br /><br /> NULL = 暗号化されています。|  
|**uses_ansi_nulls**|**bit**|モジュールは、SET ANSI_NULLS ON で作成されました。<br /><br /> ルールと既定値の場合、は常に0になります。|  
|**uses_quoted_identifier**|**bit**|モジュールは QUOTED_IDENTIFIER ON に設定して作成されました。|  
|**is_schema_bound**|**bit**|モジュールは SCHEMABINDING オプションを使用して作成されました。<br /><br /> ネイティブコンパイルストアドプロシージャの場合は、常に値1が格納されます。|  
|**uses_database_collation**|**bit**|スキーマ バインドのモジュール定義が適切な評価のためにデータベースの既定の照合順序に依存する場合は 1 になります。それ以外の場合は 0 になります。 このような依存関係によって、データベースの既定の照合順序が変更されることはありません。|  
|**is_recompiled**|**bit**|プロシージャは、RECOMPILE オプションを使用して作成されました。|  
|**null_on_null_input**|**bit**|モジュールは、任意の NULL 入力上で NULL 出力を生成するように宣言されました。|  
|**execute_as_principal_id**|**通り**|実行データベースプリンシパルの ID。<br /><br /> 既定では NULL、または EXECUTE AS CALLER の場合は NULL です。<br /><br /> [SELF として実行するか、プリンシパルとし\<て実行する場合> 指定されたプリンシパルの ID です。<br /><br /> -2 = EXECUTE AS OWNER。|  
|**uses_native_compilation**|**bit**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]から[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]。<br /><br /> 0 = ネイティブでコンパイルされていない<br /><br /> 1 = ネイティブコンパイル<br /><br /> 既定値は 0 です。|  
|**is_inlineable**|**bit**|**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssqlv15-md.md)] 以降。<br/><br />モジュールがインライン化可能かどうかを示します。 Inlineability は、[ここで](../user-defined-functions/scalar-udf-inlining.md#inlineable-scalar-udfs-requirements)指定した条件に基づいています。<br /><br /> 0 = not インライン化可能<br /><br /> 1 = はインライン化可能です。 <br /><br /> スカラー Udf の場合、UDF がインライン化可能の場合、値は1になり、それ以外の場合は0になります。 インライン Tvf の場合は値1、その他のすべてのモジュール型の場合は0を格納します。<br />|  
|**inline_type**|**bit**|**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssqlv15-md.md)] 以降。<br /><br />現在モジュールに対してインライン展開が有効になっているかどうかを示します。 <br /><br />0 = インライン展開は無効になっています<br /><br /> 1 = インライン展開が有効になっています。<br /><br /> スカラー Udf では、インライン展開が有効になっている場合 (明示的または暗黙的)、値は1になります。 インライン Tvf の場合、値は常に1になり、その他のモジュールの種類では0になります。<br />|  

  
## <a name="remarks"></a>解説  
 既定の制約の SQL 式、D 型のオブジェクトは、 [default_constraints](../../relational-databases/system-catalog-views/sys-default-constraints-transact-sql.md)カタログビューにあります。 CHECK 制約の SQL 式、C 型のオブジェクトは、 [check_constraints](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)カタログビューにあります。  
  
 この情報については、「 [sys. dm_db_uncontained_entities &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>例  
 次の例では、現在のデータベース内の各モジュールの名前、型、および定義を返します。  
  
```  
SELECT sm.object_id, OBJECT_NAME(sm.object_id) AS object_name, o.type, o.type_desc, sm.definition  
FROM sys.sql_modules AS sm  
JOIN sys.objects AS o ON sm.object_id = o.object_id  
ORDER BY o.type;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [SQL Server システムカタログに対するクエリについてよく寄せられる質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
