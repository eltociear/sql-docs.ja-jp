---
title: crypt_properties (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- crypt_properties
- crypt_properties_TSQL
- sys.crypt_properties_TSQL
- sys.crypt_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.crypt_properties catalog view
ms.assetid: d5684f5a-30b1-418e-ae4d-ab040db9257e
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9655866d4fd2d6f98b38532f77f94bc12f16f9b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68109482"
---
# <a name="syscrypt_properties-transact-sql"></a>sys.crypt_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  セキュリティ保護可能なリソースに関連付けられている暗号化プロパティごとに1行の値を返します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**講義**|**tinyint**|プロパティが存在するリソースのクラスの識別子。<br /><br /> 1 = オブジェクトまたは列<br /> 5 = アセンブリ|  
|**class_desc**|**nvarchar (60)**|プロパティが存在するクラスの説明。<br /><br /> OBJECT_OR_COLUMN<br /> ASSEMBLY|  
|**major_id**|**int**|クラスに従って解釈される、プロパティが存在する対象の ID|  
|**thumbprint**|**varbinary (32)**|使用する証明書または非対称キーの SHA-1 ハッシュ。|  
|**crypt_type**|**char (4)**|暗号化の種類。<br /><br /> SPVC = 証明書の秘密キーで署名済み<br /><br /> SPVA = 非対称秘密キーによる署名<br /><br /> CPVC = 証明書の秘密キーによって副署されます。<br /><br /> CPVA = 非対称キーによって副署されます。|  
|**crypt_type_desc**|**nvarchar (60)**|暗号化の種類の説明。<br /><br /> SIGNATURE BY CERTIFICATE<br /><br /> SIGNATURE BY ASYMMETRIC KEY<br /><br /> 証明書によるカウンターの署名<br /><br /> 非対称キーによるカウンターの署名|  
|**crypt_property**|**varbinary(max)**|署名された、または暗号化されたビット。 署名付きモジュールの場合は、モジュールの署名ビットです。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [セキュリティカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [Transact-sql&#41;&#40;証明書の作成](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
