---
title: 結果の取得 (基本) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], about result sets
- data sources [ODBC], result sets
- empty result sets [ODBC]
ms.assetid: 052870e3-3f3f-4f07-91da-b649348225f4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7abe4dd2f0bfb0b5302022d8e50cddc7df84f192
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020471"
---
# <a name="retrieving-results-basic"></a>結果の取得 (基本)
*結果セット*は、特定の条件に一致するデータソースの行セットです。 これは、クエリによって生成され、表形式でアプリケーションで使用できる概念テーブルです。 **SELECT**ステートメント、カタログ関数、およびいくつかのプロシージャによって結果セットが作成されます。 次の例では、最初の SQL ステートメントによって、Orders テーブルのすべての行とすべての列を含む結果セットが作成されます。2番目の SQL ステートメントでは、Orders テーブルの行に対して OrderID、販売員、および状態の各列を含む結果セットが作成されます。状態が [開く] の場合:  
  
```  
SELECT * FROM Orders  
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'  
```  
  
 結果セットを空にすることはできません。これは、結果セットとはまったく異なります。 たとえば、次の SQL ステートメントでは、空の結果セットが作成されます。  
  
```  
SELECT * FROM Orders WHERE 1 = 2  
```  
  
 空の結果セットは、行がないことを除いて、他の結果セットとは異なります。 たとえば、アプリケーションでは、結果セットのメタデータを取得し、行をフェッチして、結果セットの上にカーソルを閉じる必要があります。  
  
 データソースから行を取得してアプリケーションに返すプロセスは、*フェッチ*と呼ばれます。 このセクションでは、そのプロセスの基本部分について説明します。 ブロックカーソルやスクロール可能なカーソルなど、より高度なトピックについては、「[ブロックカーソル](../../../odbc/reference/develop-app/block-cursors.md)とスクロール可能な[カーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)」を参照してください。 行の更新、削除、および挿入の詳細については、「[データの更新の概要](../../../odbc/reference/develop-app/updating-data-overview.md)」を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [結果セットは作成されましたか?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
-   [結果セットのメタデータ](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
-   [バインディング列](../../../odbc/reference/develop-app/binding-columns.md)  
  
-   [データのフェッチ](../../../odbc/reference/develop-app/fetching-data.md)  
  
-   [カーソルを閉じる](../../../odbc/reference/develop-app/closing-the-cursor.md)
