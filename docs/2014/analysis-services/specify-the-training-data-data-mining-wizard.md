---
title: '[トレーニングデータの指定] (データマイニングウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifytrainingdata.f1
ms.assetid: cb04deeb-0f89-4bba-b3f1-efccada16825
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c3bbeb708cdb0c2882b85d55081446b3dc12b56b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66068065"
---
# <a name="specify-the-training-data-data-mining-wizard"></a>[トレーニング データの指定] (データ マイニング ウィザード)
  
  **[トレーニング データの指定]** ページを使用すると、マイニング構造に含める列を指定できます。 構造に含める列をすべてのモデルで使用するとは限らない場合でも、それらの列を選択できます。 たとえば、マイニング モデルから列にドリルスルーする場合は、それらの列をモデルには含めずに構造に含めることができます。  
  
 構造に含まれる各テーブルには、少なくとも 1 つのキー列が必要です。 キーとして選択する列は、テーブルがケース テーブルか入れ子になったテーブルかによって異なります。 テーブルが入れ子になったテーブルである場合は、通常、キーは予測可能列でもあり、リレーショナル外部キーではありません。 入れ子になったキーについては、「[入れ子になったテーブル &#40;Analysis Services - データ マイニング&#41;](data-mining/nested-tables-analysis-services-data-mining.md)」を参照してください。  
  
> [!NOTE]  
>  マイニング アルゴリズムごとに、異なるキーが使用されます。 各種のキーの詳細については、「[コンテンツの種類 &#40;データ マイニング&#41;](data-mining/content-types-data-mining.md)」を参照してください。  
  
 **詳細については、「** [マイニング構造 &#40;Analysis Services-データマイニング&#41;](data-mining/mining-structures-analysis-services-data-mining.md)」、「[マイニングモデル列](data-mining/mining-model-columns.md)」、「[データマイニングウィザード &#40;Analysis Services データマイニング&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)」、「[リレーショナルマイニング構造を作成する](data-mining/create-a-relational-mining-structure.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **テーブルまたは列**  
 ウィザードの前のページで選択したテーブルおよび列が表示されます。  
  
 **\<チェックボックス>**  
 マイニング構造に含める列を選択します。  
  
 データ ソースに入れ子になったテーブルまたは複数のビューが含まれている場合は、列の一覧を展開して入れ子になったテーブルを表示します。  
  
 **[キー]**  
 データの一意識別子として使用される列を選択します。  
  
 ケース テーブルの場合、通常、キーは一意識別子です。  
  
 入れ子になったテーブルの場合は、 **[キー]** により、関連付けられているケースのコンテキスト内の行の識別子が指定されます。  
  
 **代入**  
 推奨設定の作成時にこの列が使用されます。  
  
> [!NOTE]  
>  この列を使用できるのは、マイニング モデルをマイニング構造と共に作成する場合のみです。  
  
 **[予測可能]**  
 このテーブルまたは列が今後の追加入力に基づいて予測できるようにします。  
  
 入れ子になったテーブルを予測可能として指定すると、入れ子になったテーブル全体が予測可能になります。 入れ子になったテーブル内で入力列または予測可能列として指定されている列がない場合、そのテーブルはマイニング構造に表示されても、モデル内では無視されます。  
  
 **メモ**この列は、マイニングモデルをマイニング構造と共に作成する場合にのみ使用できます。  
  
 **候補**  
 クリックすると、 **[関連列の提示]** ダイアログ ボックスが開きます。ここで、サンプル データに基づいて分析を実行し、選択した **[予測可能]** 列に対してエントロピに基づく最大のリレーションシップを持つ入力列を識別します。 この分析は、OLAP ソースに基づく入れ子になったテーブル列またはマイニング構造にも適用されます。  
  
 **メモ**この列は、マイニングモデルをマイニング構造と共に作成する場合にのみ使用できます。  
  
## <a name="see-also"></a>参照  
 [データマイニングウィザードの F1 ヘルプ &#40;Analysis Services データマイニング&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [データマイニングウィザード &#40;関連する列の提案&#41;](suggest-related-columns-data-mining-wizard.md)   
 [データマイニングウィザード &#40;テーブルの種類の指定&#41;](specify-table-types-data-mining-wizard.md)   
 [列のコンテンツとデータ型 &#40;データマイニングウィザードを指定し&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
