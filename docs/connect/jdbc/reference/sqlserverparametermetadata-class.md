---
title: SQLServerParameterMetaData クラス | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 546290e0-9411-4a2b-aa36-61251e70e9cf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b0721341cbf095e0aa27fab392c8d03f72dc2e3a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67970893"
---
# <a name="sqlserverparametermetadata-class"></a>SQLServerParameterMetaData クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  準備されたステートメントのパラメーターのメタデータを表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** java.lang.Object  
  
 **実装:** java.sql.ParameterMetaData  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerParameterMetaData  
```  
  
## <a name="remarks"></a>解説  
 パラメーターのメタデータを取得するために、準備されたステートメントは SET FMT ONLY を指定して実行されます。 呼び出し可能ステートメントで sp_sproc_columns が呼び出され、プロシージャ パラメーターの名前とメタデータが取得されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerParameterMetaData のメンバー](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
