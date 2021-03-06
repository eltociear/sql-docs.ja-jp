---
title: メモリ内データベース システムの機能とテクノロジ
ms.date: 10/30/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- in-memory systems
- in-memory technologies
- in-memory features
- database, in-memory database
- system, in-memory system
- features, in-memory features
- in-memory
ms.assetid: 11f8017e-5bc3-4bab-8060-c16282cfbac1
author: briancarrig
ms.author: brcarrig
manager: amitban
ms.openlocfilehash: df8bb9e603d5455a2e42393df4c40956000cb037
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76831591"
---
# <a name="in-memory-database-systems-and-technologies"></a>メモリ内データベース システムとテクノロジ

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このページは、SQL Server 内のインメモリ機能とテクノロジに関するリファレンス ページとして使用できます。 概念上、メモリ内データベース システムとは、最新のデータベース システムで使用できるより大きなメモリ容量を利用するように設計されたデータベース システムを指します。 メモリ内データベースは、本質的にリレーショナルまたは非リレーショナルです。

多くの場合、メモリ内データベース システムのパフォーマンスの利点は主として、メモリ内にあるデータにアクセスする方が利用可能な最速のディスク サブシステム上にあるデータにアクセスよりも (桁違いに) 高速であることに起因すると考えられます。 しかし、多くの SQL Server ワークロードは、使用可能なメモリ内にワーキング セット全体を収めることができます。 多くのメモリ内データベース システムは、データをディスクに永続化することができ、使用可能なメモリ内にデータ セット全体を常に収めることができるとは限りません。

リレーショナル データベースのワークロードでは、かなり低速でも持続性のあるメディアに代わって、高速の揮発性キャッシュが主流です。 これは、ワークロードを管理するための特定のアプローチを必要とします。 メモリ転送速度の高速化、容量の増加、または永続メモリによって与えられる機会により、リレーショナル データベースのワークロード管理への新しいアプローチを促進させることができる新しい機能とテクノロジの開発が容易になります。

## <a name="hybrid-buffer-pool"></a>ハイブリッド バッファー プール

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[ハイブリッド バッファー プール](../database-engine/configure-windows/hybrid-buffer-pool.md) は、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]を搭載した Windows と Linux の両方のプラットフォームのバイト アドレス指定可能な永続メモリ ストレージ デバイス上にあるデータベース ファイル用のバッファー プールを拡張します。

## <a name="memory-optimized-tempdb-metadata"></a>メモリ最適化 `tempdb` メタデータ

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では、[メモリ最適化 tempdb メタデータ](./databases/tempdb-database.md#memory-optimized-tempdb-metadata)という新機能が導入されています。この機能により、効果的に一部の競合ボトルネックが除去され、tempdb が多用されるワークロードに対して新たなレベルのスケーラビリティが実現されます。

## <a name="in-memory-oltp"></a>インメモリ OLTP

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[インメモリ OLTP](./in-memory-oltp/in-memory-oltp-in-memory-optimization.md) は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] および [!INCLUDE[ssSDS](../includes/sssds-md.md)] で、トランザクション処理のパフォーマンスの最適化、データ インジェスト、データの読み込み、一時的なデータのシナリオに使用できるデータベース テクノロジです。

## <a name="configuring-persistent-memory-support-for-linux"></a>Linux 用に永続メモリのサポートを構成する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[sqlv15](../includes/sssqlv15-md.md)] では、`ndctl` ユーティリティを使用して永続メモリ (PMEM) を構成する方法が説明されています。[永続メモリ](../linux/sql-server-linux-configure-pmem.md) に関するページをご覧ください。

## <a name="persisted-log-buffer"></a>永続化されたログ バッファー

[!INCLUDE[ssSQL16](../includes/sssql16-md.md)] の Service Pack 1 では、WRITELOG 待機によってバインドされた、書き込み負荷の高いワークロードのパフォーマンスの最適化が導入されました。 ログ バッファーの格納には永続メモリが使用されます。 このバッファーは小さく (ユーザー データベースあたり 20MB)、トランザクション ログに書き込まれたトランザクションを書き込むためにディスクにフラッシュする必要があります。 書き込み負荷の高い OLTP ワークロードの場合、このフラッシュ メカニズムがボトルネックになる可能性があります。 ログ バッファーを永続メモリに格納すると、ログを書き込むために必要な操作の数が削減され、トランザクション時間全体を短縮し、ワークロードのパフォーマンスを向上することができます。 このプロセスは、[ログ末尾のキャッシング]( https://blogs.msdn.microsoft.com/bobsql/2016/11/08/how-it-works-it-just-runs-faster-non-volatile-memory-sql-server-tail-of-log-caching-on-nvdimm/)として導入されました。 しかし、[ログ末尾のバックアップ](./backup-restore/tail-log-backups-sql-server.md)、およびログの末尾は、書き込まれてはいるがまだバックアップされていないトランザクション ログの一部であるという従来の認識と矛盾することが考えられます。 正式な機能名は、「永続化されたログ バッファー」であるため、ここでは、この名前を使用しています。

「[Add persisted log buffer to a database](./databases/add-persisted-log-buffer.md)」 (永続化されたログ バッファーをデータベースに追加する) を参照してください。
