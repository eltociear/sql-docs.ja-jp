---
title: getCharacterStream メソッド (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getCharacterStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4f9f230d-be4c-469a-b3dc-f24531429aae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c0dd69211302a10fe72fc2742cbcd8b6bda7c933
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "68213695"
---
# <a name="getcharacterstream-method-int"></a>getCharacterStream (int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの現在の行にある指定された列インデックスの値が、java.io.Reader オブジェクトとして取得されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.Reader getCharacterStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 列インデックスを示す **int** です。  
  
## <a name="return-value"></a>戻り値  
 Reader オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getCharacterStream メソッドは、java.sql.ResultSet インターフェイスの getCharacterStream メソッドで規定されています。  
  
 このメソッドでは、nchar、nvarchar、nvarchar(max)、ntext などの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の Unicode 文字データ型のみが読み取られます。 ASCII 文字型などのその他のデータ型では、例外がスローされます。 ASCII データ型を読み取るには、[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md) メソッドを使用します。  
  
## <a name="see-also"></a>参照  
 [getCharacterStream メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
