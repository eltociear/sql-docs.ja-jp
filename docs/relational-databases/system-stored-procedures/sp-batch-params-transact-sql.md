---
title: sp_batch_params (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_batch_params
- sp_batch_params_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_batch_params
ms.assetid: 7b92fe9e-e755-4b7a-8a15-822c58a813d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9a5b4ac7c5e1e8d3c136f99475fa7a17ebd8b002
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001810"
---
# <a name="sp_batch_params-transact-sql"></a>sp_batch_params (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[tsql](../../includes/tsql-md.md)]バッチに含まれるパラメーターに関する情報を含む行セットを返します。 **sp_batch_params**は、指定されたバッチを解析し、埋め込みパラメーター値に関する情報を返します。 バッチの実行や、実行環境の変更は行いません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_batch_params [ [ @tsqlbatch = ] 'tsqlbatch' ]   
```  
  
## <a name="arguments"></a>引数  
`[ @tsqlbatch = ] 'tsqlbatch'`は、パラメーター情報を必要と[!INCLUDE[tsql](../../includes/tsql-md.md)]するステートメントまたはバッチを含む Unicode 文字列です。 *tsqlbatch*は**nvarchar (max)** または**nvarchar (max)** に暗黙的に変換できます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**PARAMETER_NAME**|**sysname**|バッチ内で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]検出されたパラメーターの名前。|  
|**COLUMN_TYPE**|**smallint**|このフィールドは、次のいずれかの値を返します。<br /><br /> 0 = SQL_PARAM_TYPE_UNKNOWN<br /><br /> 1 = SQL_PARAM_TYPE_INPUT<br /><br /> 2 = SQL_PARAM_TYPE_OUTPUT<br /><br /> 3 = SQL_RESULT_COL<br /><br /> 4 = SQL_PARAM_OUTPUT<br /><br /> 5 = SQL_RETURN_VALUE<br /><br /> この列は常に 0 です。|  
|**DATA_TYPE**|**smallint**|パラメーターのデータ型 (ODBC データ型の整数コード)。 このデータ型を ISO 型にマップできない場合、値は NULL になります。 ネイティブデータ型の名前が**TYPE_NAME**列に返されます。 この値は常に NULL です。|  
|**TYPE_NAME**|**sysname**|基になる DBMS によって表された、データ型を表す文字列です。 この値は NULL です。|  
|**精度**|**int**|有効桁数。 **有効桁数**列の戻り値は、10進数値です。|  
|**LENGTH**|**int**|データの転送サイズです。 この値は NULL です。|  
|**段階**|**smallint**|小数点の右側の桁数。 この値は NULL です。|  
|**RADIX**|**smallint**|数値型の基数です。 この値は NULL です。|  
|**NULLABLE**|**smallint**|Null 値の許容属性を指定します。<br /><br /> 1 = NULL 値を許容するパラメーターのデータ型が作成されます。<br /><br /> 0 = Null 値は使用できません。<br /><br /> この値は NULL です。|  
|**SQL_DATA_TYPE**|**smallint**|記述子の TYPE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フィールドに表示されるシステムデータ型の値。 この列は、 **datetime**データ型と ISO **interval**データ型を除き、 **DATA_TYPE**列と同じです。 この列は常に値が返されます。 この値は NULL です。|  
|**SQL_DATETIME_SUB**|**smallint**|**SQL_DATA_TYPE**の値が SQL_DATETIME または SQL_INTERVAL の場合は、 **DATETIME**または ISO **interval**サブコード。 
  **datetime** および **ISO interval** 以外のデータ型の場合、この列は NULL です。 この値は NULL です。|  
|**CHAR_OCTET_LENGTH**|**int**|**文字**または**バイナリ**データ型パラメーターの最大長 (バイト単位)。 他のすべてのデータ型については、この列は NULL を返します。 この値は常に NULL です。|  
|**ORDINAL_POSITION**|**int**|バッチ内のパラメーターの序数位置。 パラメーター名が複数回繰り返される場合は、この列には最初のオカレンスの序数が入ります。 最初のパラメーターには序数 1 が設定されます。 この列は常に値が返されます。|  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_batch_params**を実行する権限は、 **public**に与えられます。  
  
## <a name="examples"></a>例  
 この例では、クエリが `sp_batch_params` に渡されています。 結果セットには、埋め込みパラメーター値の一覧が列挙されます。  
  
```  
DECLARE @SQLString nvarchar(500);  
/* Build the SQL string */  
SET @SQLString =  
     N'SELECT * FROM AdventureWorks2012.HumanResources.Employee   
     WHERE BusinessEntityID = @BusinessEntityID';  
EXECUTE sp_batch_params @SQLString;  
```  
  
## <a name="see-also"></a>参照  
 [ストアドプロシージャの実行](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [ストアドプロシージャの実行方法に関するトピック &#40;ODBC&#41;](https://msdn.microsoft.com/library/c2220182-a23d-4475-b353-77a77ab613d6)   
 [ストアドプロシージャの実行 &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/stored-procedures-running.md)  
  
  
