---
title: MoveRecordOptionsEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- MoveRecordOptionsEnum
helpviewer_keywords:
- MoveRecordOptionsEnum enumeration [ADO]
ms.assetid: f53c2ce4-1021-4a45-92b8-775e8bebad99
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dcdb825073b267c3e3351001ecc7b11c969582e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932044"
---
# <a name="moverecordoptionsenum"></a>MoveRecordOptionsEnum
[Record](../../../ado/reference/ado-api/record-object-ado.md)オブジェクトの[MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md)メソッドの動作を指定します。  
  
|常時|値|[説明]|  
|--------------|-----------|-----------------|  
|**adMoveUnspecified**|-1|既定。 既定の移動操作を実行します。コピー先のファイルまたはディレクトリが既に存在する場合、操作は失敗し、ハイパーテキストリンクが更新されます。|  
|**adMoveOverWrite**|1 で保護されたプロセスとして起動されました|コピー先のファイルまたはディレクトリが既に存在する場合でも、上書きします。|  
|**adMoveDontUpdateLinks**|2|ソース**レコード**のハイパーテキストリンクを更新しないことで、 **MoveRecord**メソッドの既定の動作を変更します。 既定の動作は、プロバイダーの機能によって異なります。 プロバイダーが対応している場合は、移動操作によってリンクが更新されます。 プロバイダーがリンクを修正できない場合、またはこの値が指定されていない場合は、リンクが修正されていなくても移動は成功します。|  
|**adMoveAllowEmulation**|4|プロバイダーが (ダウンロード、アップロード、および削除の各操作を使用して) 移動をシミュレートしようとしていることを要求します。 送信先 URL が別のサーバー上にあるか、ソースとは異なるプロバイダーによってサービスされているために**レコード**を移動しようとして失敗した場合、プロバイダー間でリソースを移動するときに、プロバイダーの機能が異なるため、待機時間が長くなったり、データが失われる可能性があります。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 これらの定数には、対応する ADO/WFC がありません。  
  
## <a name="applies-to"></a>適用対象  
 [MoveRecord メソッド (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
