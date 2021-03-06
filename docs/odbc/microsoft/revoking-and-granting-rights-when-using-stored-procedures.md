---
title: ストアドプロシージャを使用する場合の権限の取り消しと許可 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 24070039-03ab-4623-a681-6308802eb399
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 91fcf722554fe1840465329e707c792a6bbab6db
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67987953"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>ストアド プロシージャ使用時の権限の取り消しと付与
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用してください。  
  
 Microsoft ODBC Driver for Oracle では、ストアドプロシージャによってアクセスされるテーブルでユーザー権限が許可されている場合に、次のエラーメッセージが返されます。  
  
 SQL_ERROR =-1  
  
 szErrorMsg = "[Microsoft] [ODBC driver for Oracle] パラメーターの数が正しくありません"  
  
 szErrorMsg = "[Microsoft] [ODBC driver for Oracle] 構文エラーまたはアクセス違反"  
  
 このシナリオでは、Oracle OCI 関数 Odessp () の呼び出しは失敗しますが、既定のパラメーターを実装するために必要です。 基になるテーブルの権限を変更した後、ストアドプロシージャを再実行する前に再コンパイルする必要があります。
