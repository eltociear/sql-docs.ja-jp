---
title: getSchemas メソッド (String, String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 672171ac-976f-4605-9bee-2a5e141d92cb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c5f380123f0fc3f2b23a82b72871622e98c0f185
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67980092"
---
# <a name="getschemas-method-string-string"></a>getSchemas (String, String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたカタログ名とスキーマ名を使用して、現在のデータベースで使用できるスキーマ名を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public ResultSet getSchemas(java.lang.String catalog,  
                       java.lang.String schemaPattern)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *catalog*  
  
 データベース内のカタログの名前です。 空の文字列 "" の場合、結果にはカタログのないスキーマが含まれます。 **null** の場合、カタログ名は検索に使用されません。  
  
 *schemaPattern*  
  
 スキーマの名前です。 **null** の場合、スキーマ名は検索に使用されません。  
  
## <a name="return-value"></a>戻り値  
 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getSchemas メソッドは、java.sql.DatabaseMetaData インターフェイスの getSchemas メソッドで規定されています。  
  
 getSchemas メソッドによって返される結果セットには、次の情報が含まれます。  
  
|Name|Type|説明|  
|----------|----------|-----------------|  
|TABLE_SCHEM|**String**|スキーマの名前です。|  
|TABLE_CATALOG|**String**|スキーマのカタログ名です。|  
  
 結果は、TABLE_CATALOG、TABLE_SCHEM の順に順序付けされます。 各行の最初の列は TABLE_SCHEM、次の列は TABLE_CATALOG です。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
