---
title: バージョンにフラグを割り当てる
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], assigning flags
- versions [Master Data Services], assigning flags
ms.assetid: 6629ec7e-32e7-4a1e-8b31-eb43c5923766
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4e8f69d473ff15be3105c8dcef5f51edf30f4302
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729783"
---
# <a name="assign-a-flag-to-a-version-master-data-services"></a>バージョンにフラグを割り当てる (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、バージョンにフラグを割り当てて、ユーザーまたはサブスクライブ システムが使用する必要があるバージョンを示します。  
  
> [!NOTE]  
>  バージョン フラグは一度に 1 つのバージョンにしか割り当てることができません。 別のバージョンに既に割り当てられているフラグを割り当てた場合、フラグは、選択したバージョンに移動します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [**バージョン管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
-   割り当てるバージョン フラグを作成している必要があります。 詳細については、「 [バージョン フラグを作成する (マスター データ サービス)](../master-data-services/create-a-version-flag-master-data-services.md)」を参照してください。  
  
-   [バージョン管理] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
### <a name="to-assign-a-flag-to-a-version"></a>フラグをバージョンに割り当てるには  
  
1.  
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。  
  
2.  
  **[バージョンの管理]** ページで、フラグを割り当てるバージョンの行の **[フラグ]** 列のセルをダブルクリックします。  
  
3.  一覧から、割り当てるフラグを選択します。  
  
    > [!NOTE]  
    >  フラグが使用できない場合、そのフラグは **[コミット済み]** のバージョンのみで使用できる可能性があります。 これを確認するには、 **[バージョン フラグの管理]** ページに移動し **[コミット済みのバージョンのみ]** フィールドでそのフラグを確認します。  
  
4.  Enter キーを押して変更を保存します。  
  
## <a name="see-also"></a>参照  
 [バージョンフラグ &#40;マスターデータサービスを作成し&#41;](../master-data-services/create-a-version-flag-master-data-services.md)   
 [バージョン &#40;マスターデータサービス&#41;](../master-data-services/versions-master-data-services.md)  
  
  
