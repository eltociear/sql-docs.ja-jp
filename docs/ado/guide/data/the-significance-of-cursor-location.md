---
title: カーソル位置の意味 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- server-side cursors [ADO]
- cursors [ADO], client-side
- client-side cursors [ADO]
- cursors [ADO], server-side
ms.assetid: 70ef5b1c-0459-41a1-b796-031f61a29a8a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e663ac5cdcf85fc1d050e0f066b597d29141ebfd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923898"
---
# <a name="the-significance-of-cursor-location"></a>カーソル位置の有意性
すべてのカーソルは、一時リソースを使用してデータを保持します。 これらのリソースには、メモリ、ディスクページングファイル、一時ディスクファイル、またはデータベース内の一時的なストレージを使用できます。 これらのリソースがクライアントコンピューターに配置されている場合、カーソルは*クライアント側*カーソルと呼ばれます。 これらのリソースがサーバーに配置されている場合、カーソルは*サーバー側*カーソルと呼ばれます。  
  
## <a name="client-side-cursors"></a>クライアント側カーソル  
 ADO では、 **AdUseClient Cursor Locationenum**を使用して、クライアント側のカーソルを呼び出します。 キーセット以外のクライアント側カーソルを使用すると、サーバーは結果セット全体をネットワーク経由でクライアントコンピューターに送信します。 クライアントコンピューターは、カーソルと結果セットで必要とされる一時的なリソースを提供し、管理します。 クライアント側アプリケーションでは、結果セット全体を参照して、必要な行を特定できます。  
  
 静的およびキーセットドリブンのクライアント側カーソルには、多数の行が含まれている場合、ワークステーションに大きな負荷がかかることがあります。 すべてのカーソルライブラリは、何千もの行を含むカーソルを構築できますが、このような大きな行セットをフェッチするように設計されたアプリケーションは、パフォーマンスが低下する可能性があります。 もちろん、例外もあります。 アプリケーションによっては、大規模なクライアント側カーソルが完全に適切であり、パフォーマンスが問題になることがあります。  
  
 クライアント側カーソルの明らかな利点の1つは、迅速な対応です。 結果セットがクライアントコンピューターにダウンロードされると、行の参照が非常に高速になります。 カーソルのリソース要件はサーバー上ではなく個々のクライアントに配置されるため、通常、アプリケーションはクライアント側のカーソルを使用して拡張できます。  
  
## <a name="server-side-cursors"></a>サーバー側カーソル  
 ADO で、 **Aduseserver Cursor Locationenum**を使用して、サーバー側カーソルを呼び出します。 サーバー側カーソルを使用すると、サーバーはサーバーコンピューターによって提供されるリソースを使用して結果セットを管理します。 サーバー側カーソルは、要求されたデータのみをネットワーク経由で返します。 この種のカーソルは、特にネットワークトラフィックが過剰に問題になる状況では、クライアント側のカーソルよりもパフォーマンスが向上する場合があります。  
  
 ただし、サーバー側カーソルは、アクティブなクライアントごとに、一時的に貴重なサーバーリソースであることを指摘することが重要です。 サーバーハードウェアがアクティブなクライアントによって要求されたすべてのサーバー側カーソルを管理できることを確認するために、適切に計画する必要があります。 また、サーバー側カーソルは、単一の行へのアクセスのみを提供するので、処理が遅くなる可能性があります。使用できるバッチカーソルがありません。  
  
 サーバー側カーソルは、レコードを挿入、更新、または削除するときに便利です。 サーバー側カーソルを使用すると、同じ接続に複数のアクティブなステートメントを含めることができます。
