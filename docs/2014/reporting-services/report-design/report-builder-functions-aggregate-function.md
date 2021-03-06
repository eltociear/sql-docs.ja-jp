---
title: 集計関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 16ce643f-bbb3-40a5-ba78-7aed73156f3e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0c58b99b616c07e2144a30a9ea996b135b6f8a4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66105338"
---
# <a name="aggregate-function-report-builder-and-ssrs"></a>集計関数 (レポート ビルダーおよび SSRS)
  データ プロバイダーの定義に従い、指定された式のカスタムの集計を返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>構文  
  
```  
  
Aggregate(expression, scope)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *条件*  
 この集計関数の実行対象の式です。 指定する式は、単純なフィールド参照の式である必要があります。  
  
 *検索*  
 (`String`) 集計関数の適用先となるレポート アイテムを含むデータセット、グループ、またはデータ領域の名前です。 *スコープ*は文字列定数である必要があり、式にすることはできません。 
  *scope* を指定しない場合、現在のスコープが使用されます。  
  
## <a name="return-type"></a>戻り値の型  
 戻り値の型はデータ プロバイダーによって決められます。 プロバイダーがこの関数をサポートしていない場合や、データが取得できなかった場合は、`Nothing` が返されます。  
  
## <a name="remarks"></a>解説  
 
  `Aggregate` 関数を使用すると、外部データ ソース上で計算される集計を使用できます。 この機能のサポートは、データ拡張機能によって異なります。 たとえば、データ処理[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]拡張機能は、MDX クエリからフラットな行セットを取得します。 結果セット内の一部の行には、データ ソース サーバーで計算される集計値を含めることができます。 これらは、 *サーバー集計*と呼ばれます。 サーバー集計を [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のグラフィカル クエリ デザイナーで表示するには、ツール バーの **[集計の表示]** ボタンを使用します。 詳細については、「[Analysis Services の MDX クエリ デザイナーのユーザー インターフェイス (レポート ビルダー)](../analysis-services-mdx-query-designer-user-interface-report-builder.md)」を参照してください。  
  
 Tablix データ領域の詳細行にデータセットの集計値および詳細値の組み合わせを表示する場合、通常、サーバー集計値は詳細データではないため含まれません。 ただし、データセットから取得したすべての値を表示し、集計データを計算および表示する方法をカスタマイズできます。  
  
 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、サーバー集計値を詳細行に表示するかどうかを判断するため、レポート内の式で `Aggregate` 関数の使用が検出されます。 データ領域の式に `Aggregate` を含めると、サーバー集計値は、詳細行ではなくグループの合計行または総計行のみに表示されます。 サーバー集計値を詳細行に表示する場合は、`Aggregate` 関数を使用しないでください。  
  
 この既定の動作を変更するには、 **[データセットのプロパティ]** ダイアログ ボックスの **[小計を詳細行として解釈]** オプションの値を変更します。 このオプションを `True` に設定すると、サーバー集計値を含むすべてのデータが詳細データとして表示されます。 
  `False` に設定すると、サーバー集計値は合計として表示されます。 このプロパティの設定は、このデータセットにリンクされているすべてのデータ領域に影響します。  
  
> [!NOTE]  
>  
  `Aggregate` を参照するレポート アイテムを含むすべてのグループでは、そのグループ式に単純なフィールド参照 (`[FieldName]` など) が指定されている必要があります。 複雑なグループ式を使用するデータ領域で `Aggregate` を使用することはできません。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ処理拡張機能では、`LevelProperty` 関数を使用した集計がサポートされるように、(`MemberProperty` 型ではなく) `Aggregate` 型の MDX フィールドをクエリに含める必要があります。  
  
 *式*には、入れ子になった集計関数への呼び出しを含めることができます。ただし、次の例外と条件があります。  
  
-   入れ子集計の*スコープ*は、外側の集計のスコープと同じであるか、そのスコープに含まれている必要があります。 式内のすべてのスコープについては、1 つのスコープがそれ以外のすべてのスコープに対する子であるようなリレーションシップが必要です。  
  
-   入れ子集計の*スコープ*にデータセットの名前を指定することはできません。  
  
-   *式*には、 `First`、 `Last`、 `Previous`、また`RunningValue`は関数を含めることはできません。  
  
-   *式*には、*再帰*を指定する入れ子になった集計を含めることはできません。  
  
 詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。  
  
 再帰的集計については、「[複数の再帰型階層グループの作成 &#40;レポート ビルダーおよび SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="comparing-the-aggregate-and-sum-functions"></a>Aggregate 関数と Sum 関数の比較  
 
  `Aggregate` 関数はデータ プロバイダーまたはデータ処理拡張機能によって計算される値を返すという点で、`Sum` 関数は `Aggregate` などの数値の集計関数と異なります。 のような`Sum`数値集計関数は、*スコープ*パラメーターによって決定されるデータセットのデータセットに基づいて、レポートプロセッサによって計算される値を返します。 詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」に示されている集計関数を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、 `LineTotal`フィールドのサーバー集計値を取得する式を示します。 式は、 `GroupbyOrder`グループに属する行内のセルに追加されます。  
  
```  
=Aggregate(Fields!LineTotal.Value, "GroupbyOrder")  
```  
  
## <a name="see-also"></a>参照  
 [レポートでの式の使用 (レポート ビルダーおよび SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
