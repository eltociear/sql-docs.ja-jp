---
title: SQL Server の Plan Cache オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Plan Cache object
- SQLServer:Plan Cache
ms.assetid: 225e2b02-8d2f-4f29-9eba-f5847c36ea99
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ff1acb1fb3af2708b14b31eeb82aa0989685630c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68210819"
---
# <a name="sql-server-plan-cache-object"></a>SQL Server の Plan Cache オブジェクト
  **Plan Cache** オブジェクトには、ストアド プロシージャ、アドホックおよび準備済みの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメント、トリガーなどのオブジェクトを保存するために、 [!INCLUDE[tsql](../../includes/tsql-md.md)] がどのようにメモリを使用しているかを監視するためのカウンターがあります。 **Plan Cache** オブジェクトの複数のインスタンスを同時に監視できます。各インスタンスは、監視される異なる種類のクエリ プランを表します。  
  
 次の表では、 **SQLServer:Plan Cache**カウンターについて説明します。  
  
|SQL Server Plan Cache のカウンター|[説明]|  
|------------------------------------|-----------------|  
|**Cache Hit Ratio**|キャッシュ ヒットとキャッシュ参照の比率。|  
|**キャッシュオブジェクト数**|キャッシュ内にあるキャッシュ オブジェクトの数。|  
|**キャッシュページ**|キャッシュ オブジェクトによって使用される 8 KB ページの数。|  
|**使用中のキャッシュオブジェクト**|使用中のキャッシュ オブジェクトの数。|  
  
 オブジェクトの各カウンターには、次のインスタンスが含まれています。  
  
|Plan Cache インスタンス|[説明]|  
|-------------------------|-----------------|  
|**_Total**|すべての種類のキャッシュ インスタンスの情報。|  
|**Sql プラン**|自動パラメーター化クエリを含むアドホック [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリから作成されたクエリ プランか、 [!INCLUDE[tsql](../../includes/tsql-md.md)] sp_prepare **または** sp_cursorprepare **を使用して準備された**ステートメントから作成されたクエリ プラン。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、後で同一の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが実行された場合の再利用に備えて、アドホック [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのプランをキャッシュに格納します。 ユーザーによるパラメーター化クエリも、明示的に準備されていない場合も含めて Prepared SQL Plans として監視されます。|  
|**オブジェクトプラン**|ストアド プロシージャ、関数、またはトリガーの作成によって生成されたクエリ プラン。|  
|**バインドされたツリー**|ビュー、規則、計算済みの列、および CHECK 制約のための正規化ツリー。|  
|**拡張ストアドプロシージャ**|拡張ストアド プロシージャのカタログ情報。|  
|**テーブル変数 & 一時テーブル**|一時テーブルおよびテーブル変数に関連するキャッシュ情報。|  
  
## <a name="see-also"></a>参照  
 [サーバーメモリのサーバー構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [SQL Server、Buffer Manager オブジェクト](sql-server-buffer-manager-object.md)   
 [リソース使用状況の監視 &#40;システムモニタ&#41;](monitor-resource-usage-system-monitor.md)  
  
  
