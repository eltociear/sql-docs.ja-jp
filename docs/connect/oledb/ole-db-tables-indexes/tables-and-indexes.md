---
title: テーブルとインデックス | Microsoft Docs
description: OLE DB Driver for SQL Server を使用したテーブルとインデックスの作成、変更、および削除
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- OLE DB Driver for SQL Server, tables
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 0fc8aeed348f64c17894fa3432a7a81274ffbea4
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "68015244"
---
# <a name="tables-and-indexes"></a>テーブルとインデックス
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server では、**IIndexDefinition** インターフェイスと **ITableDefinition** インターフェイスが公開されます。コンシューマーは、これらのインターフェイスにより [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のテーブルとインデックスを作成、変更、および削除できます。 有効なテーブルやインデックスの定義は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のバージョンによって異なります。  
  
 テーブルやインデックスを作成または削除できるかどうかは、コンシューマー アプリケーション ユーザーの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アクセス権によって決まります。 テーブルの削除は、宣言参照整合性制約やその他の要因の指定によってさらに制約できます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を対象とする多くのアプリケーションでは、このような OLE DB Driver for SQL Server インターフェイスではなく、SQL-DMO が使用されます。 SQL-DMO は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のすべての管理機能をサポートする OLE オートメーション オブジェクトの集まりです。 複数の OLE DB プロバイダーを対象とするアプリケーションでは、さまざまな OLE DB プロバイダーでサポートされる、これらの汎用 OLE DB インターフェイスを使用します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、プロバイダー固有の DBPROPSET_SQLSERVERCOLUMN プロパティ セットで、次のプロパティを定義しています。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|型: VT_BSTR<br /><br /> R/W:Write<br /><br /> 既定値は[Null]<br /><br /> 説明:このプロパティは、**ITableDefinition** でのみ使用されます。 このプロパティに指定した文字列は、[CREATE TABLE](../../../t-sql/statements/create-table-transact-sql.md) ステートメントの作成時に<br /><br /> ステートメントの使用などがあります。|  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [SQL Server テーブルの作成](../../oledb/ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [SQL Server テーブルへの列の追加](../../oledb/ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [SQL Server テーブルからの列の削除](../../oledb/ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [SQL Server テーブルの削除](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [SQL Server インデックスの作成](../../oledb/ole-db-tables-indexes/creating-sql-server-indexes.md)  
  
-   [SQL Server インデックスの削除](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server のプログラミング](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [DROP TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/create-index-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
