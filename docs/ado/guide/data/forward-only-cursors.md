---
title: 順方向専用カーソル |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], forward-only
- forward-only cursors [ADO]
ms.assetid: 2b1e062f-3294-4a6f-8241-a17045c4df18
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e84fbf2b8fda2fa2b14088af1e0830d8109aba8a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925307"
---
# <a name="forward-only-cursors"></a>順方向専用カーソル
既定のカーソルの種類 (順方向専用 (またはスクロール不可能) のカーソル) は、結果セットを前方にのみ移動できます。 順方向専用カーソルは、スクロールをサポートしていません (結果セット内で前後に移動する機能)。結果セットの先頭から末尾までの行のフェッチのみがサポートされます。 一部の順方向専用カーソル (SQL Server カーソルライブラリなど) では、結果セット内の行に影響を与えるすべての insert、update、および delete ステートメントが、行がフェッチされたときに表示されます。 ただし、カーソルは後方にスクロールできないので、データベース内の行のフェッチ後にその行に対して行われた変更内容は、カーソル内で確認できません。  
  
 現在の行のデータが処理された後、順方向専用カーソルは、そのデータを保持するために使用されたリソースを解放します。 順方向専用カーソルは既定では動的であり、現在の行が処理されるとすべての変更が検出されることを意味します。 これにより、カーソルを開く時間が短縮され、基になるテーブルに対して行われた更新を結果セットで表示できるようになります。  
  
 前方参照専用カーソルは後方スクロールをサポートしていませんが、アプリケーションはカーソルを閉じてから再度開いて、結果セットの先頭に戻ることができます。 これは、少量のデータを処理する効果的な方法です。 別の方法として、アプリケーションは結果セットを1回読み取り、データをローカルにキャッシュして、ローカルデータキャッシュを参照することもできます。  
  
 アプリケーションで結果セットをスクロールする必要がない場合は、順方向専用カーソルを使用すると、オーバーヘッドを最小限に抑えてデータをすばやく取得できます。 ADO で順方向専用カーソルを使用することを示すには、 **AdOpenForwardOnly Cursor Typeenum**を使用します。  
  
## <a name="see-also"></a>参照  
 [静的カーソル](../../../ado/guide/data/static-cursors.md)   
 [キーセットカーソル](../../../ado/guide/data/keyset-cursors.md)   
 [動的カーソル](../../../ado/guide/data/dynamic-cursors.md)
