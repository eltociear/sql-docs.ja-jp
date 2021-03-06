---
title: データ長、バッファー長、および切り捨て |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- data length [ODBC]
- truncating data [ODBC]
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 2825c6e7-b9ff-42fe-84fc-7fb39728ac5d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8586157237db1158587e3c39f1320b78d8251fb5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081467"
---
# <a name="data-length-buffer-length-and-truncation"></a>データの長さ、バッファー長、および切り捨て
データ*長*は、データソースに格納されているのではなく、アプリケーションのデータバッファーに格納されるデータのバイト長です。 この区別は、データがデータソースよりもデータバッファー内のさまざまな型に格納されることが多いため、重要です。 データソースに送信されるデータについては、これはデータソースの型に変換する前のデータのバイト長です。 データソースからデータを取得する場合は、データバッファーの型に変換した後、切り捨てが行われる前に、データのバイト長が返されます。  
  
 固定長のデータ (整数や日付構造など) の場合、データのバイト長は常にデータ型のサイズになります。 一般に、アプリケーションはデータ型のサイズであるデータバッファーを割り当てます。 アプリケーションがより小さなバッファーを割り当てる場合、ドライバーはデータバッファーがデータ型のサイズであると想定しており、小さいバッファーに格納されるデータが切り捨てられないため、結果は未定義になります。 アプリケーションがより大きなバッファーを割り当てる場合、余分なスペースは使用されません。  
  
 文字やバイナリデータなどの可変長データの場合、データのバイト長は、バッファーのバイト長とは別のものであることを認識することが重要です。 これらの2つの長さの関係については、「 [Buffers](../../../odbc/reference/develop-app/buffers.md) 」セクションを参照してください。 データのバイト長がバッファーのバイト長を超える場合、ドライバーはフェッチされたデータをバッファーのバイト長に切り詰め、SQLSTATE 01004 (データが切り捨てられた) の SQL_SUCCESS_WITH_INFO を返します。 ただし、返されるバイト長は、切り捨てられたデータの長さです。  
  
 たとえば、アプリケーションがバイナリデータバッファーに50バイトを割り当てるとします。 ドライバーが10バイトのバイナリデータを返す場合は、バッファー内の10バイトを返します。 データのバイト長は10で、バッファーのバイト長は50です。 ドライバーが60バイトのバイナリデータを返す場合は、データを50バイトに切り捨て、バッファー内のバイトを返し、SQL_SUCCESS_WITH_INFO を返します。 データのバイト長は 60 (切り捨て前の長さ) であり、バッファーのバイト長は引き続き50です。  
  
 切り捨てられた列ごとに診断レコードが作成されます。 ドライバーによってこれらのレコードが作成され、アプリケーションで処理されるまでに時間がかかるため、切り捨てによってパフォーマンスが低下する可能性があります。 通常、アプリケーションでは、十分な大きさのバッファーを割り当てることでこの問題を回避できますが、長いデータを処理する場合には不可能です。 データの切り捨てが発生した場合、アプリケーションはより大きなバッファーを割り当て、データを再フェッチことがあります。すべての場合、これは当てはまりません。 **SQLGetData**への呼び出しを使用してデータを取得しているときに切り捨てが発生した場合、アプリケーションは既に返されたデータに対して**SQLGetData**を呼び出す必要はありません。詳細については、「[長い形式のデータの取得](../../../odbc/reference/develop-app/getting-long-data.md)」を参照してください。
