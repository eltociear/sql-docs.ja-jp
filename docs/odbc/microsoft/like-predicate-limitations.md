---
title: LIKE 述語の制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8cd3cebfcf20df2f8a3a786ea66fd28dd76307c0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68119712"
---
# <a name="like-predicate-limitations"></a>LIKE 述語の制限事項
列のデータが255文字を超える場合、LIKE 比較は最初の255文字にのみ基づいて行われます。  
  
 プロシージャで使用される LIKE は、定数パターンでのみサポートされます。 デスクトップデータベースドライバーは、パターンマッチングと同様に SQL-92 をサポートしています。  
  
 LIKE 述語での escape 句の使用はサポートされていません。  
  
 数値データ型または float データ型のデータを含む列に対して、LIKE 比較を実行することはできません。 結果は予測できない場合があります。 詳細については、 *『 Microsoft Jet データベースエンジンプログラマーズガイド』* を参照してください。
