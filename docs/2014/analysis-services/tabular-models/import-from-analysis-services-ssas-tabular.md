---
title: Analysis Services からのインポート (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b9a21b23-3a06-4ef8-bc06-9c79cdc54870
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9d864b2f8256bdd33cd2f595274a7894b4ea5e89
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66067044"
---
# <a name="import-from-analysis-services-ssas-tabular"></a>Analysis Services からのインポート (SSAS テーブル)
  このトピックでは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のサーバーからインポート プロジェクト テンプレートを使用して既存の表形式モデルからメタデータをインポートし、新しい表形式モデル プロジェクトを作成する方法を説明します。  
  
## <a name="create-a-new-model-by-importing-metadata-from-an-existing-model-in-analysis-services"></a>Analysis Services の既存のモデルからのメタデータのインポートによる新しいモデルの作成  
 Analysis Services サーバーの既存のテーブル モデルからメタデータをコピーして、新しいテーブル モデル プロジェクトを作成するには、サーバーからインポート プロジェクト テンプレートを使用します。 新しいプロジェクトは、インポート元のモデルと同じデータ ソース接続、テーブル、リレーションシップ、メジャー、KPI、ロール、階層、パースペクティブ、およびパーティションを使用して作成されます。 ただし、データは既存のモデルから新しいモデル ワークスペースにコピーされません。 インポート プロセスが完了し、新しいモデル プロジェクトが作成された後、[すべて処理] を実行し、データ ソースから新しいモデル プロジェクト ワークスペース データベースにデータを読み込む必要があります。  
  
#### <a name="to-create-a-new-model-by-importing-metadata-from-an-existing-model"></a>既存のモデルからのメタデータのインポートによって、新しいモデルを作成するには  
  
1.  
  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[ファイル]** メニューの **[新規作成]** をクリックし、 **[プロジェクト]** をクリックします。  
  
2.  
  **[新しいプロジェクト]** ダイアログ ボックスの **[インストールされているテンプレート]** で **[ビジネス インテリジェンス]** をクリックし、 **[サーバーからインポート]** をクリックします。  
  
3.  [**名前**] にプロジェクトの名前を入力し、場所とソリューション名を指定して、[ **OK**] をクリックします。  
  
4.  
  **[Analysis Services からのインポート]** ダイアログ ボックスの **[サーバー名]** で、インポートするモデル メタデータを含む Analysis Services サーバーの名前を指定します。  
  
5.  
  **[データベース名]** で、インポートするモデル メタデータを含むテーブル モデル データベースを選択し、 **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SSAS 表形式&#41;のプロジェクトプロパティ &#40;](properties-ssas-tabular.md)  
  
  
