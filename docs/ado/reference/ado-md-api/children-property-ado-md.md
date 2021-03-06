---
title: Children プロパティ (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member::Children
- Children
helpviewer_keywords:
- Children property [ADO MD]
ms.assetid: 61d36468-1ccd-467a-9cb5-17d0bfacc766
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cbec9733044127d23e75364697a41ccd7e8910e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67911520"
---
# <a name="children-property-ado-md"></a>Children プロパティ (ADO MD)
現在の[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)が階層内の親である[メンバー](../../../ado/reference/ado-md-api/members-collection-ado-md.md)コレクションを返します。  
  
## <a name="return-values"></a>戻り値  
 **メンバー**コレクションを返し、読み取り専用です。  
  
## <a name="remarks"></a>解説  
 **Children**プロパティには、現在の**メンバー**が階層構造の親である**Members**コレクションが含まれています。 リーフレベルの**メンバー**オブジェクトには、 **members**コレクションに子メンバーがありません。 このプロパティは、 [Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)オブジェクトに属している**メンバー**オブジェクトでのみサポートされます。 このプロパティが、 [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md)オブジェクトに属する**メンバー**オブジェクトから参照されている場合に、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Member オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [ChildCount プロパティ (ADO MD)](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)
