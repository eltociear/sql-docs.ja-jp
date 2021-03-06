---
title: データベース ミラーリングの前提条件、制限事項、推奨事項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- partners [SQL Server]
- database mirroring [SQL Server], prerequisites
- database mirroring [SQL Server], recommendations
- database mirroring [SQL Server], restrictions
- database mirroring [SQL Server], planning
- database mirroring [SQL Server], about database mirroring
ms.assetid: fdcf2251-9895-44c6-b81e-768fef32e732
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9763385093db6e649e60ab7a6be74f8f28466e1d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62754600"
---
# <a name="prerequisites-restrictions-and-recommendations-for-database-mirroring"></a>データベース ミラーリングの前提条件、制限事項、および推奨事項
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]を使用してください。  
  
 このトピックでは、データベース ミラーリングを設定するための前提条件と推奨事項について説明します。 データベース ミラーリングの概要については、「 [データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md)のインスタンスをホストするフェールオーバー クラスター インスタンスとして構成されます。  
  
> [!NOTE]  
>  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のディスク上ストレージ形式は、64 ビット環境でも 32 ビット環境でも同じです。 このため、データベース ミラーリング セッションでは、32 ビット環境で実行されているサーバー インスタンスと 64 ビット環境で実行されているサーバー インスタンスを組み合わせることができます。  
  

  
##  <a name="DbmSupport"></a>データベースミラーリングのサポート  
 
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でのデータベース ミラーリングのサポートについては、「[SQL Server 2014 の各エディションでサポートされる機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。  
  
 データベース ミラーリングは、サポートされているすべてのデータベース互換性レベルで動作します。 サポートされている互換性レベルについては、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)」を参照してください。  
  

  
##  <a name="Prerequisites"></a> 前提条件  
  
-   ミラーリング セッションを確立するには、パートナーとミラーリング監視サーバー (存在する場合) が、同じバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で実行されている必要があります。  
  
-   2 つのパートナー (プリンシパル サーバーとミラー サーバー) で同じエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行されている必要があります。 ミラーリング監視サーバー (存在する場合) は、データベース ミラーリングをサポートする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで実行できます。  
  
    > [!NOTE]  
    >  ミラーリング セッションでのパートナーであるサーバー インスタンスを、より新しいバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にアップグレードできます。 詳しくは、「 [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](upgrading-mirrored-instances.md)」をご覧ください。  
  
-   このデータベースは、完全復旧モデルを使用する必要があります。 単純復旧モデルと一括ログ復旧モデルでは、データベース ミラーリングがサポートされていません。 そのため、ミラー化されたデータベースでは、常に一括操作が完全にログに記録されます。 復旧モデルについては、「[復旧モデル &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)」を参照してください。  
  
