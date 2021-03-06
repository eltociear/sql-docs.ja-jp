---
title: SQL ツールの概要
description: SQL Server、Azure SQL (Azure SQL データベース、Azure SQL マネージド インスタンス、SQL 仮想マシン)、および Azure SQL データ ウェアハウス用の SQL クエリおよび管理ツール。
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ''
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 12/06/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: f4aaea790cf1e308b0675792b110ed129a55ed97
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "76516265"
---
# <a name="sql-tools-overview"></a>SQL ツールの概要

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

データベースを管理するには、ツールが必要です。 クラウド内、Windows 上、macOS 上、または [Linux](../linux/sql-server-linux-overview.md) 上のいずれでデータベースが実行されているかにかかわらず、ツールをデータベースと同じプラットフォーム上で実行する必要はありません。

次の表にまとめたさまざまな SQL ツールのリンクを参照してください。

> [!Note]
> SQL Server をダウンロードするには、[SQL Server のインストール](../database-engine/install-windows/install-sql-server.md)に関する記事を参照してください。

## <a name="recommended-tools"></a>推奨されるツール

次のツールには、グラフィカル ユーザー インターフェイス (GUI) が用意されています。

| ツール | 説明 | オペレーティング システム |
|:--|:--|:--|
| [ **![ADS の画像](../tools/media/overview-sql-tools/azure-data-studio.svg)</br></br>Azure Data Studio**](../azure-data-studio/download.md) | 必要に応じて SQL クエリを実行し、テキスト、JSON、または Excel 形式で結果を表示および保存できる軽量のエディターです。 使い慣れたオブジェクト ブラウズ エクスペリエンスで、データの編集、お気に入りのデータベース接続の整理、データベース オブジェクトの参照を行います。 | **Windows</br>macOS</br>Linux** |
| [ **![SSMS の画像](../tools/media/overview-sql-tools/ssms.svg)</br></br>SQL Server Management Studio (SSMS)** ](../ssms/download-sql-server-management-studio-ssms.md) | GUI を完全にサポートし、SQL Server インスタンスまたはデータベースを管理します。 SQL Server、Azure SQL Database、および SQL Data Warehouse のすべてコンポーネントのアクセス、構成、管理、運営、および開発を行います。 さまざまなグラフィック ツールと、機能の豊富な多くのスクリプト エディターを結合して、あらゆるスキル レベルの開発者やデータベース管理者が SQL にアクセスできる包括的なユーティリティが 1 つ用意されています。 | **Windows** |
| [ **![SSDT の画像](../tools/media/overview-sql-tools/ssdt.svg)</br>SQL Server Data Tools (SSDT)** ](../ssdt/download-sql-server-data-tools-ssdt.md) | SQL Server リレーショナル データベース、Azure SQL データベース、Analysis Services (AS) データ モデル、Integration Services (IS) パッケージ、Reporting Services (RS) レポートをビルドするための、最新の開発ツールです。 SSDT を使うと、 **[Visual Studio](https://visualstudio.microsoft.com/downloads/)** でアプリケーションを開発する場合と同じくらい簡単に、任意の SQL Server コンテンツ タイプを設計および展開できます。 | **Windows** |
| [ **![VS Code の画像](../tools/media/overview-sql-tools/visual-studio-code.svg)</br></br>Visual Studio Code**](https://code.visualstudio.com/) | Visual Studio Code 用の **[mssql 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)** は、SQL Server への接続と、Visual Studio Code での T-SQL の豊富な編集エクスペリエンスをサポートする公式の SQL Server 拡張機能です。 軽量エディターで T-SQL スクリプトを作成できます。 | **Windows</br>macOS</br>Linux** |

## <a name="command-line-tools"></a>コマンドライン ツール

次のツールは、主なコマンドライン ツールです。

| ツール | 説明 | オペレーティング システム |
|:--|:--|:--|
|[**mssql-cli (プレビュー)** ](mssql-cli.md)|**mssql-cli** は、SQL Server のクエリを実行するための対話型コマンドライン ツールです。 また、IntelliSense、構文の強調表示などの機能を備えたコマンドライン ツールを使用して SQL Server のクエリを実行できます。 | **Windows</br>macOS</br>Linux** |
| [**sqlpackage**](sqlpackage.md) |**sqlpackage** は、一部のデータベース開発タスクを自動化するコマンドライン ユーティリティです。 |**Windows</br>macOS</br>Linux** |
|[**SQL Server PowerShell**](../powershell/sql-server-powershell.md)| **SQL Server PowerShell** には、SQL を操作するためのコマンドレットが用意されています。 | **Windows</br>macOS</br>Linux** |
| [**sqlcmd**](sqlcmd-utility.md) |**sqlcmd** ユーティリティを使用すると、Transact-SQL ステートメントやシステム プロシージャ、スクリプト ファイルをコマンド プロンプトから入力することができます。 | **Windows</br>macOS</br>Linux** |
|[**bcp**](bcp-utility.md)|**b**ulk **c**opy **p**rogram ユーティリティ (**bcp**) は、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスと、ユーザー指定の形式のデータ ファイルとの間でデータの一括コピーを行います。| **Windows</br>macOS</br>Linux** |
|[**mssql-scripter (プレビュー)** ](https://github.com/Microsoft/mssql-scripter) | **mssql-scripter** は、SQL Server データベースのスクリプトを作成するためのマルチプラットフォーム コマンドライン エクスペリエンスです。 | **Windows</br>macOS</br>Linux** |
|[**mssql-conf**](../linux/sql-server-linux-configure-mssql-conf.md) | **mssql-conf** を使うと、Linux 上で実行される SQL Server を構成できます。 | **Linux** |

## <a name="migration-and-other-tools"></a>移行とその他のツール

これらのツールは、SQL Database の移行、構成、およびその他の機能の提供に使用されます。

| ツール | 説明 |
|:--|:--|
| **[構成マネージャー](../tools/configuration-manager/sql-server-configuration-manager-help.md)** | SQL Server 構成マネージャーを使用して、SQL Server サービスを構成し、ネットワーク接続を構成します。 Windows 上での構成マネージャーの実行|
| **[SQL Server Migration Assistant](../ssma/sql-server-migration-assistant.md)** | SQL Server Migration Assistant を使用して、Microsoft Access、DB2、MySQL、Oracle、Sybase から SQL Server へのデータベースの移行を自動化します。|
| **[Database Experimentation Assistant](../dea/database-experimentation-assistant-overview.md)** | Database Experimentation Assistant を使用して、特定のワークロードの対象となる SQL のバージョンを評価します。 |
| **[分散再生](../tools/distributed-replay/install-distributed-replay-overview.md)** | 分散再生機能を使用すると、今後の SQL Server アップグレードの影響を評価するために役立ちます。 また、分散再生を使用して、ハードウェアとオペレーティング システムのアップグレード、および SQL Server のチューニングの影響を評価することもできます。 |
| **[ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)** | ssbdiagnose ユーティリティからは、Service Broker のメッセージ好感や Service Broker サービスの構成の問題が報告されます。 |

このページに記載されていないその他のツールについては、「[SQL コマンド プロンプト ユーティリティ](command-prompt-utility-reference-database-engine.md)」を参照してください。