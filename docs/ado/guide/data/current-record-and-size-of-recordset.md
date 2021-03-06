---
title: レコードセットの現在のレコードとサイズ |Microsoft Docs
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
ms.assetid: e63ff331-8655-4be7-82c6-e6cd6cc9d16d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a01e17ea9c786a724e5869a28bf4d8927b58ac81
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925694"
---
# <a name="current-record-and-size-of-recordset"></a>レコードセットの現在のレコードとサイズ
ここでは、JScript コード例のサンプル**レコード**セット内のカーソルの現在位置を検索して、[レコードセットを返す](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)方法について説明します。  
  
## <a name="current-record"></a>現在のレコード  
 データセット内の現在のレコードは、**レコードセット**オブジェクトのカーソル位置が指すものに対応します。 レコードセットを呼び出した結果として **、レコードセットオブジェクトが**データソースから返された場合、このカーソルは最初のレコードをポイントするように設定**** されています。この場合、 **Open**、 **Command. execute**、または**connection. execute** **(接続を含む)** を呼び出します。 サンプルデータセットでは、最初の現在のレコードは "あなた Bob's 有機理屈 Pears" 項目です。  
  
## <a name="size-of-recordset"></a>レコードセットのサイズ  
 **レコードセット**オブジェクトのサイズを調べるには、**レコードセットの RecordCount**プロパティの値を取得します。 この値は、**レコードセット**内のレコードの数を示す long 整数です。 データセットが Microsoft SQL Server の OLEDB プロバイダーから返された場合、この値によって返される行の数が示されます。 閉じた**レコードセット**の**RecordCount**プロパティを読み取ると、エラーが発生します。  
  
 レコードの数を特定できない場合、プロパティの値は-1 になります。  
  
 **RecordCount**プロパティの値は、プロバイダーの機能と使用されるカーソルの種類にも依存します。 順方向専用カーソルの場合、値は-1 です。 静的カーソルまたはキーセットカーソルの場合、この値は**レコードセット**オブジェクトで返される実際のレコード数になります。 動的カーソルの場合、データソースに応じて、値は-1 または実際のレコード数になります。  
  
 **Recordcount**をサポートするカーソルは、処理が困難であり、カーソルが**recordcount**をサポートしていないため、より多くのコンピューティング能力が必要です。 レコードの数を知る必要がない場合は、さまざまなカーソルの種類を使用すると、特に大規模なデータセットを処理する必要がある場合に、アプリケーションのパフォーマンスを向上させることができます。  
  
 場合によっては、最初にデータソースからすべてのレコードをフェッチせずに、プロバイダーまたはカーソルが**RecordCount**値を特定できないことがあります。 正確なカウントを確認するには、**レコードセット**を呼び出します。**レコードセットを**呼び出す前に、 **MoveLast**メソッド。  
  
 [JScript コード例](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)を使用して取得したサンプルの**レコードセット**オブジェクトは、順方向専用カーソルを使用するため、このオブジェクトで**RecordCount**を呼び出すと、常に-1 になります。 **レコードセット**を呼び出すコード行を変更する場合は、次の例に示すように、メソッドを**開き**ます。 **RecordCount**プロパティは、フェッチされた実際のレコード数を返します。  
  
```  
oRs.Open sSQL, sCnStr, adOpenStatic, adLockOptimistic, adCmdText   
```  
  
 これは、 [Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)を使用した静的カーソルが**RecordCount**をサポートするためです。 この例では5つのレコードがあるため、 **RecordCount**は5の値を生成する必要があります。  
  
 ここでは、次のトピックについて説明します。  
  
 [レコードセットの境界](../../../ado/guide/data/boundaries-of-a-recordset.md)
