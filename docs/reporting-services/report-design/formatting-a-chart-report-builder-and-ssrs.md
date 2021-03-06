---
title: グラフの書式設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
f1_keywords:
- "10214"
- sql13.rtp.rptdesigner.charttitleproperties.shadow.f1
- sql13.rtp.rptdesigner.serieslabelproperties.font.f1
- "10149"
- sql13.rtp.rptdesigner.legendproperties.fill.f1
- sql13.rtp.rptdesigner.seriesproperties.shadow.f1
- "10255"
- sql13.rtp.rptdesigner.seriesproperties.fill.f1
- "10154"
- "10170"
- "10173"
- "10169"
- "10158"
- sql13.rtp.rptdesigner.minorgridlineproperties.gridlineoptions.f1
- sql13.rtp.rptdesigner.calculatedseriesproperties.borders.f1
- "10246"
- sql13.rtp.rptdesigner.serieslabelproperties.fill.f1
- "10150"
- sql13.rtp.rptdesigner.majorgridlineproperties.gridlineoptions.f1
- "10159"
- sql13.rtp.rptdesigner.chartproperties.fill.f1
- "10160"
- "10182"
- "10163"
- sql13.rtp.rptdesigner.charttitleproperties.fill.f1
- "10164"
- "10253"
- "10216"
- "10171"
- "10257"
- sql13.rtp.rptdesigner.chartareaproperties.shadow.f1
- sql13.rtp.rptdesigner.chartareaproperties.fill.f1
- sql13.rtp.rptdesigner.calculatedseriesproperties.fill.f1
- sql13.rtp.rptdesigner.charttitleproperties.font.f1
- sql13.rtp.rptdesigner.seriesproperties.markers.f1
- sql13.rtp.rptdesigner.calculatedseriesproperties.shadow.f1
- sql13.rtp.rptdesigner.charttitleproperties.borders.f1
- sql13.rtp.rptdesigner.chartareaproperties.border.f1
- sql13.rtp.rptdesigner.chartproperties.border.f1
- "10247"
ms.assetid: d3984300-c766-42f8-b7c4-863123d67c99
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bdbaff988ae0b433e12e3f65b64899b0c3e0b02a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "65575964"
---
# <a name="formatting-a-chart-report-builder-and-ssrs"></a>グラフの書式設定 (レポート ビルダーおよび SSRS)
  グラフのデータを定義し、そのデータが希望どおりに表示されるようになったら、書式を追加して、全体的な外観を改善したり主要なデータ ポイントを強調したりすることができます。 最も一般的な書式設定オプションは、グラフ要素を右クリックして表示されるショートカット メニューを使用すると表示できるプロパティ ダイアログ ボックスから変更できます。 各グラフ要素には、独自のダイアログ ボックスがあります。 グラフ要素の詳細については、「 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)」を参照してください。  
  
 グラフに関連するプロパティはすべてプロパティ ペインにありますが、これらのプロパティの多くはダイアログ ボックスから設定することもできます。 系列の書式を設定する場合は、カスタム属性を使用して系列固有のプロパティを指定できます。カスタム属性は、プロパティ ペイン内にある、プロパティの **[CustomAttributes]** カテゴリのみで操作できます。  
  
 使用する手順の数を最小限に抑えてグラフの書式を効率的に設定するには、罫線のスタイル、パレット、および描画スタイルを既定値から変更します。 この 3 つの機能は、グラフの外観に最も大きな変化をもたらします。 描画スタイルを適用できるのは、円グラフ、ドーナツ グラフ、横棒グラフ、および縦棒グラフだけです。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a>このセクションの内容  
 [グラフの系列の色の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)  
 パレットを使用して色を定義する方法、独自の色パレットを定義する方法、および式に基づいて色を定義する方法について説明します。  
  
 [グラフの軸ラベルの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)  
 グリッド線、目盛り、およびタイトルを表示する方法と、軸スケール上の数値と日付の書式を設定する方法について説明します。  
  
 [グラフの凡例の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)  
 グラフの凡例内のアイテムの順序変更と書式設定を実行する方法について説明します。  
  
 [グラフでのデータ ポイントの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
 グラフ上のすべての系列に対するデータ ポイント ラベルの配置とデータ ポイント マーカーの書式設定を実行する方法について説明します。  
  
 [グラフに対する 3D、傾斜、およびその他の効果 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/chart-effects-3d-bevel-and-other-report-builder.md)  
 グラフに適用できるさまざまな 3D 効果について説明します。  
  
 [グラフへの枠線の追加 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)  
 グラフに枠線を追加する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [グラフへの枠線の追加 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/add-a-border-frame-to-a-chart-report-builder-and-ssrs.md)   
 [パレットを使用したグラフの色の定義 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)   
 [グラフへの傾斜、エンボス、およびテクスチャのスタイルの追加 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/chart-effects-add-bevel-emboss-or-texture-report-builder.md)  
  
  
