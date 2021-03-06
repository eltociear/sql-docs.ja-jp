---
title: Excel で分析 (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2f17b4df-eea2-48c7-a1f2-a3fb7748c15f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f8090c75108f7a384019030082699917fca915b6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66067686"
---
# <a name="analyze-in-excel-ssas-tabular"></a>Excel で分析 (SSAS テーブル)
  
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の "Excel で分析" 機能を使用すると、テーブル モデルの作成者は、開発時にモデル プロジェクトを迅速に分析できます。 "Excel で分析" 機能によって Microsoft Excel が開き、モデル ワークスペース データベースへのデータ ソース接続が作成され、自動的にピボットテーブルがワークシートに追加されます。 ワークスペース データベース オブジェクト (テーブル、列、およびメジャー) は、ピボットテーブルのフィールドの一覧にフィールドとして含まれます。 これによりオブジェクトとデータは、有効なユーザーまたはロールおよびパースペクティブのコンテキスト内で表示できるようになります。  
  
 このトピックは、既に Microsoft Excel、ピボットテーブル、およびピボットグラフの使用に慣れているユーザーを対象としています。 Excel の使用方法の詳細については、Excel のヘルプを参照してください。  
  
 このトピックのセクション:  
  
-   [効果](#bkmk_benefits)  
  
-   [Related Tasks](#bkmk_rt)  
  
##  <a name="bkmk_benefits"></a>効果  
 "Excel で分析" 機能によって、モデルの作成者は Microsoft Excel という一般的なデータ分析アプリケーションを使用して、モデル プロジェクトの有効性をテストできます。 "Excel で分析" 機能を使用するには、Microsoft Office 2003 以降が [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]と同じコンピューターにインストールされている必要があります。  
  
> [!NOTE]  
>  Office が [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]と同じコンピューターにインストールされていない場合は、別のコンピューターの Excel を使用して、データ ソースとしてワークスペース データベースに接続できます。 これにより、ピボットテーブルをワークシートに手動で追加することができます。  
  
 "Excel で分析" 機能によって、Excel が開き、新しい Excel ブック (.xls) が作成されます。 ブックからモデル ワークスペース データベースへのデータ接続が作成されます。 空のピボットテーブルがワークシートに追加され、モデル オブジェクト メタデータがピボットテーブルのフィールドの一覧に入力されます。 これで、表示可能なデータとスライサーをピボットテーブルに追加できます。  
  
 "Excel で分析" 機能を使用する際に、既定では、現在ログオンしているユーザー アカウントが有効なユーザーになります。 このアカウントは通常、モデル オブジェクトまたはデータに対する表示制限のない管理者です。 ただし、別の有効なユーザー名またはロールを指定することもできます。 これにより、特定のユーザーまたはロールのコンテキスト内で Excel のモデル プロジェクトを参照できます。 有効なユーザーの指定には、次のオプションが含まれています。  
  
 **現在の Windows ユーザー**  
 現在ログオンしているユーザー アカウントを使用します。  
  
 **その他の Windows ユーザー**  
 現在ログオンしているユーザーではなく、指定した Windows ユーザー名を使用します。 別の Windows ユーザーを使用する場合、パスワードは必要ありません。 有効なユーザー名のコンテキスト内で Excel を使用して、オブジェクトおよびデータを表示することのみが可能になります。 Excel でモデル オブジェクトまたはデータに変更を行うことはできません。  
  
 **果たす**  
 ロールは、オブジェクト メタデータおよびデータに対するユーザーの権限の定義に使用されます。 ロールは通常、特定の Windows ユーザーまたは Windows ユーザー グループに対して定義されます。 一部の適切なロールには、DAX 式で定義した追加の行レベル フィルターを含めることができます。 "Excel で分析" 機能を使用する際には、必要に応じて使用するロールを選択することもできます。 オブジェクト メタデータおよびデータの表示は、ロールに対して定義された権限とフィルターによって制限されます。 詳細については、「[ロールの作成および管理 (SSAS テーブル)](roles-ssas-tabular.md)」を参照してください。  
  
 有効なユーザーまたはロールに加え、パースペクティブを指定することもできます。 モデル作成者はパースペクティブを使用して、ビジネス シナリオに基づいてモデル オブジェクトとデータの表示を定義できます。 既定では、パースペクティブは使用されません。 "Excel で分析" 機能でパースペクティブを使用するには、あらかじめ [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で [パースペクティブ] ダイアログ ボックスを使用して、パースペクティブを定義しておく必要があります。 パースペクティブが指定されている場合、ピボットテーブルのフィールドの一覧には、パースペクティブで選択されたオブジェクトのみが表示されます。 詳細については、「 [SSAS テーブル&#41;&#40;パースペクティブの作成と管理](perspectives-ssas-tabular.md)」を参照してください。  
  
##  <a name="bkmk_rt"></a> 関連タスク  
  
|**トピック**|**説明**|  
|---------------|---------------------|  
|[Excel でのテーブルモデルの分析 &#40;SSAS 表形式&#41;](analyze-a-tabular-model-in-excel-ssas-tabular.md)|このトピックでは、モデル デザイナーで "Excel で分析" 機能を使用する方法、モデル ワークスペース データベースへのデータ ソース接続を作成する方法、およびワークシートにピボットテーブルを追加する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [Excel でのテーブルモデルの分析 &#40;SSAS 表形式&#41;](analyze-a-tabular-model-in-excel-ssas-tabular.md)   
 [SSAS 表形式のロール &#40;&#41;](roles-ssas-tabular.md)   
 [SSAS テーブル&#41;&#40;パースペクティブ](perspectives-ssas-tabular.md)  
  
  
