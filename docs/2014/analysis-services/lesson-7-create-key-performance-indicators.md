---
title: 'レッスン 8: 主要業績評価指標を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a6c8ac2b-64ba-456f-b418-7bf0afe145d1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1d9d3145583670fb849321bac5b57928caacfbc2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078372"
---
# <a name="lesson-8-create-key-performance-indicators"></a>レッスン 8: 主要業績評価指標の作成
  このレッスンでは、主要業績評価指標 (KPI) を作成します。 KPI は､業績面からある値 (*Base* メジャーで定義) と *Target* 値(メジャーまたは絶対値で定義) との比較評価に使用されます｡ レポート用のクライアント アプリケーションでは､KPI はビジネスのプロが事業の成功の摘要を理解したり､傾向を把握したりする容易で迅速な手段になります｡ 詳細については、[「KPI (SSAS テーブル)」](tabular-models/kpis-ssas-tabular.md) を参照してください。  
  
 このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン [「レッスン 7: メジャーの作成」](lesson-6-create-measures.md)を完了している必要があります。  
  
## <a name="create-key-performance-indicators"></a>主要業績評価指標を作成する  
  
#### <a name="to-create-an-internet-current-quarter-sales-performance-kpi"></a>Internet Current Quarter Sales Performance KPI を作成するには  
  
1.  モデル デザイナーで、**[Internet Sales]** テーブル (タブ) をクリックします。  
  
2.  メジャー グリッドで空のセルをクリックします｡  
  
3.  テーブルの上の数式バーに次の式を入力します｡  
  
     `Internet Current Quarter Sales Performance :=IFERROR([Internet Current Quarter Sales]/[Internet Previous Quarter Sales Proportion to QTD],BLANK())`  
  
     数式の入力が終了したら、Enter キーを押します。  
  
     このメジャーは､KPI の Base メジャーの働きをします｡  
  
4.  メジャー グリッドで、 **Internet Current Quarter Sales Performance** メジャーを右クリックし、[ **KPI の作成**] をクリックします。  
  
     [ **主要業績評価指標** ] ダイアログ ボックスが開きます。  
  
5.  [ **主要業績評価指標** ] ダイアログ ボックスの [ **ターゲット値の定義**] で、[ **絶対値** ] オプションを選択します。  
  
6.  [**絶対値**] フィールドに「」 `1.1`と入力し、enter キーを押します。  
  
7.  [**状態のしきい値の定義**] で、左 (下) の`1`スライダーフィールドに「」と入力し、右 (高) `1.07`のスライダーフィールドに「」と入力します。  
  
8.  
  **[Select Icon Style]** で､アイコン タイプとして菱形 (赤)､三角形 (黄色)､円 (緑) を選択します｡  
  
    > [!TIP]  
    >  使用可能なアイコン スタイルの下には [ **説明** ] という展開可能フィールドがあります。 各種の KPI 要素に対する説明を入力することで、それらをクライアント アプリケーションで識別しやすくすることができます。  
  
9. 
  **[OK]** をクリックして KPI を終了します。  
  
     メジャー グリッドで、 **Internet Current Quarter Sales Performance** メジャーの横にアイコンが表示されます。 このアイコンは､そのメジャーが KPI の Base 値の働きをしていることを示します｡  
  
#### <a name="to-create-an-internet-current-quarter-margin-performance-kpi"></a>Internet Current Quarter Margin Performance KPI を作成するには  
  
1.  
  **Internet Sales** テーブルのメジャー グリッドで、空のセルをクリックします。  
  
2.  テーブルの上の数式バーに次の式を入力します｡  
  
     `Internet Current Quarter Margin Performance :=IF([Internet Previous Quarter Margin Proportion to QTD]<>0,([Internet Current Quarter Margin]-[Internet Previous Quarter Margin Proportion to QTD])/[Internet Previous Quarter Margin Proportion to QTD],BLANK())`  
  
     数式の入力が終了したら、Enter キーを押します。  
  
3.  メジャー グリッドで、 **Internet Current Quarter Margin Performance** メジャーを右クリックし、[ **KPI の作成**] をクリックします。  
  
4.  [ **主要業績評価指標** ] ダイアログ ボックスの [ **ターゲット値の定義**] で、[ **絶対値** ] オプションを選択します。  
  
5.  [**絶対値**] フィールドに「」 `1.25`と入力します。  
  
6.  [ **ステータスのしきい値の定義**] で、左 (下) のスライダー フィールドをスライドして「 **0.8**」と表示させ、右 (上) のスライダー フィールドをスライドして「 **1.03**」と表示させます。  
  
7.  
  **[Select Icon Style]** で､アイコン タイプとして菱形 (赤)､三角形 (黄色)､円 (緑) を選択し､**[OK]** をクリックします｡  
  
## <a name="next-step"></a>次のステップ  
 このチュートリアルを続行するには、次のレッスン [「レッスン 9: パースペクティブの作成」](lesson-8-create-perspectives.md)に進んでください。  
  
  
