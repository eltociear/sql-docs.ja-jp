---
title: SQL Server のレプリケーション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], about
- replication [SQL Server]
ms.assetid: 3a5f4592-3c61-4b4d-9ceb-39716aeeba41
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: be03754ea8eeb61d838357667da6e37e1be6bc31
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62626154"
---
# <a name="sql-server-replication"></a>SQL Server のレプリケーション
  レプリケーションとは、あるデータベースから別のデータベースにデータやデータベース オブジェクトをコピーおよび配布し、それらのデータベースを同期させて一貫性を保つための一連のテクノロジです。 レプリケーションを使用すると、ローカル エリア ネットワーク、ワイド エリア ネットワーク、ダイヤルアップ接続、ワイヤレス接続、インターネットなどを経由して、別の場所や、リモート ユーザーまたはモバイル ユーザーにデータを配布することができます。  
  
 トランザクション レプリケーションは、高いスループットが必要とされるサーバー間のシナリオで使用されるのが一般的です。たとえば、スケーラビリティと可用性の向上、データ ウェアハウジングとレポート、複数サイトからのデータの統合、異種データの統合、バッチ処理のオフロードなどのシナリオで使用されます。 マージ レプリケーションは、データの競合の可能性があるモバイル アプリケーションや分散サーバー アプリケーションを主な対象としています。 モバイル ユーザーとのデータ交換、店舗販売時点管理 (POS) アプリケーション、複数サイトからのデータの統合などのシナリオが一般的です。 スナップショット レプリケーションは、トランザクション レプリケーションとマージ レプリケーションに初期データセットを提供するために使用されます。データの完全な更新が必要な場合にも使用できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この 3 種類のレプリケーションにより、企業全体のデータの同期のための強力かつ柔軟なシステムが提供されます。 SQLCE 3.5 および SQLCE 4.0 に対するレプリケーションは [!INCLUDE[win8srv](../../includes/win8srv-md.md)] と [!INCLUDE[win8](../../includes/win8-md.md)]の両方でサポートされます。  
  
 レプリケーションの代替手段として、Microsoft Sync Framework を使用してデータベースを同期できます。 Sync Framework には、SQL Server、SQL Server Express、SQL Server Compact、および SQL Azure の各データベース間での同期を容易にするコンポーネントと、直感的かつ柔軟性の高い API が含まれています。 また、Sync Framework には、SQL Server データベースと、ADO.NET と互換性があるその他のデータベースとの間で同期を行うために使用できるクラスもあります。 Sync Framework のデータベース同期コンポーネントの詳細については、「 [データベースの同期](https://go.microsoft.com/fwlink/?LinkId=209079)」を参照してください。 Sync Framework の概要の詳細については、「 [Microsoft Sync Framework デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=209078)」を参照してください。 Sync Framework とマージ レプリケーションとの比較の詳細については、データベースの同期の「 [概要とシナリオ](https://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)」を参照してください。  
  

## <a name="whats-new"></a>新機能 
- SQL Server 2017 では、SQL Server のレプリケーションに重要な新機能は加えられていません。 
- SQL Server 2016 では、SQL Server のレプリケーションに重要な新機能は加えられていません。 

下位互換性の情報については、「[レプリケーションの旧バージョンとの互換性](replication-backward-compatibility.md)」を参照してください。 


 ## <a name="replication-security"></a>レプリケーションのセキュリティ
  
-   [レプリケーションのセキュリティ設定を表示および変更する](security/view-and-modify-replication-security-settings.md)  
-   [パブリケーション アクセス リストのログインの管理](security/manage-logins-in-the-publication-access-list.md)  
  
## <a name="publishing-and-distribution"></a>パブリッシングおよびディストリビューション  
  
-   [パブリッシングおよびディストリビューションの構成](configure-publishing-and-distribution.md)   
-   [パブリケーションのプロパティの表示および変更](publish/view-and-modify-publication-properties.md)   
-   [パブリッシングおよびディストリビューションの無効化](disable-publishing-and-distribution.md)  
  
## <a name="publications-and-articles"></a>パブリケーションおよびアーティクル 
  
-   [パブリケーションを作成する](publish/create-a-publication.md)    
-   [アーティクルの定義](publish/define-an-article.md)   
-   [パブリケーションのプロパティの表示および変更](publish/view-and-modify-publication-properties.md)   
-   [アーティクルのプロパティの表示および変更](publish/view-and-modify-article-properties.md)    
-   [パブリケーションを削除する](publish/delete-a-publication.md)   
-   [アーティクルの削除](publish/delete-an-article.md)    
-   [Oracle Database からのパブリケーションの作成](publish/create-a-publication-from-an-oracle-database.md)   
-   [サブスクリプションの有効期限を設定する](publish/set-the-expiration-period-for-subscriptions.md)  
-   [スキーマオプションの指定](publish/specify-schema-options.md)  
-   [スキーマ変更のレプリケート](publish/replicate-schema-changes.md)    
-   [Id 列の管理](publish/manage-identity-columns.md)   
-   [マージ パブリケーションの互換性レベルの設定](publish/set-the-compatibility-level-for-merge-publications.md)  
  
### <a name="snapshot-options"></a>スナップショット オプション  
  
-   [スナップショットのプロパティの構成](publish/configure-snapshot-properties-replication-transact-sql-programming.md)    
-   [FTP を使用してスナップショットを配信する](publish/deliver-a-snapshot-through-ftp.md) 
  
### <a name="filter-data"></a>データのフィルター選択  
  
-   [列フィルターの定義および変更](publish/define-and-modify-a-column-filter.md)    
-   [静的行フィルターを定義および変更する](publish/define-and-modify-a-static-row-filter.md)    
-   [マージアーティクルのパラメーター化された行フィルターを定義および変更する](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)    
-   [パラメーター化された行フィルターの最適化](publish/optimize-parameterized-row-filters.md)    
-   [マージアーティクル間の結合フィルターを定義および変更する](publish/define-and-modify-a-join-filter-between-merge-articles.md)  
  
### <a name="transactional-replication-options"></a>トランザクション レプリケーション オプション  
  
-   [データの変更をトランザクション アーティクルに反映する方法の設定](publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)    
-   [トランザクション パブリケーションの更新可能なサブスクリプションの有効化](publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
### <a name="merge-replication-options"></a>マージ レプリケーション オプション  
  
-   [マージテーブルアーティクル間に論理レコードリレーションシップを定義する](publish/define-a-logical-record-relationship-between-merge-table-articles.md)    
-   [マージレプリケーションのプロパティの指定](publish/specify-merge-replication-properties.md)    
-   [マージ アーティクル競合回避モジュールの指定](publish/specify-a-merge-article-resolver.md)    

  
## <a name="manage-subscriptions"></a>サブスクリプションを管理する  
  
-   [プル サブスクリプションの作成](create-a-pull-subscription.md)    
-   [プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md)    
-   [プル サブスクリプションの削除](delete-a-pull-subscription.md)    
-   [プッシュ サブスクリプションの作成](create-a-push-subscription.md)   
-   [プッシュ サブスクリプションのプロパティの表示または変更](view-and-modify-push-subscription-properties.md)   
-   [プッシュ サブスクリプションの削除](delete-a-push-subscription.md)   
-   [同期スケジュールの指定](specify-synchronization-schedules.md)    
-   [トランザクションパブリケーションに対する更新可能なサブスクリプションの作成](publish/create-an-updatable-subscription-to-a-transactional-publication.md)  
-   [SQL Server 以外のサブスクライバーのサブスクリプションの作成](create-a-subscription-for-a-non-sql-server-subscriber.md)  
  
## <a name="synchronize-subscriptions"></a>サブスクリプションの同期  
  
-   [初期スナップショットを作成して適用する](create-and-apply-the-initial-snapshot.md)   
-   [パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)    
-   [バックアップからのトランザクション サブスクリプションの初期化](initialize-a-transactional-subscription-from-a-backup.md)    
-   [サブスクリプションを手動で初期化する](initialize-a-subscription-manually.md)    
-   [プルサブスクリプションの同期](synchronize-a-pull-subscription.md)    
-   [プッシュサブスクリプションの同期](synchronize-a-push-subscription.md)   
-   [サブスクリプションの再初期化](reinitialize-a-subscription.md)    
-   [同期中のスクリプトの実行](execute-scripts-during-synchronization-replication-transact-sql-programming.md)    
-   [マージアーティクルのビジネスロジックハンドラーの実装](implement-a-business-logic-handler-for-a-merge-article.md)  
-   [ビジネスロジックハンドラーのデバッグ &#40;レプリケーションプログラミング&#41;](debug-a-business-logic-handler-replication-programming.md)    
-   [同期中にトリガーと制約の動作を制御する](control-behavior-of-triggers-and-constraints-in-synchronization.md)    
-   [マージアーティクルのカスタム競合回避モジュールの実装](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="administeration"></a>このように 
  
-   [レプリケーション エージェント プロファイルを操作する](agents/work-with-replication-agent-profiles.md)   
-   [サブスクライバーでのデータの検証](validate-data-at-the-subscriber.md)    
-   [パラメーター化されたフィルターを使用してマージパブリケーションのパーティションを管理する](publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)    
-   [マージ パブリケーションでのテーブルへのデータの一括読み込み](bulk-load-data-into-tables-in-a-merge-publication.md)    
-   [マージメタデータのクリーンアップ](administration/clean-up-merge-metadata-replication-transact-sql-programming.md)    
-   [マージアーティクルのダミー更新の実行](administration/perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming.md)    
-   [ディストリビューションデータベース内のレプリケートされたコマンドおよびその他の情報を表示する](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [トランザクション レプリケーションの連携バックアップの有効化](administration/enable-coordinated-backups-for-transactional-replication.md)   
-   [ピアツーピアトポロジの管理](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)    
-   [レプリケーショントポロジの停止](administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)    
-   [Oracle パブリッシャー用のトランザクション セット ジョブの構成](administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
-   [レプリケーションスクリプトのアップグレード](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)  
  
## <a name="monitor"></a>モニター
  
-   [管理者以外のユーザーがレプリケーション モニターを使用できるようにする](monitor/allow-non-administrators-to-use-replication-monitor.md)    
-   [プログラムによるレプリケーションの監視](monitor/programmatically-monitor-replication.md)    
-   [ディストリビューションデータベース内のレプリケートされたコマンドおよびその他の情報を表示する](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [マージ パブリケーションの競合情報の表示](view-conflict-information-for-merge-publications.md) 
-   [トランザクションレプリケーションの待機時間を計測して接続を検証する](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  