-   ミラー サーバーにミラー データベースを保持するだけの十分なディスク領域があることを確認します。  
  
    > [!NOTE]  
    >  レプリケートされるデータベースでのデータベース ミラーリングの使用方法の詳細については、「[データベース ミラーリングとレプリケーション &#40;SQL Server&#41;](database-mirroring-and-replication-sql-server.md)」を参照してください。  
  
-   ミラー サーバーにミラー データベースを作成する際は、同じデータベース名と WITH NORECOVERY オプションを指定して、プリンシパル データベースのバックアップを復元する必要があります。 また、このバックアップが実行された後で作成されたすべてのログ バックアップについても、WITH NORECOVERY を指定して適用する必要があります。  
  
    > [!IMPORTANT]  
    >  データベース ミラーリングが停止している場合は、データベース ミラーリングを再開する前に、停止中にプリンシパル データベースで作成されたすべてのログ バックアップをミラー データベースに適用する必要があります。  
  

  
##  <a name="Restrictions"></a>おける  
  
-   ミラー化できるのはユーザー データベースのみです。 
  **master**、 **msdb**、 **tempdb**、または **model** の各データベースはミラー化できません。  
  
-   データベース ミラーリング セッション中に、ミラー化されるデータベースの名前を変更することはできません。  
  
-   データベース ミラーリングは FILESTREAM をサポートしていません。 プリンシパル サーバー上に FILESTREAM ファイル グループを作成することはできません。 FILESTREAM ファイル グループを含むデータベースに対してデータベース ミラーリングを構成することはできません。  
  
-   32 ビット システムの場合、データベース ミラーリングでは、各データベース ミラーリング セッションで使用されるワーカー スレッド数の関係で、サーバー インスタンスあたり最大約 10 個のデータベースをサポートできます。  
  
-   複数のデータベースにまたがるトランザクションまたは分散トランザクションでは、データベース ミラーリングがサポートされません。 詳細については、「[データベース ミラーリングまたは AlwaysOn 可用性グループではサポートされない複数データベースにまたがるトランザクション &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)」を参照してください。  
  

  
##  <a name="RecommendationsForPartners"></a>パートナーサーバーの構成に関する推奨事項  
  
-   パートナーは、同じ量のワークロードを処理できる同等のシステムで実行する必要があります。  
  
    > [!NOTE]  
    >  自動フェールオーバーを伴う高い安全性モードを使用する場合は、各フェールオーバー パートナーの通常の負荷が CPU の 50% 未満である必要があります。 ワークロードによって CPU が過負荷になると、フェールオーバー パートナーがミラーリング セッションで他のサーバー インスタンスに ping を実行できなくなる場合があります。 これにより、不必要なフェールオーバーが発生します。 CPU 使用率を 50% 未満に維持できない場合は、自動フェールオーバーを伴わない高い安全性モードか、高パフォーマンス モードを使用することを推奨しています。  
  
-   可能であれば、ミラー データベースのパス (ドライブ文字を含む) を、プリンシパル データベースと同一のパスにします。 ファイル レイアウトが異なる場合は、RESTORE ステートメントに MOVE オプションを含める必要があります。 プリンシパル データベースがドライブ 'F:' 上にあっても、ミラー システムには F: ドライブがない場合などがあります。  
  
    > [!IMPORTANT]  
    >  ミラー データベースの作成時にデータベース ファイルを移動した場合、そのミラー データベースに後でファイルを追加する際に、ミラーリングの中断が必要になる場合があります。  
  
-   ミラーリング セッションのすべてのサーバー インスタンスが同じマスター コード ページと照合順序を使用する必要があります。 異なるマスター コード ページと照合順序を使用すると、ミラーリングの設定中にエラーが発生する可能性があります。  
  
-   必要に応じて、データベースのフェールオーバーにかかる時間を見積もり、必要なパフォーマンスを実現できるようにシステムを構成します。 詳しくは、「 [役割の交代中に発生するサービスの中断時間の算出 &#40;データベース ミラーリング&#41;](estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)という処理により、一般的にプリンシパルとミラーの役割を相互交換できます。  
  
-   最適なパフォーマンスを得るには、ミラーリングに専用のネットワーク アダプター (ネットワーク インターフェイス カード) を使用します。  
  
-   高い安全性モードでデータベース ミラーリングを行う場合、ワイドエリア ネットワーク (WAN) の信頼性が十分かどうかに関する推奨事項はありません。 高い安全性モードで WAN 経由のデータベース ミラーリングを使用する場合、不要なフェールオーバーが自動的に行われる可能性があるため、セッションにミラーリング監視サーバーを追加する方法には注意してください。 詳細については、このトピックの「 [データベース ミラーリングの配置に関する推奨事項](#RecommendationsForDeploying)」を参照してください。  
  

  
##  <a name="RecommendationsForDeploying"></a>データベースミラーリングの配置に関する推奨事項  
 データベース ミラーリングのパフォーマンスを最適化するには、非同期動作を使用する必要があります。 同期動作を使用するミラーリング セッションは、ワークロードが大量のトランザクション ログ データを生成するときに、パフォーマンスが低下する可能性があります。  
  
 テスト環境ですべての動作モードを調査し、データベース ミラーリングのパフォーマンスを評価することをお勧めします。 ただし、ミラーリングを運用環境に配置する前に、実際のネットワークの性能を理解することが必要です。  
  
 自動フェールオーバーを伴う高い安全性モードは、ネットワーク障害が発生する可能性を最小限に抑える、専用接続または非常に単純なネットワーク構成を備えた高サービス ネットワーク用に設計されています。 自動フェールオーバーを伴う高い安全性モードにはこのような質の高いネットワーク環境が不可欠であり、すべてのデータベース ミラーリング セッションに推奨されます。 ただし、高パフォーマンス モードと自動フェールオーバーを伴わない高い安全性モードは、ネットワークの信頼性による影響をそれほど受けません。  
  
 したがって、実稼働環境では、以下の配置ガイドラインに従うことをお勧めします。  
  
1.  非同期の高パフォーマンス モードで実行を開始します。 このモードは、ネットワーク環境の影響を受けることが最も少なく、ミラーリングの動作を調べるには最善の構成です。 帯域幅がミラーリングをサポートすることに確信が持て、ミラーリングの設定および環境における非同期モードのパフォーマンスについて理解できるまでは、システムを非同期で実行することをお勧めします。 詳しくは、「 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)」をご覧ください。  
  
    > [!IMPORTANT]  
    >  テストの期間をとおして、データベース ミラーリングの障害の原因となるネットワーク エラーをセッションで監視することをお勧めします。 障害の潜在的な原因の詳細については、「 [Possible Failures During Database Mirroring](possible-failures-during-database-mirroring.md)」を参照してください。 データベース ミラーリングの監視方法については、「[データベース ミラーリングの監視 &#40;SQL Server&#41;](monitoring-database-mirroring-sql-server.md)」を参照してください。  
  
2.  非同期動作がビジネス ニーズを満たすことが確信できたなら、同期動作を実行してデータ保護の強化を図ることができます。 自分の環境で同期ミラーリングがどのように動作するのかをテストするときは、最初に自動フェールオーバーを伴わない高い安全性モードをテストすることをお勧めします。 このテストの主な目的は、同期操作がデータベースのパフォーマンスに与える影響を確認することです。 詳しくは、「 [Database Mirroring Operating Modes](database-mirroring-operating-modes.md)」をご覧ください。  
  
3.  自動フェールオーバーを伴わない高い安全性モードがビジネス ニーズを満たしていること、およびネットワーク エラーによって障害が発生しないことを確認できるまで、自動フェールオーバーは有効にしないでください。 詳細については、「[データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)」を参照してください。  
  

  
## <a name="see-also"></a>参照  
 [データベースミラーリングの設定 &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md)   
 [データベースミラーリングと AlwaysOn 可用性グループ &#40;SQL Server のトランスポートセキュリティ&#41;](transport-security-database-mirroring-always-on-availability.md)   
 [データベースミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [データベースミラーリング構成 &#40;SQL Server のトラブルシューティング&#41;](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
