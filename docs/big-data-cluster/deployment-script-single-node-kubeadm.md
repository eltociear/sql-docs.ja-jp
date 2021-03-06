---
title: 単一ノード kubeadm クラスターの展開
titleSuffix: SQL Server Big Data Clusters
description: bash 展開スクリプトを使用して、[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] を単一ノード kubeadm クラスターに展開します。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f60256e58339387323f923c85d2b880459455663
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75252099"
---
# <a name="deploy-with-a-bash-script-to-a-single-node-kubeadm-cluster"></a>bash スクリプトを使用して単一ノード kubeadm クラスターに展開する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このチュートリアルでは、サンプルの bash 展開スクリプトを利用し、kubeadm と SQL Server ビッグ データ クラスターを使用して単一ノード Kubernetes クラスターを展開します。

## <a name="prerequisites"></a>前提条件

- バニラ Ubuntu 18.04 または 16.04 **サーバー**の仮想マシンまたは物理マシン。 スクリプトによってすべての依存関係が設定され、VM 内からそのスクリプトを実行します。

  > [!NOTE]
  > Azure Linux VM の使用は、まだサポートされていません。

- VM には、少なくとも 8 個の CPU、64 GB の RAM、および 100 GB のディスク領域が必要です。 すべてのビッグ データ クラスターの Docker イメージをプルした後は、すべてのコンポーネント全体で使用するデータとログに対して 50 GB が残されます。

- 次のコマンドを使用して既存のパッケージを更新し、OS イメージが最新の状態になっていることを確認します。

   ``` bash
   sudo apt update && sudo apt upgrade -y
   sudo systemctl reboot
   ```

## <a name="recommended-virtual-machine-settings"></a>推奨される仮想マシン設定

1. 仮想マシンに静的メモリ構成を使用します。 たとえば、Hyper-V のインストールでは動的メモリ割り当ては使用せず、代わりに推奨される 64 GB 以上を割り当てます。

1. 仮想マシンをクリーンな状態にロールバックできるように、ハイパーバイザーでチェックポイントまたはスナップショット機能を使用します。


## <a name="instructions-to-deploy-sql-server-big-data-cluster"></a>SQL Server ビッグ データ クラスターを展開する手順

1. 展開に使用することを計画している VM 上にスクリプトをダウンロードします。

   ```bash
   curl --output setup-bdc.sh https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/setup-bdc.sh
   ```

2. 次のコマンドを使用して、スクリプトを実行可能にします。

   ```bash
   chmod +x setup-bdc.sh
   ```

3. スクリプトを実行します (必ず *sudo* を使用して実行してください)。

   ```bash
   sudo ./setup-bdc.sh
   ```

   要求された場合は、次の外部エンドポイント、つまり、コントローラー、SQL Server マスター、ゲートウェイに使用するパスワードの入力値を指定します。 パスワードは、SQL Server パスワードの既存の規則に基づいて、十分に複雑なものにする必要があります。 コントローラーのユーザー名の既定値は、*admin* です。

4. **azdata** ツールに対して別名を設定します。

   ```bash
   source ~/.bashrc
   ```

5. azdata のエイリアス セットアップを更新します。

   ```bash
   azdata --version
   ```

## <a name="cleanup"></a>クリーンアップ

[cleanup-bdc.sh](https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/cleanup-bdc.sh) スクリプトは、必要に応じて環境をリセットするために便利な方法として提供されています。 ただし、テスト目的では仮想マシンを使用し、仮想マシンをクリーンな状態にロールバックするためにハイパーバイザーでスナップショット機能を使用することをお勧めします。

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターの使用を開始するには、「[Tutorial:Load sample data into a SQL Server big data cluster](tutorial-load-sample-data.md)」(チュートリアル: SQL Server ビッグ データ クラスターにサンプル データを読み込む) を参照してください。
