---
title: bcp_sendrow |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_sendrow
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4bb5375de9769046c12f56f91d5c26e41090564b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73782497"
---
# <a name="bcp_sendrow"></a>bcp_sendrow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  プログラム変数から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にデータ行を送信します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC hdbc);  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>解説  
 **Bcp_sendrow**関数は、プログラム変数から行を作成し、に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]送信します。  
  
 **Bcp_sendrow**を呼び出す前に、行データを含むプログラム変数を指定するために[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)の呼び出しを行う必要があります。  
  
 Long 型の可変長データ型を指定して**bcp_bind**が呼び出された場合 (たとえば、SQLTEXT の*EDATATYPE*パラメーターと NULL 以外の*pData*パラメーター)、 **bcp_sendrow**は他のデータ型の場合と同様に、データ値全体を送信します。 ただし、 **bcp_bind**に*PDATA*パラメーターが NULL の場合は、指定されたデータを含むすべての列がに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]送信された直後に、 **bcp_sendrow**制御がアプリケーションに返されます。 その後、アプリケーションは[bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)を繰り返し呼び出して、長い可変長データ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をチャンクとして一度に送信できます。 詳細については、「 [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)」を参照してください。  
  
 プログラム**** 変数からテーブルに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]行を一括コピーするために bcp_sendrow を使用する場合、ユーザーが[bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)または[bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)を呼び出したときにのみ行がコミットされます。 ユーザーは、 *n*行ごとに**bcp_batch**を呼び出すことも、受信データの期間間になどがあるときに呼び出すこともできます。 **Bcp_batch**が呼び出されない場合、 **bcp_done**が呼び出されたときに行がコミットされます。  
  
 での[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]一括コピーの重大な変更については、「 [ODBC&#41;&#40;の一括コピー操作の実行](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
