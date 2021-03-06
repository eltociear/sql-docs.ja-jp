---
title: コレクション権限
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], permissions
- permissions [Master Data Services], collections
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b55d028e90869f6b21d51348b97411fb6c965eb9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729641"
---
# <a name="collection-permissions-master-data-services"></a>コレクション権限 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  コレクション権限は、エンティティのすべてのコレクションに適用されます。 特定のコレクションに権限を与えることはできません。つまり、権限はすべてのコレクションに適用されます。  
  
> [!NOTE]  
>  これらの権限は、ユーザー インターフェイスの **[エクスプローラー]** 機能領域にのみ適用されます。  
  
|権限|[説明]|  
|----------------|-----------------|  
|**Read**|ユーザーがコレクションのメンバーとメンバーの属性を読み取ることができます。|  
|**生成**|ユーザーがコレクションのメンバーを作成して属性値を割り当てることができます。|  
|**Update**|ユーザーがコレクションのメンバー、属性、リレーションシップを更新できます。|  
|**デリート**|ユーザーがコレクションのメンバーを削除できます。|  
|**Deny**|コレクション メンバーに対するアクセスをすべて拒否します。|  
  
 読み取り、作成、更新、削除の各権限は組み合わせることができます。 作成、更新、削除が割り当てられると、読み取り権限が自動的に割り当てられます。  
  
## <a name="see-also"></a>参照  
 [モデルオブジェクト権限の割り当て &#40;マスターデータサービス&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [コレクション &#40;マスターデータサービス&#41;](../master-data-services/collections-master-data-services.md)   
 [モデルオブジェクト権限 &#40;マスターデータサービス&#41;](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
