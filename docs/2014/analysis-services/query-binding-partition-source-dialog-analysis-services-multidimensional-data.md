---
title: '[クエリバインドの詳細] ([パーティションソース] ダイアログボックス) (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionfilterexpression.f1
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 604a42cc0b3519f1034733e12f72dc1a7c969ce6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070573"
---
# <a name="query-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a>クエリ バインドの詳細 ([パーティション ソース] ダイアログ ボックス) (Analysis Services - 多次元データ)
  
  **[パーティション ソース]** ダイアログ ボックスの **[クエリ バインド]** オプションを使用すると、パーティション用のデータを表示するクエリを指定できます。 このペインを表示するには、 **[パーティション ソース]** ダイアログ ボックスの **[バインドの種類]** オプションで **[クエリ バインド]** を選択します。  
  
## <a name="options"></a>オプション  
 **データソース**  
 パーティションのファクト データを提供するためのクエリが実行されるデータ ソースを選択します。  
  
 **クエリ**  
 パーティションを処理する際にファクト データの取得に使用される SQL ステートメントを入力、または変更します。  
  
> [!IMPORTANT]  
>  WHERE 句を指定することにより、レコードのサブセットをこのパーティションで使用できます。 複数のパーティションが 1 つのファクト テーブルに基づいている場合は、データを複製しないでください。 詳細については、「[[パーティションソース] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。  
  
 **オフ**  
 クリックすると、 **クエリ** 内のステートメントが有効な SQL ステートメントであるかどうかが確認されます。  
  
## <a name="see-also"></a>参照  
 [[パーティションソース] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
