---
title: データを検査するためのサンプルレコードセットMicrosoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record location [ADO]
- current record [ADO]
ms.assetid: e770e626-68b1-4ddf-a217-d7b30311e2ee
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1882c5298d92e17a7ddaa165288fddfab7fdb02b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924302"
---
# <a name="sample-recordset-for-examining-data"></a>データを確認するためのサンプルのレコードセット
まず、Microsoft SQL Server で Northwind サンプルデータベースに対して実行される、次の SQL クエリを使用して返された**レコードセット**オブジェクトを見てみましょう。  
  
```  
SELECT ProductID,ProductName,UnitPrice   
FROM Products   
WHERE CategoryID = 7    
```  
  
 結果の**レコードセット**オブジェクトには、次の表に示すように、データベースで生成されたすべてのが含まれます。  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|7|あなた Bob's 有機理屈 Pears|30.0000|  
|14|Tofu|23.2500|  
|28|Rssle ラウト|45.6000|  
|51|Manjimup 理屈リンゴ|53.0000|  
|74|Longlife Tofu|10.0000|  
  
 これらの結果を自分で取得することに関心がある場合は、次の JScript の例を試してください。  
  
-   [レコードセットを返す JScript の例](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)
