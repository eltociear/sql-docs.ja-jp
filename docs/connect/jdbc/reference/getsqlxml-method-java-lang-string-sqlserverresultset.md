---
title: getSQLXML メソッド (java.lang.String) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab9c7b10-026f-4a51-8d60-e6871d1abd02
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ecf5030c4722f2e5681cb199993a48fea0e22462
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67979684"
---
# <a name="getsqlxml-method-javalangstring-sqlserverresultset"></a>getSQLXML (java.lang.String) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの現在の行にある指定された列の値が、SQLXML オブジェクトとして取得されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.sql.SQLXML getSQLXML(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 列ラベルを示す **String** です。  
  
## <a name="return-value"></a>戻り値  
 ASQLXML オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getSQLXML メソッドは、java.sql.ResultSet インターフェイスの getSQLXML メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [getSQLXML メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
