---
title: StreamReadEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamReadEnum
helpviewer_keywords:
- StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7700fc1ddc3cc619db224ac46006370898af1d62
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928664"
---
# <a name="streamreadenum"></a>StreamReadEnum
ストリーム全体または次の行を[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトから読み取るかどうかを指定します。  
  
|常時|値|[説明]|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|既定。 ストリームから、現在の位置から[EOS](../../../ado/reference/ado-api/eos-property.md)マーカーまでのすべてのバイトを読み取ります。 これは、バイナリストリームを持つ唯一の有効な**Streamreadenum**値です ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adtypebinary**です)。|  
|**adReadLine**|-2|( [Lineseparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)プロパティによって指定された) ストリームから次の行を読み取ります。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 これらの定数には、対応する ADO/WFC がありません。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Read メソッド](../../../ado/reference/ado-api/read-method.md)|[ReadText メソッド](../../../ado/reference/ado-api/readtext-method.md)|
