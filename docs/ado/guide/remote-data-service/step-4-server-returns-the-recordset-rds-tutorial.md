---
title: '手順 4: サーバーがレコードセットを返す (RDS チュートリアル) |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], server returns Recordset
ms.assetid: 3d1855c4-419c-4810-b5ea-6c874b5e2905
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bd243b21b7003c524c3483f5b8d7bb92be1e18d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922066"
---
# <a name="step-4-server-returns-the-recordset-rds-tutorial"></a>手順 4: サーバーがレコード セットを返す (RDS チュートリアル)
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
 RDS は、取得した**レコードセット**オブジェクトをクライアントに送り返すことのできる形式に変換します (つまり、**レコードセット**を*マーシャリング*します)。 変換の正確な形式と送信方法は、サーバーがインターネット上にあるか、イントラネット上にあるか、ローカルエリアネットワーク上にあるか、またはダイナミックリンクライブラリであるかによって異なります。 ただし、この詳細は重要ではありません。これが重要なのは、RDS が**レコードセット**をクライアントに送り返すことだけです。  
  
 クライアント側では、**レコードセット**オブジェクトが返され、ローカル変数に割り当てられます。  
  
```vb
Sub RDSTutorial4()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "https://yourServer")  
   Set RS = DF.Query("DSN=Pubs", "SELECT * FROM Authors")  
...  
```  
  
## <a name="see-also"></a>参照  
 [手順 5: DataControl を使用できるようにする (RDS チュートリアル)](../../../ado/guide/remote-data-service/step-5-datacontrol-is-made-usable-rds-tutorial.md)   
 [RDS のチュートリアル (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
