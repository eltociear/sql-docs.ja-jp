---
title: Count プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Collection::Count
helpviewer_keywords:
- Count property [ADO]
ms.assetid: da9ccd1f-d402-41a2-940c-45556fc5340d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 292a4a8c26b3b10aa47fcbe7046a5897f601ed9f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919353"
---
# <a name="count-property-ado"></a>Count プロパティ (ADO)
コレクション内のオブジェクトの数を示します。  
  
## <a name="return-value"></a>戻り値  
 **Long 型**の値を返します。  
  
## <a name="remarks"></a>解説  
 **Count**プロパティを使用して、特定のコレクションに含まれるオブジェクトの数を確認します。  
  
 コレクションのメンバーの番号はゼロで始まるので、常にゼロのメンバーで始まり、 **Count**プロパティの値から1を引いた値で終わる必要があります。 Microsoft Visual Basic を使用していて、 **Count**プロパティを確認せずにコレクションのメンバーをループする場合は、for each を使用します。 **次**のコマンド。  
  
 **Count**プロパティが0の場合、コレクションにはオブジェクトが存在しません。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Axes コレクション (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs コレクション (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Dimensions コレクション (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Errors コレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)|[Fields コレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Groups コレクション (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Hierarchies コレクション (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Indexes コレクション (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Keys コレクション (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Levels コレクション (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Members コレクション (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Positions コレクション (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Procedures コレクション (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)|[Tables コレクション (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|[Users コレクション (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Views コレクション (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>参照  
 [Count プロパティの例 (VB)](../../../ado/reference/ado-api/count-property-example-vb.md)   
 [Count プロパティの例 (VC + +)](../../../ado/reference/ado-api/count-property-example-vc.md)   
 [Refresh メソッド (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)
