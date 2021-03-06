---
title: 可用性レプリカのプロパティの表示 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- ', policies'
ms.assetid: 14fed3c4-8ecc-4e1c-931d-a7ec1e9f9e90
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a1ca87fc977ee97900be9e821cab4918064c7a44
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62788008"
---
# <a name="view-availability-replica-properties-sql-server"></a>可用性レプリカのプロパティの表示 (SQL Server)
  このトピックでは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] で [!INCLUDE[tsql](../../../includes/tsql-md.md)] または [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] を使用して、AlwaysOn 可用性グループの可用性レプリカのプロパティを表示する方法について説明します。  
  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **可用性レプリカのプロパティを表示および変更するには**  
  
1.  オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー ツリーを展開します。  
  
2.  
  **[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。  
  
3.  可用性レプリカが属する可用性グループを展開し、[ **可用性レプリカ** ] ノードを展開します。  
  
4.  プロパティを表示する可用性レプリカを右クリックし、[ **プロパティ** ] をクリックします。  
  
5.  [ **可用性レプリカ プロパティ** ] ダイアログ ボックスで、[ **全般** ] ページを使用して、このレプリカのプロパティを表示します。 プライマリ レプリカに接続している場合に変更できるプロパティは、可用性モード、フェールオーバー モード、プライマリ ロールの接続アクセス、セカンダリ ロールの読み取りアクセス (読み取り可能なセカンダリ)、およびセッション タイムアウトの値です。 詳細については、「[可用性レプリカのプロパティ &#40;全般ページ&#41;](availability-replica-properties-general-page.md)」を参照してください。  
  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **可用性レプリカのプロパティと状態を表示するには**  
  
 可用性レプリカのプロパティおよび状態を表示するには、次のビューとシステム関数を使用します。  
  
 [sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のローカル インスタンスが可用性レプリカをホストしている各可用性グループ内の可用性レプリカごとに 1 行のデータを返します。  
  
 **列の名前:** replica_id、group_id、replica_metadata_id、replica_server_name、owner_sid、endpoint_url、availability_mode、availability_mode_desc、failover_mode、failover_mode_desc、session_timeout、primary_role_allow_connections、primary_role_allow_connections_desc、secondary_role_allow_connections、secondary_role_allow_connections_desc です。  
  
 [sys.availability_read_only_routing_lists](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
 WSFC フェールオーバー クラスター内の AlwaysOn 可用性グループにある各可用性レプリカの読み取り専用ルーティング リストに対する行を返します。  
  
 **列名:** replica_id、routing_priority、read_only_replica_id  
  
 [可用性レプリカの監視](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
 Windows Server フェールオーバー クラスタリング (WSFC) クラスター内の AlwaysOn 可用性グループの可用性レプリカ (結合状態に関係なく) ごとに 1 行のデータを返します。  
  
 **列名:** group_name、replica_server_name、node_name  
  
 [sys.dm_hadr_availability_replica_cluster_nodes](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
 Windows Server フェールオーバー クラスタリング (WSFC) クラスター内のすべての AlwaysOn 可用性グループ (レプリカの場所に関係なく) のレプリカ (結合状態に関係なく) ごとに 1 行のデータを返します。  
  
 **列名:** replica_id、replica_server_name、group_id、join_state、join_state_desc  
  
 [sys.dm_hadr_availability_replica_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
 各ローカル可用性レプリカの状態を示す 1 行のデータと、同じ可用性グループに含まれるリモート可用性グループごとの 1 行のデータを返します。  
  
 **列名:** replica_id、group_id、is_local、ロール、role_desc、operational_state、operational_state_desc、connected_state、connected_state_desc、recovery_health、recovery_health_desc、synchronization_health、および synchronization_health_desc  
  
 [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
 現在のレプリカが推奨されるバックアップ レプリカであるかどうかを判別します。 現在のサーバー インスタンス上のデータベースが推奨されるレプリカの場合は 1 を返します。 それ以外の場合は 0 を返します。  
  
> [!NOTE]  
>  可用性レプリカのパフォーマンス カウンター ( **SQLServer:可用性レプリカ**  パフォーマンス オブジェクト) の詳細については、「 [SQL Server、可用性レプリカ](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)」を参照してください。  
  
  
##  <a name="RelatedTasks"></a> 関連タスク  
 **可用性グループに関する情報を表示するには**  
  
-   [可用性グループのプロパティの表示 &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md)  
  
-   [可用性グループ リスナーのプロパティの表示 &#40;SQL Server&#41;](view-availability-group-listener-properties-sql-server.md)  
  
-   [AlwaysOn 可用性グループ &#40;SQL Server での運用上の問題のための AlwaysOn ポリシー&#41;](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [AlwaysOn ダッシュボード &#40;SQL Server Management Studio を使用&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [Transact-sql&#41;&#40;可用性グループの監視](monitor-availability-groups-transact-sql.md)  
  
 **可用性レプリカを管理するには**  
  
-   [セカンダリレプリカを可用性グループ &#40;SQL Server に追加&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [セカンダリレプリカを可用性グループに参加させる &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [可用性レプリカの可用性モードを変更する &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [可用性レプリカのフェールオーバーモードを変更する &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [可用性レプリカのセッションタイムアウト期間を変更する &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
-   [可用性グループからセカンダリレプリカを削除する &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
 **可用性データベースを管理するには**  
  
-   [可用性グループにデータベースを追加 &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
-   [セカンダリデータベースを可用性グループに参加させる &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [可用性データベース &#40;SQL Server を中断&#41;](suspend-an-availability-database-sql-server.md)  
  
-   [可用性データベース &#40;SQL Server の再開&#41;](resume-an-availability-database-sql-server.md)  
  
-   [可用性グループからセカンダリデータベースを削除する &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [可用性グループからのプライマリデータベースの削除 &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Transact-sql&#41;&#40;可用性グループの監視](monitor-availability-groups-transact-sql.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server での運用上の問題のための AlwaysOn ポリシー&#41;](always-on-policies-for-operational-issues-always-on-availability.md)   
 [可用性グループ &#40;SQL Server の管理&#41;](administration-of-an-availability-group-sql-server.md)  
  
  
