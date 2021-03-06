---
title: Change Tracking 関数 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], change tracking
- change tracking [SQL Server], functions
ms.assetid: 04eb53c4-8b69-414e-9696-185d227fea35
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8dc2dceec177922369fe2bbef74bafeeef2ca27c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68042961"
---
# <a name="change-tracking-functions-transact-sql"></a>変更追跡関数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  変更の追跡では、追跡対象のテーブルに適用された挿入、更新、削除の各アクティビティを記録して、変更の詳細を簡単に使用できるリレーショナル形式で提供します。 次の関数は、変更に関する情報を返します。  
  
|Function|[説明]|  
|--------------|-----------------|  
|[CHANGETABLE (変更)](../../relational-databases/system-functions/changetable-transact-sql.md)|指定したバージョン以降に発生したテーブルに対するすべての変更の追跡情報を返します。|  
|[CHANGETABLE (VERSION)](../../relational-databases/system-functions/changetable-transact-sql.md)|指定された行の最新の変更追跡情報を返します。|  
|[CHANGE_TRACKING_MIN_VALID_VERSION ()](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)|[CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md)関数を使用するときに、指定されたテーブルから変更追跡情報を取得するために有効な最小バージョンを返します。|  
|[CHANGE_TRACKING_CURRENT_VERSION](../../relational-databases/system-functions/change-tracking-current-version-transact-sql.md)|最後にコミットされたトランザクションに関連付けられているバージョンを取得します。 このバージョンは、次に CHANGETABLE を使用して変更を列挙するときに使用できます。|  
|[CHANGE_TRACKING_IS_COLUMN_IN_MASK](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md)|CHANGETABLE (CHANGES...) 関数によって返される SYS_CHANGE_COLUMNS 値を解釈します。|  
|[WITH CHANGE_TRACKING_CONTEXT](../../relational-databases/system-functions/with-change-tracking-context-transact-sql.md)|アプリケーションがデータを変更するときに、発信元 ID などの変更コンテキストを指定できるようにします。|  
  
## <a name="see-also"></a>参照  
 [データ変更の追跡 &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
