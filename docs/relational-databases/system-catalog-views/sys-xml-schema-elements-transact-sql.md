---
title: xml_schema_elements (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_elements
- sys.xml_schema_elements_TSQL
- xml_schema_elements
- xml_schema_elements_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_elements catalog view
ms.assetid: 190ed0cd-0c5e-4607-9db4-9e77cacf17d7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d43f30f15502a41882190dcdd19984d9ec042d4a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037393"
---
# <a name="sysxml_schema_elements-transact-sql"></a>sys.xml_schema_elements (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **E**の**symbol_space**型である XML スキーマコンポーネントごとに1行の値を返します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**\<継承された列>**|**--**|[Xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md)から列を継承します。|  
|**is_default_fixed**|**bit**|1 = 既定値は固定値です。 この値を XML インスタンスでオーバーライドすることはできません。<br /><br /> 0 = 既定値は、要素の固定値ではありません。 (既定値)。|  
|**is_abstract**|**bit**|1 = 要素は abstract であり、インスタンス ドキュメント内では使用できません。 要素の代替グループのメンバーは、インスタンス ドキュメント内に表示される必要があります。<br /><br /> 0 = 要素は abstract ではありません。 (既定値)。|  
|**is_nillable**|**bit**|1 = 要素は nillable です。<br /><br /> 0 = 要素は nillable ではありません  (既定値)。|  
|**must_be_qualified**|**bit**|1 = 要素は、明示的に名前空間を修飾する必要があります。<br /><br /> 0 = 要素には暗黙的に名前空間の修飾名が追加されます  (既定値)。|  
|**is_extension_blocked**|**bit**|1 = 拡張型のインスタンスへの置換はブロックされます。<br /><br /> 0 = 拡張型による置換は許可されます。 (既定値)。|  
|**is_restriction_blocked**|**bit**|1 = 制限型のインスタンスへの置換はブロックされます。<br /><br /> 0 = 制限型による置換は許可されます。 (既定値)。|  
|**is_substitution_blocked**|**bit**|1 = 代替グループのインスタンスは使用できません。<br /><br /> 0 = 代替グループによる置換は許可されています。 (既定値)。|  
|**is_final_extension**|**bit**|1 = 拡張型のインスタンスへの置換は許可されません。<br /><br /> 0 = 拡張型のインスタンスへの置換は許可されます  (既定値)。|  
|**is_final_restriction**|**bit**|1 = 制限型のインスタンスへの置換は許可されていません。<br /><br /> 0 = 制限型のインスタンスでの置換は許可されます。 (既定値)。|  
|**default_value**|**nvarchar (4000)**|要素の既定値。 既定値が指定されていない場合は NULL です。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Xml スキーマ &#40;XML 型システム&#41; カタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
