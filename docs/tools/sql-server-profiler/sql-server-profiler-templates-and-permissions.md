---
title: SQL Server プロファイラーのテンプレートと権限
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 6d00378a-5d74-463b-9ed6-a2685306a9d2
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 9a5bb7c38fe1a9984c66dd83414aed9d3b853aa6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307831"
---
# <a name="sql-server-profiler-templates-and-permissions"></a>SQL Server プロファイラーのテンプレートと権限

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] には、クエリが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の内部でどのように解決されるのかが表示されます。 これにより管理者は、どのような [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたは多次元式がサーバーに送信されるのか、また、そのサーバーではどのようにデータベースやキューブに接続して結果セットを返すのかを正確に知ることができます。  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用すると、以下の操作を行えます。  
  
-   再利用可能なテンプレートに基づいたトレースを作成する  
  
-   トレースを実行しながらトレース結果を監視する  
  
-   トレース結果をテーブルに保存する  
  
-   必要に応じて、トレースの開始、停止、一時停止、および変更を行う  
  
-   トレース結果を再生できます。  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、関心のあるイベントだけを監視できます。 トレースが大きくなりすぎた場合は、必要な情報だけをフィルターにより選択できます。その結果、イベント データのサブセットだけが収集されます。 監視するイベントが多すぎると、サーバーと監視プロセスのオーバーヘッドが増え、トレース ファイルやトレース テーブルが非常に大きくなる可能性があります。特に、監視プロセスを長期にわたって実行する場合はこの可能性が高くなります。  
  
> [!NOTE]  
>  トレース列の値が 1 GB を超えるとエラーを返し、1 GB を超えた値がトレース出力では切り捨てられます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|[説明]|  
|-----------|-----------------|  
|[SQL Server Profiler のテンプレート](../../tools/sql-server-profiler/sql-server-profiler-templates.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]に付属している定義済みのトレース テンプレートについて説明します。|  
|[SQL Server Profiler の実行に必要なアクセス許可](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]の実行に必要な権限について説明します。|  
|[トレースとトレース テンプレートの保存](../../tools/sql-server-profiler/save-traces-and-trace-templates.md)|トレース出力を保存する方法と、トレース定義をテンプレートに保存する方法について説明します。|  
|[トレース テンプレートを変更する](../../tools/sql-server-profiler/modify-trace-templates.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用してトレース テンプレートを変更する方法について説明します。|  
|[トレースを開始する](../../tools/sql-server-profiler/start-a-trace.md)|トレースを開始、一時停止、または停止するとどのような状態になるのかを説明します。|  
|[トレースと Windows パフォーマンス ログ データの関連付け](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler を使用して、Windows のパフォーマンス ログ データと特定のトレースを相互に関連付ける方法について説明します。|  
|[SQL Server Profiler を使用したトレースの表示と分析](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)|トレースを使用してデータのトラブルシューティングを行う方法、トレースに含まれているオブジェクト名を表示する方法、およびトレースに含まれているイベントを検索する方法について説明します。|  
|[SQL Server Profiler を使用したデッドロックの分析](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用してデッドロックの原因を特定する方法について説明します。|  
|[SQL Server Profiler での Showplan 結果を使用したクエリの分析](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して、Showplan と Showplan Statistics の結果を収集し表示する方法について説明します。|  
|[SQL Server Profiler でのトレースへのフィルターの適用](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、データ列にフィルターを設定しトレース出力をフィルター処理する方法について説明します。|  
|[トレースの再生](../../tools/sql-server-profiler/replay-traces.md)|トレースの再生について説明し、トレースの再生を実行するための条件を示します。|  
  
## <a name="see-also"></a>参照  
 [[SQL Server Profiler]](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server Profiler の起動](../../tools/sql-server-profiler/start-sql-server-profiler.md)  
  
  
