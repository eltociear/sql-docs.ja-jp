---
title: 計算されるメンバーフォームエディター (キューブデザイナーの [計算] タブ) (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationexpression.calculatedmember.f1
ms.assetid: f7719b9e-b1e6-4792-90a6-30d9d8eb1196
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 432300f54a7678970f394b27712bcb28ba8a7e7d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66088371"
---
# <a name="calculated-member-form-editor-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a>計算されるメンバー フォーム エディター (キューブ デザイナーの [計算] タブ) (Analysis Services - 多次元データ)
  キューブ デザイナーの **[計算]** タブの **計算されるメンバー フォーム エディター** ペインを使用すると、計算されるメンバーを作成したり変更したりできます。  
  
 **メモ**このペインはフォームビューでのみ表示されます。  
  
## <a name="options"></a>オプション  
 **名前**  
 計算されるメンバーの名前を入力します。  
  
 **[親のプロパティ]**  
 展開して、 **[親階層]**、 **[親メンバー]**、および **[変更]** の各オプションを表示します。  
  
 **親階層**  
 計算されるメンバーを含めるために選択したキューブ内でディメンションと階層を選択します。 [メジャー] を選択して、計算されるメジャーを定義します。  
  
 **親メンバー**  
 計算されたメンバーが下に表示されるメンバーを選択します。  
  
 **メモ**このオプションは、**親階層**でメジャー以外の階層が指定されている場合に使用できます。  
  
 **変更**  
 
  **[親メンバーの選択]** ダイアログ ボックスを表示し、 **[親メンバー]** のメンバーを選択します。 
  **[親メンバーの選択]** ダイアログ ボックスの詳細については、「[[親メンバーの選択] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](select-parent-member-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。  
  
 **式**  
 展開して、計算されるメンバーの多次元式 (MDX) を表示または編集します。  
  
 選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。  
  
> [!NOTE]  
>  この式は文字列または数値として評価することをお勧めします。  
  
 **追加のプロパティ**  
 展開して、 **[書式設定文字列]**、 **[表示]**、 **[空以外の動作]**、 **[色の式]**、および **[フォントの式]** の各オプションを表示します。  
  
 **書式設定文字列**  
 計算されるメンバーが返す値の書式設定に使用するために、MDX 書式設定文字列を入力するか、定義済みの書式設定文字列を選択します。  
  
 MDX 書式設定文字列の詳細については、「[FORMAT_STRING の内容 &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md)」を参照してください。  
  
 **[表示]**  
 
  **[True]** を選択すると、計算されるメンバーのクライアント アプリケーションへの表示を許可します。  
  
 **空でない動作**  
 計算されるメンバーの MDX で NON EMPTY クエリの解決に使用するメジャー名を選択します。 
  **[空以外の動作]** プロパティが空白の場合、メンバーが空であるかどうかを判断するために、計算されるメンバーを繰り返し評価する必要があります。 
  **[空以外の動作]** プロパティにメジャー名が格納されるときに、指定されたメジャーが空の場合は、計算されるメンバーは空として処理されます。  
  
> [!WARNING]  
>  このプロパティの使用は非推奨とされます。 これを設定しないでください。 詳細については、「 [SQL Server 2014 の非推奨の Analysis Services 機能](deprecated-analysis-services-features-in-sql-server-2014.md)」を参照してください。  
  
 **色の式**  
 展開して **[前景の色]** オプションおよび **[背景色]** オプションを表示します。  
  
 **[前景の色]**  
 計算されるメンバーの前景色を指定するために、MDX 式を入力します。  
  
 選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。  
  
 色の選択ボタンをクリックして、 **[色]** ダイアログ ボックスを表示し、指定する色の RGB 値 (赤、緑、青) を MDX 式に挿入します。 RGB 値の詳細については、「[FORE_COLOR および BACK_COLOR の内容 &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)」を参照してください。  
  
 **[背景色]**  
 計算されるメンバーの背景色を指定するために、MDX 式を入力します。  
  
 選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。  
  
 色の選択ボタンをクリックして、 **[色]** ダイアログ ボックスを表示し、指定する色の RGB 値 (赤、緑、青) を MDX 式に挿入します。 RGB 値の詳細については、「[FORE_COLOR および BACK_COLOR の内容 &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)」を参照してください。  
  
 **[フォントの式]**  
 展開して **[フォント名]**、 **[フォント サイズ]**、および **[フォント フラグ]** の各オプションを表示します。  
  
 **フォント名**  
 計算されるメンバーに使用するフォント名を指定するために、MDX 式を入力します。  
  
 選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。  
  
 フォントの選択ボタンをクリックして、 **[フォント]** ダイアログ ボックスを表示し、指定するフォントのプロパティ値を MDX 式に挿入します。 プロパティ値の詳細については、「[プロパティ値の作成および使用 &#40;MDX&#41;](creating-and-using-property-values-mdx.md)」を参照してください。  
  
 **フォントサイズ**  
 計算されたメンバーに使用するフォント サイズを指定するために、MDX 式を入力します。  
  
 選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。  
  
 フォントの選択ボタンをクリックして、 **[フォント]** ダイアログ ボックスを表示し、指定するフォントのプロパティ値を MDX 式に挿入します。 プロパティ値の詳細については、「[プロパティ値の作成および使用 &#40;MDX&#41;](creating-and-using-property-values-mdx.md)」を参照してください。  
  
 **[フォント フラグ]**  
 下線、太字など、計算されるメンバーに使用するフォントのフォント フラグを含む、ビットマップ形式の値を指定するために、MDX 式を入力します。  
  
 選択した要素を **[計算ツール]** ペインからこのオプションへドラッグして、選択した要素に対して MDX 構文を含めます。  
  
 フォントの選択ボタンをクリックして、 **[フォント]** ダイアログ ボックスを表示し、指定するフォントのプロパティ値を MDX 式に挿入します。 プロパティ値の詳細については、「[プロパティ値の作成および使用 &#40;MDX&#41;](creating-and-using-property-values-mdx.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Custom](multidimensional-models-olap-logical-cube-objects/calculations.md)   
 [計算されるメンバーの作成](multidimensional-models/create-calculated-members.md)   
 [キューブデザイナー &#40;Analysis Services-多次元データ&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [キューブデザイナーの計算 &#40;&#41; &#40;Analysis Services-多次元データ&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md)   
 [ツールバー &#40;キューブデザイナーの [計算] タブ&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [[スクリプトオーガナイザー &#40;計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](script-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [計算ツール &#40;[計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md)   
 [名前付きセットフォームエディター &#40;の [計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [スクリプトエディターの [&#40;の計算] タブ、キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
