---
title: SQLRemoveDefaultDataSource 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDefaultDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDefaultDataSource
helpviewer_keywords:
- SQLRemoveDefaultDataSource function [ODBC]
ms.assetid: db803266-57df-4864-a41b-901247549c1f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cfefcd9f2f55e2d78c5c6e5b1bac7ce52e9033e5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68024597"
---
# <a name="sqlremovedefaultdatasource-function"></a>SQLRemoveDefaultDataSource 関数
**互換性**  
 導入されたバージョン: ODBC 1.0、非推奨  
  
 **まとめ**  
 ODBC 3.0 では、 **Sqlremovedefaultdatasource**関数は、ODBC_REMOVE_DEFAULT_DSN の*frequest*引数を使用して[sqlconfigdatasource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)への呼び出しに置き換えられました。 ODBC 2.x のインストールプログラムがこの関数を呼び出すと、ODBC インストーラーによって、次の**Sqlconfigdatasource**呼び出しにマップさ*れます。*  
  
```cpp  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
