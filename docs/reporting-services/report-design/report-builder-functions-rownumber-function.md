---
title: RowNumber 関数 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e918a674b48eeb34fad7ea660b7e907fc9dcb44b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "65577187"
---
# <a name="report-builder-functions---rownumber-function"></a>レポート ビルダー関数 - RowNumber 関数
  指定されたスコープの実行中の行数を返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>構文  
  
```  
  
RowNumber(scope)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *スコープ (scope)*  
 (**String**) 行数を評価するコンテキストを示すデータセット、データ領域、またはグループの名前か、NULL (**では** Nothing [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]) です。 **Nothing** は、最も外側のコンテキスト (通常はレポート データセット) を示します。  
  
## <a name="remarks"></a>解説  
 **RunningValue** では、集計関数の実行中の値が返されますが、 [RowNumber](../../reporting-services/report-design/report-builder-functions-runningvalue-function.md) では、指定したスコープ内の行数の実行中の値が返されます。 スコープを指定すると、行数を 1 にリセットするタイミングが指定されます。  
  
 *scope* には、式を指定することはできません。 *scope* には、コンテナー スコープを指定する必要があります。 一般的なスコープは、外側から内側の順に、レポート データセット、データ領域、行グループまたは列グループです。  
  
 列全体で値を増分するには、列グループの名前であるスコープを指定します。 行の下方向に向かって数を増分するには、行グループの名前であるスコープを指定します。  
  
> [!NOTE]  
>  行グループと列グループの両方を指定する複数の集計を含めた式はサポートされていません。  
  
 詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)」および「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。  
  
## <a name="code-example"></a>コード例  
 Tablix データ領域の詳細行の **BackgroundColor** プロパティに使用できる式を次に示します。この式では、各グループの詳細行の色を交互に設定し、常に先頭が白になるようにしています。  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a>参照  
 [レポートでの式の使用 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [合計、集計、および組み込みコレクションの式のスコープ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
