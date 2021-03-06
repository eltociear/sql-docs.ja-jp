---
title: VARCHAR 列のサイズ (ODBC Driver for Oracle) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- varchar column size [ODBC]
- ODBC driver for Oracle [ODBC], data types
ms.assetid: eb4cb410-3d00-4251-8c5e-a06f36c4dac7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3a3156c3f71eb4b3f7b8319da5d5fec7514f08b6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087964"
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>VARCHAR 列のサイズ (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用してください。  
  
 Oracle8 では、VARCHAR 列の最大サイズが2000から4000バイトに増加しました。 Oracle 7.3. x クライアントソフトウェアでは、2000バイトを超えるパラメーター値をバインドすることはできません。 したがって、2000バイトを超える VARCHAR 型の列を含むテーブルを作成した場合、クライアントソフトウェアの2000バイトの制限を超えるデータを使用して、パラメーター化された挿入、更新、削除、およびクエリを実行することはできません。 ODBC Driver for Oracle と OLE DB Provider for Oracle は、パラメーター化された挿入、更新、削除、およびクエリを使用するため、この場合は ORA-01026 エラーを報告します。 Oracle クライアントソフトウェアによって適用される制限内のデータは機能します。 この2000バイトの制限を回避するには、クライアントソフトウェアを Oracle8 (8.0.4.1.1 c 以降) にアップグレードする必要があります。
