---
title: リフトチャートを使用した精度のテスト (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 822d414b-4a39-473f-80c3-53476e30655a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 06cefcdac192b715fe843f842088456f769cdd24
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63042667"
---
# <a name="testing-accuracy-with-lift-charts-basic-data-mining-tutorial"></a>リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)
  データマイニングデザイナーの [**マイニング精度チャート**] タブでは、各モデルがどの程度予測されるかを計算し、各モデルの結果を他のモデルの結果と比較して直接比較することができます。 この比較方法を*リフトチャート*と呼びます。 通常、マイニング モデルの予測精度は、リフトまたは分類の精度によって測定します。 このチュートリアルでは、リフト チャートのみを使用します。  
  
 このトピックでは次の作業を行います。  
  
-   [入力データの選択](#BKMK_InputData)  
  
-   [精度チャートのパラメーターの構成](#BKMK_Selecting)  
  
##  <a name="BKMK_InputData"></a>入力データの選択  
 マイニング モデルの精度をテストするには、まず、テストに使用するデータ ソースを選択する必要があります。 テスト データに対するモデルの予測精度をテストし、その後で外部データに対してモデルを使用します。  
  
#### <a name="to-select-the-data-set"></a>データ セットを選択するには  
  
1.  の[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]データマイニングデザイナーの [**マイニング精度チャート**] タブに切り替えて、[**入力の選択**] タブを選択します。  
  
2.  [**精度チャートに使用するデータセットの選択**] グループボックスで、[**マイニング構造のテストケースを使用**する] を選択します。 これは、マイニング構造を作成したときに確保したテスト データです。  
  
     その他のオプションの詳細については、「[精度チャートの種類の選択」および「グラフのオプションの設定](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md)」を参照してください。  
  
##  <a name="BKMK_Selecting"></a>精度チャートのパラメーターの設定  
 精度チャートを作成するには、次の 3 つの事項を定義する必要があります。  
  
-   どのモデルを精度チャートに含めますか。  
  
-   予測可能な、どの属性を測定しますか。 特定のモデルには複数の対象が存在しますが、各グラフで測定できるのは一度に 1 つの結果のみです。  
  
     精度チャートで**予測可能列の名前**として列を使用するに`Predict`は、列の使用法の`Predict Only`種類がまたはである必要があります。 また、対象列のコンテンツの種類は、`Discrete` と `Discretized` のどちらかであることが必要です。 つまり、リフト チャートを使用して、連続する数値の出力に関する精度を測定することはできません。  
  
-   モデルの一般精度、または特定の値を予測する精度 ([自転車購入者] = ' Yes ' など) を測定する必要があります。  
  
#### <a name="to-generate-the-lift-chart"></a>リフト チャートを生成するには  
  
1.  データマイニングデザイナーの [**入力の選択**] タブの [**リフトチャートに表示する予測可能なマイニングモデル列の選択**] で、[**予測列と値の同期**] のチェックボックスをオンにします。  
  
2.  [**予測可能列の名前**] 列で、各モデルに対して [**自転車購入**者] が選択されていることを確認します。  
  
3.  [**表示]** 列で、各モデルを選択します。  
  
     既定では、マイニング構造内のすべてのモデルが選択されます。 モデルを除外することもできますが、このチュートリアルではすべてのモデルを選択したままにしておきます。  
  
4.  [**予測値**] 列で**1**を選択します。 同じ予測可能列を持つモデルのそれぞれに対して、同じ値が自動的に設定されます。  
  
5.  [**リフトチャート**] タブを選択します。  
  
     このタブをクリックすると、予測クエリが実行されてテスト データに関する予測結果が取得され、結果は既知の値と比較されます。 結果がグラフとして表示されます。  
  
     [**予測値**] オプションを使用して特定のターゲットの結果を指定した場合、リフトチャートはランダムな推測の結果と理想的なモデルの結果をプロットします。  
  
    -   ランダム推定の線では、何もデータを使用せずに予測を行う場合に、モデルがどれほどの精度であるかが示されます。つまり、2 つの結果のいずれかを予測する場合は、50 対 50 の分割が行われます。 リフト チャートを使用すると、ランダム推定と比較してモデルがどれほど改善された予測を行うかが視覚的に表現されます。  
  
    -   理想的なモデルの線は、精度の上限を表します。 これは、モデルが常にできるだけ高い精度で予測を行う場合に達成できる、実現可能な最大の成果を示しています。  
  
     作成したマイニング モデルは通常、これら 2 つの極値の間に位置します。 ランダムな推測による改善は、*リフト*と見なされます。  
  
6.  凡例を使用して、理想モデルとランダム推測モデルを表す色付きの線を配置します。  
  
     この`TM_Decision_Tree`モデルでは、クラスタリングモデルと Naive Bayes モデルの両方を実行することで、最大のリフトが得られることがわかります。  
  
 このレッスンで作成したものと似たリフトチャートの詳細については、「[リフトチャート &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)」を参照してください。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [フィルター選択されたモデルのテスト &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [リフトチャート &#40;Analysis Services-データマイニング&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)   
 [[リフトチャート] タブ &#40;マイニング精度チャートビュー&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)  
  
  
