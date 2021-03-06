---
title: WillChangeRecordset および RecordsetChangeComplete イベント (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset::RecordsetChangeComplete
- RecordsetChangeComplete
- Recordset::WillChangeRecordset
- WillChangeRecordset
helpviewer_keywords:
- RecordsetChangeComplete event [ADO]
- WillChangeRecordset event [ADO]
ms.assetid: d5d44659-e0d9-46d9-a297-99c43555082f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dd4e2f1485c18ce1fecc76d4eb23aa4132d85329
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938682"
---
# <a name="willchangerecordset-and-recordsetchangecomplete-events-ado"></a>WillChangeRecordset および RecordsetChangeComplete イベント (ADO)
**WillChangeRecordset**イベントは、保留中の操作によって[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)が変更される前に呼び出されます。 **RecordsetChangeComplete**イベントは、**レコードセット**が変更された後に呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
WillChangeRecordset adReason, adStatus, pRecordset  
RecordsetChangeComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>パラメーター  
 *adReason*  
 このイベントの理由を指定する[Eventreason 列挙](../../../ado/reference/ado-api/eventreasonenum.md)値。 この値には、 **Adrsnrequery**、 **adrsnrequery 同期**、adrsnrequery、 **adRsnOpen**を指定できます。 ****  
  
 *adStatus*  
 [Eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md)状態の値です。  
  
 **WillChangeRecordset**が呼び出されると、イベントの原因となった操作が成功した場合、このパラメーターは**adstatusok**に設定されます。 このイベントが保留中の操作の取り消しを要求できない場合は、 **Adstatuscantdeny**に設定されます。  
  
 **RecordsetChangeComplete**が呼び出されると、このパラメーターは、イベントの原因となった操作が成功した場合は**adstatusok** 、操作が失敗した場合は**Adstatuserror curred** 、以前に受け入れられた**WillChangeRecordset**イベントに関連付けられている操作が取り消された場合は**adstatusok**に設定されます。  
  
 **WillChangeRecordset**が返される前に、このパラメーターを**adstatuscancel**に設定して保留中の操作の取り消しを要求するか、このパラメーターを adStatusUnwantedEvent に設定して、後続の通知が行われないようにします。  
  
 **WillChangeRecordset**または**RecordsetChangeComplete**がを返す前に、このパラメーターを**adStatusUnwantedEvent**に設定して、後続の通知が行われないようにします。  
  
 *pError*  
 [エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトです。 *Adstatus*の値が**adstatuserrorて**いる場合に発生したエラーについて説明します。それ以外の場合は設定されません。  
  
 *pRecordset*  
 **レコードセット**オブジェクトです。 このイベントが発生した**レコードセット**。  
  
## <a name="remarks"></a>解説  
 **WillChangeRecordset**または**RecordsetChangeComplete**イベントは、**レコードセット**の再[実行または](../../../ado/reference/ado-api/requery-method.md) [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドが原因で発生する可能性があります。  
  
 プロバイダーがブックマークをサポートしていない場合、プロバイダーから新しい行が取得されるたびに**RecordsetChange**イベント通知が発生します。 このイベントの頻度は、 **RecordsetCacheSize**プロパティによって異なります。  
  
 **AdReason**パラメーターを含むイベントのイベント通知を完全に停止するには、使用可能な**adReason**値ごとに**adstatus**パラメーターを**adStatusUnwantedEvent**に設定する必要があります。  
  
## <a name="see-also"></a>参照  
 [ADO Events モデルの例 (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)
