---
title: OLE DB API による機能強化された日付と時刻のサポート | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, date/time improvements
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef6334f6fe4671f2563add857f6dd58ce67a2840
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63237847"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>OLE DB API による機能強化された日付と時刻のサポート
  機能強化された日付や時刻をサポートする OLE DB API を次に示します。  
  
|Function|[説明]|  
|--------------|-----------------|  
|IAccessor:: CreateAccessor|アプリケーションで `datetime`、`datetime2`、および `smalldatetime` の各値を区別できるように、DBBINDING 構造体にフラグが用意されています。 詳細については、「[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)」を参照してください。|  
|IBCPSession::BCPColFmt|詳細については、「 [&#40;OLE DB および ODBC&#41;の拡張された日付/時刻型に対する一括コピーの変更](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)」を参照してください。|  
|ICommandWithParameters::GetParameterInfo|詳細については、「[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)」を参照してください。|  
|ICommandWithParameters::SetParameterinfo|詳細については、「[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)」を参照してください。|  
|IColumnsRowset::GetColumnsRowset|詳細については、「[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)」を参照してください。|  
|IColumnsInfo::GetColumnInfo|詳細については、「[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)」を参照してください。|  
|IDBSchemaRowset::GetRowset|影響を受けるスキーマ行セットの詳細については、「[日付と時刻およびスキーマ行セット](../native-client-ole-db-rowsets/rowsets.md)」を参照してください。|  
|IRowsetFastLoad|このインターフェイスは新しい日付と時刻の型をサポートしますが、インターフェイスに変更はありません。|  
|ITableDefinition::CreateTable|詳細については、「 [OLE DB の日付と時刻の機能強化に関するデータ型のサポート](data-type-support-for-ole-db-date-and-time-improvements.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [OLE DB &#40;の日付と時刻の改善&#41;](date-and-time-improvements-ole-db.md)  
  
  
