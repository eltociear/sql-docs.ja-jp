---
title: setFloat メソッド (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setFloat
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 26d861da-bb6a-4197-8b32-13dc7781c2bb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: eefde521b4a8dab594b4c42799f1b42e5bf445ff
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "68213671"
---
# <a name="setfloat-method-sqlservercallablestatement"></a>setFloat メソッド (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、渡された **float** 値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setFloat(java.lang.String sCol,  
                     float f)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 パラメーターの名前を含む**文字列**です。  
  
 *f*  
  
 **float** 値です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setFloat メソッドは、java.sql.CallableStatement インターフェイスの setFloat メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
