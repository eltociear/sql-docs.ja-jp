---
title: ビジネス ルール (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], about business rules
- business rules [Master Data Services]
ms.assetid: a9f9e41a-2461-4845-b947-58b3a205543f
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d6ad90fe277e76f98298f4e66fe8c652e64fd38d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65483656"
---
# <a name="business-rules-master-data-services"></a>ビジネス ルール (マスター データ サービス)
  
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]のビジネス ルールは、マスター データの品質と精度を保証するために使用するルールです。 ビジネス ルールを使用して自動的にデータを更新したり、電子メールを送信したり、ビジネス プロセスまたはワークフローを開始したりできます。  
  
## <a name="create-and-publish-business-rules"></a>ビジネス ルールの作成およびパブリッシュ  
 ビジネス ルールは、`If/Then` で作成する [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ステートメントです。 属性値が特定の条件を満たす場合、アクションが実行されます。 実行可能なアクションは、既定値の設定または値の変更です。 これらのアクションを、電子メール通知の送信と組み合わせることができます。  
  
 ビジネス ルールは、特定の属性値に基づいて作成する (たとえば、Color=Blue の場合にアクションを実行する) か、属性値の変更に基づいて作成する (たとえば、Color 属性の値が変更されたときにアクションを実行する) ことができます。 不特定の変更の追跡の詳細については、「[変更の追跡 &#40;マスター データ サービス&#41;](change-tracking-master-data-services.md)」を参照してください。  
  
 ビジネス ルールを使用するには、ルールを作成してパブリッシュし、パブリッシュしたルールをデータに適用する必要があります。 バージョンを検証することによって、バージョンのデータのサブセットまたはすべてのデータにルールを適用できます。 バージョンは、すべての属性がビジネス ルール検証に合格するまでコミットできません。  
  
 ビジネス ルール検証に合格していない属性値を追加しようとした場合でも、値は保存されます。 
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]に表示される検証の問題は、確認して修正できます。  
  
 モデル配置パッケージを作成するときにビジネス ルールを含める場合は、パッケージ内のバージョンからデータを含める必要があります。  
  
 
  **OR** 演算子を使用するビジネス ルールを作成する場合は、個別に評価できる条件ステートメントごとに個別のルールを作成してください。 そうすることによって、必要に応じてルールを除外できるので、柔軟性が向上し、トラブルシューティングも容易になります。  
  
## <a name="how-business-rules-are-applied"></a>ビジネス ルールの適用方法  
 実行されるルールに優先順位を設定できます。 ただし、優先順位が適用される前に、ビジネス ルールはそのルールによって実行されるアクションの種類に基づいて適用されます。 順序は次のとおりです。  
  
1.  **既定値**  
  
2.  **値の変更**  
  
3.  **検証**  
  
4.  **外部アクション**  
  
 これらのグループの中で、アクションが優先順位に基づいて (値が小さいものから順に) 適用されます。 そのため、たとえば別々の 4 つのルールに **既定値** アクションが含まれる場合があります。 最初に実行される **既定値** アクションは、Web UI で指定された優先順位によって決まります。  
  
 ルールの適用については、次の点についても注意してください。  
  
-   ビジネス ルールが除外された場合、または **[アクティブ]** の状態でパブリッシュされていない場合、そのルールは使用可能ですが、ビジネス ルールが適用されるときには対象となりません。  
  
-   ビジネス ルールは、すべてのリーフ メンバーまたはすべての統合メンバーのいずれかの属性値に適用されます。  
  
-   ビジネス ルールは、 **[未処理]** または **[ロック済み]** である、任意のバージョンのモデルに適用できます。  
  
-   ビジネス ルールに適用するときにデータに加えられた変更は、トランザクションとしては記録されません。  
  
-   ビジネス ルールには、 **"がワークフローで始まる"** アクションを複数含めることはできません。  
  
## <a name="system-settings"></a>システム設定  
 
  [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] には、ビジネス ルールに影響する設定が 2 つあります。 これらの設定は、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] で調整するかSystem Settings テーブルで直接調整することができます。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../../2014/master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|新しいビジネス ルールを作成してパブリッシュする。|[ビジネスルール &#40;マスターデータサービスを作成して発行&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)|  
|ビジネス ルールに複数の条件を追加する。|[ビジネスルールに複数の条件を追加する &#40;マスターデータサービス&#41;](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)|  
|属性が値を持つことを必須とするビジネス ルールを作成する。|[属性値を要求する &#40;マスターデータサービス&#41;](../../2014/master-data-services/require-attribute-values-master-data-services.md)|  
|属性値の変更に基づくアクションを行うためのビジネス ルールを作成する。|[属性値の変更に基づいてアクションを開始する &#40;マスターデータサービス&#41;](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
|既存のビジネス ルールの名前を変更する。|[ビジネスルールの名前を変更する &#40;マスターデータサービス&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)|  
|ビジネス ルールが適用されたときに通知を送信するように [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] を構成する。|[通知を送信するようにビジネスルールを構成する &#40;マスターデータサービス&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
|特定のメンバーにビジネス ルールを適用する。|[ビジネスルールに対して特定のメンバーを検証 &#40;マスターデータサービス&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|ビジネス ルールを除外して、使用されないようにする。|[ビジネスルール &#40;マスターデータサービスを除外する&#41;](../../2014/master-data-services/exclude-a-business-rule-master-data-services.md)|  
|既存のビジネス ルールを削除する。|[ビジネスルール &#40;マスターデータサービスの削除&#41;](../../2014/master-data-services/delete-a-business-rule-master-data-services.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [マスター データ サービス概要](master-data-services-overview-mds.md)  
  
-   [バージョン &#40;マスターデータサービス&#41;](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [検証 &#40;マスターデータサービス&#41;](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [Change Tracking &#40;マスターデータサービス&#41;](change-tracking-master-data-services.md)  
  
  
