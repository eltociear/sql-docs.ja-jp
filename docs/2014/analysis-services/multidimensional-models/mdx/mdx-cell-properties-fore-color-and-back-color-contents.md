---
title: FORE_COLOR と BACK_COLOR の内容 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- FORE_COLOR contents
- backgrounds [MDX]
- cells [MDX]
- colors [MDX]
- storing cell color information
- cell backgrounds
- BACK_COLOR contents
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ecd8bb157d7b501d29230c91d87f148ae738ff45
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074409"
---
# <a name="fore_color-and-back_color-contents-mdx"></a>FORE_COLOR および BACK_COLOR の内容 (MDX)
  セル プロパティ `FORE_COLOR` および `BACK_COLOR` は、セルのテキストの色および背景色についての情報を Microsoft Windows オペレーティング システムの赤緑青 (RGB) 形式で格納します。  
  
 通常の RGB 色の有効範囲は 0 ～ 16,777,215 (&H00FFFFFF) です。 この範囲の高位バイトは常に 0 で、最も低いバイトから意味を成すバイトまでの下位 3 バイトによって、赤、緑、および青それぞれの量が決まります。 赤、緑、および青のコンポーネントは、それぞれ 0 ～ 255 (&HFF) までの数値で表されます。  
  
## <a name="see-also"></a>参照  
 [MDX&#41;&#40;のセルプロパティの使用](mdx-cell-properties-using-cell-properties.md)  
  
  
