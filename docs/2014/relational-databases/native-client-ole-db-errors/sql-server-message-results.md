---
title: SQL Server メッセージの結果 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff604f4c5d66a5742868e25ba05ca6b4528ddb1a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206712"
---
# <a name="sql-server-message-results"></a>SQL Server のメッセージ結果
  次[!INCLUDE[tsql](../../includes/tsql-md.md)]のステートメントは、Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーの行セット、または実行時に影響を受ける行の数を生成しません。  
  
-   PRINT  
  
-   重大度が 10 以下の RAISERROR  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 上記のステートメントでは、行セットや行数の結果が返されるのではなく、ステートメントから 1 つ以上の情報メッセージが返されるか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から情報メッセージが返されます。 正常に実行される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と、native client OLE DB プロバイダーは S_OK を返します。メッセージは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、native client OLE DB プロバイダーコンシューマーが使用できます。  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client OLE DB プロバイダーは S_OK を返し、多く[!INCLUDE[tsql](../../includes/tsql-md.md)]のステートメントの実行後、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client OLE DB プロバイダーメンバー関数のコンシューマー実行に従って、1つまたは複数の情報メッセージを使用できるようにします。  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーコンシューマーは、クエリテキストを動的に指定できるようにするため、リターンコードの値、返される**IRowset**または**IMultipleResults**インターフェイス参照の有無、または影響を受ける行の数に関係なく、すべてのメンバー関数の実行後にエラーインターフェイスをチェックする必要があります。  
  
## <a name="see-also"></a>参照  
 [エラー](errors.md)  
  
  
