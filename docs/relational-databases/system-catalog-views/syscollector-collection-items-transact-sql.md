---
title: syscollector_collection_items (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_collection_items_TSQL
- syscollector_collection_items
dev_langs:
- TSQL
helpviewer_keywords:
- syscollector_collection_items view
- add data collector view
ms.assetid: a279ecd1-a59c-4315-9f08-bf221f00a465
author: stevestein
ms.author: sstein
ms.openlocfilehash: 78e8211c10d019c3b2a8c2435c5ddde8f8182a14
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68060412"
---
# <a name="syscollector_collection_items-transact-sql"></a>syscollector_collection_items (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コレクション セット内のアイテムに関する情報を返します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**collection_set_id**|**int**|コレクションセットを識別します。 NULL 値は許可されません。|  
|**collection_item_id**|**int**|コレクションセット内の項目を識別します。 NULL 値は許可されません。|  
|**collector_type_uid**|**UNIQUEIDENTIFIER**|コレクター型の識別に使用する GUID です。 NULL 値は許可されません。|  
|**name**|**nvarchar(4000)**|コレクションセットの名前。 NULL 値が許可されます。|  
|**頻度**|**int**|コレクション アイテムでデータを収集する頻度です。 NULL 値は許可されません。|  
|**パラメータ**|**xml**|コレクションアイテムに関連付けられているコレクター型のパラメーター化について説明します。 このコレクション項目の XML スキーマは、特定のコレクター型の**parameter_schema**に格納されている xml スキーマ (XSD) を使用して検証されます。 NULL 値が許可されます。 詳細については、「 [syscollector_collector_types &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md)」を参照してください。|  
  
## <a name="permissions"></a>アクセス許可  
 **Dc_operator**、 **dc_proxy**を選択する必要があります。  
  
## <a name="see-also"></a>参照  
 [データコレクターストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [データコレクタービュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [データコレクション](../../relational-databases/data-collection/data-collection.md)  
  
  
