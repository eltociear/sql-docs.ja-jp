---
title: 反復可能な Read 分離レベルを使用したデッドロック |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- deadlocks in RDS [ADO]
- read repeatable in RDS [ADO]
ms.assetid: 29f3683f-12f3-4304-8a54-fe133c25a423
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c8e4e59606f3b68fbd9ce272db8ea8a50ab53e88
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922714"
---
# <a name="deadlocks-with-read-repeatable-isolation-level"></a>Read Repeatable 分離レベルでのデッドロック
カスタムビジネスオブジェクトが分離レベルを使用して SQL Server にアクセスし、同じトランザクション内でクエリと更新を送信する2つのクライアントによってビジネスオブジェクトが同時に呼び出される場合、デッドロックが発生する可能性があります。 リモートデータサービスは、プロセスの1つがタイムアウトしてデッドロックを解除できるように設計されていますが、そのクライアントの更新は失敗します。  
  
 タイムアウトの長さを変更するには、 [Cursor Service](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) **コマンドの [タイムアウト]** 動的プロパティを使用します。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)



