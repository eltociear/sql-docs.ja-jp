---
title: その他の注釈 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fff698fc4eb92dd1bade50274a289f861e07ede0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013610"
---
# <a name="other-annotations-sqlxml-40"></a>その他の注釈 (SQLXML 4.0)
  前のトピックで説明した注釈に加えて、XML 一括読み込みでは、その他の注釈が次のように解釈されます。  
  
 `sql:id-prefix`  
 スキーマで XML データのプレフィックスを指定した場合、XML 一括読み込みでは Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] へのデータの送信前にプレフィックスが削除されます。  
  
 `sql:use-cdata`  
 XML 一括読み込みでは、CDATA セクションに格納されているテキストが読み取られ、それが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に送信されます。  
  
 `sql:url-encode`  
 XML 一括読み込みでは、この注釈はサポートされません。 たとえば、XML データ入力に URL を指定することはできません。また、XML 一括読み込みで、指定した場所からデータを読み込んでデータベースに格納することはできません。  
  
 `sql:is-mapping-schema`  
 XML 一括読み込みではこの注釈はサポートされず、`sql:id` もサポートされません。  
  
> [!NOTE]  
>  XML 一括読み込みでは、インライン マッピング スキーマはサポートされません。  
  
 `sql:key-fields`  
 XML 一括読み込みでは、この注釈は常に無視されます。  
  
## <a name="see-also"></a>参照  
 [SQLXML 4.0 &#40;の注釈の解釈&#41;](annotation-interpretation-sqlxml-4-0.md)  
  
  
