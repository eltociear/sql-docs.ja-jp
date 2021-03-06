---
title: ビジネス ルールに対してバージョンを検証する
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- validating versions [Master Data Services]
- validating versions [Master Data Services], about validating versions
- versions [Master Data Services], validating
- business rules [Master Data Services], applying to all members
ms.assetid: 5aee7901-6d05-41d4-8bbb-c6f26791d1df
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2995a02e738b2c185edff26ee0d6a395df14f59f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73727828"
---
# <a name="validate-a-version-against-business-rules-master-data-services"></a>ビジネス ルールに対してバージョンを検証する (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、ビジネス ルールをモデル バージョンのすべてのメンバーに適用するためにバージョンが検証されます。  
  
 この手順では、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションを使用してデータを検証する方法について説明します。 MDS データベースの権限がある場合は、代わりにストアド プロシージャを使用することができます。 詳細については、「 [検証ストアド プロシージャ (マスター データ サービス)](../master-data-services/validation-stored-procedure-master-data-services.md)」を参照してください。  
  
> [!NOTE]  
>  バージョンをコミットするには、すべてのメンバーが検証に合格する必要があります。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   [**バージョン管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
-   バージョンの状態は、 **[未処理]** または **[ロック済み]** である必要があります。  
  
-   
  **[バージョンの検証]** ページに **[検証成功]** 以外の状態のメンバーが存在する必要があります。  
  
### <a name="to-validate-a-version"></a>バージョンを検証するには  
  
1.  
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。  
  
2.  
  **[バージョンの管理]** ページのメニュー バーから **[バージョンの検証]** をクリックします。  
  
3.  
  **[バージョンの検証]** ページで、検証するモデルおよびバージョンを選択します。  
  
4.  
  **[検証]** をクリックします。  
  
5.  確認のダイアログ ボックスで **[OK]** をクリックします。  
  
    > [!NOTE]  
    >  バージョンの検証が完了すると、進行状況インジケーターが表示されなくなります。  
  
## <a name="next-steps"></a>次の手順  
  
-   [マスターデータサービス &#40;のバージョンをロックする&#41;](../master-data-services/lock-a-version-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [検証の状態 &#40;マスターデータサービス&#41;](../master-data-services/validation-statuses-master-data-services.md)   
 [検証ストアドプロシージャ &#40;マスターデータサービス&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)   
 [バージョン &#40;マスターデータサービス&#41;](../master-data-services/versions-master-data-services.md)   
 [ビジネスルール &#40;マスターデータサービス&#41;](../master-data-services/business-rules-master-data-services.md)   
 [ビジネスルールに対して特定のメンバーを検証 &#40;マスターデータサービス&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
  
