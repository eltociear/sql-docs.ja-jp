---
title: fn_cdc_get_max_lsn (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_get_max_lsn
- fn_cdc_get_max_lsn
- fn_cdc_get_max_lsn_TSQL
- sys.fn_cdc_get_max_lsn_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_get_max_lsn
- sys.fn_cdc_get_max_lsn
ms.assetid: 93f3a4c8-b91f-4ebb-8e96-9397bb3a1c43
author: rothja
ms.author: jroth
ms.openlocfilehash: c51a69eb3604b937b9bf2aaf9a09aa383f2c1490
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046453"
---
# <a name="sysfn_cdc_get_max_lsn-transact-sql"></a>sys.fn_cdc_get_max_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [Lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)システムテーブルの start_lsn 列の最大ログシーケンス番号 (LSN) を返します。 この関数を使用すると、キャプチャインスタンスの変更データキャプチャタイムラインの上端を返すことができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_cdc_get_max_lsn ()  
```  
  
## <a name="return-types"></a>戻り値の型  
 **binary (10)**  
  
## <a name="remarks"></a>解説  
 この関数は、 [lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)テーブルの start_lsn 列の最大 LSN を返します。 変更がデータベース変更テーブルに反映されたときに、キャプチャ プロセスで最後に処理された LSN になります。 データベースに対して定義されているキャプチャインスタンスに関連付けられているすべてのタイムラインの高エンドポイントとして機能します。  
  
 関数は、通常、クエリ間隔に対して適切な高いエンドポイントを取得するために使用されます。  
  
## <a name="permissions"></a>アクセス許可  
 public データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
  
### <a name="a-returning-the-maximum-lsn-value"></a>A. 最大 LSN 値を取得する  
 次の例は、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベース内のすべてのキャプチャ インスタンスの最大 LSN を返します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT sys.fn_cdc_get_max_lsn()AS max_lsn;  
```  
  
### <a name="b-setting-the-high-endpoint-of-a-query-range"></a>B. クエリ範囲の上限を設定する  
 次の例では、`sys.fn_cdc_get_max_lsn` によって返された最大 LSN を使用して、キャプチャ インスタンス `HumanResources_Employee` に対するクエリ範囲の上端を設定します。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10);  
SET @from_lsn = sys.fn_cdc_get_min_lsn(N'HumanResources_Employee');  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
SELECT * FROM cdc.fn_cdc_get_all_changes_HumanResources_Employee(@from_lsn, @to_lsn, 'all');  
GO  
```  
  
## <a name="see-also"></a>参照  
 [fn_cdc_get_min_lsn &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-cdc-get-min-lsn-transact-sql.md)   
 [トランザクションログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)  
  
  
