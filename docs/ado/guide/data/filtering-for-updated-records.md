---
title: 更新されたレコードのフィルター処理 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- filtering for updated records [ADO]
ms.assetid: 4a798921-d7bb-47c9-a252-550fd9463ec9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0b5afe84664719da5a1dbc7777aef524be28c459
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925335"
---
# <a name="filtering-for-updated-records"></a>更新されたレコードのフィルター処理
UpdateBatch を呼び出す前に、レコードセットフィルタープロパティを使用して、レコードセットが開かれた後、または UpdateBatch を最後に呼び出した後に変更されたレコードのみを表示することができます。 これを行うには、次のセクションのコード例に示すように、フィルターを adFilterPendingRecords に設定して、更新するレコードの数を決定します。  
  
## <a name="remarks"></a>解説  
 この例では、以前の UpdateBatch の例を拡張します。この例では、UpdateBatch を呼び出す直前にレコードセットをフィルター処理して、レコードが変更されるユーザーを表示し、ユーザーが更新をキャンセルできるようにします (CancelBatch メソッドを使用)。  
  
```  
'BeginFilterPend  
    '...  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
  
    ' Change value of Phone field for first record in Recordset, saving value  
    ' for later restoration.  
    intId = objRs1("ShipperId")  
    sPhone = objRs1("Phone")  
  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Add two new records  
    For i = 0 To 1  
        objRs1.AddNew  
        objRs1(1) = "New Shipper #" & CStr((i + 1))  
        objRs1(2) = "(nnn) 555-" & i & i & i & i  
    Next i  
  
    objRs1.Filter = adFilterPendingRecords  
  
    MsgBox "There are " & objRs1.RecordCount & " records pending.", _  
            , "Filter Pending"  
  
    ' Cancel the updates  
    objRs1.CancelBatch  
'EndFilterPend  
```  
  
## <a name="see-also"></a>参照  
 [バッチ モード](../../../ado/guide/data/batch-mode.md)
