---
title: 制御フロー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- control flow [Integration Services], elements
- SSIS control flow elements
- SQL Server Integration Services control flow elements
ms.assetid: 0cc042a9-1a7f-49ed-9f47-091653d5ef6e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 60aa1e7f4e671540d8ece08a24696a3a46998c82
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62832635"
---
# <a name="control-flow"></a>制御フロー
  パッケージは、制御フローと、オプションで含まれる 1 つ以上のデータ フローから構成されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]には、パッケージ内の構造を提供するコンテナー、機能を提供するタスク、実行可能ファイル、コンテナー、およびタスクを順序付けされた制御フローに接続する優先順位制約の3種類の制御フロー要素が用意されています。  
  
 詳細については、「 [優先順位制約](precedence-constraints.md)」、「 [Integration Services コンテナー](integration-services-containers.md)」、および「 [Integration Services タスク](integration-services-tasks.md)」を参照してください。  
  
 次の図は、1 つのコンテナーと 6 つのタスクで構成される制御フローを示しています。 タスクのうち 5 つはパッケージ レベルで定義され、残りの 1 つのタスクはコンテナー レベルで定義されています。 タスクは、コンテナーの内部にあります。  
  
 ![1 つのコンテナーと 6 つのタスクで構成される制御フロー](../media/ssis-controlflowelmt.gif "1 つのコンテナーと 6 つのタスクで構成される制御フロー")  
  
 
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のアーキテクチャでは入れ子のコンテナーがサポートされており、制御フローには複数のレベルで入れ子になったコンテナーを含めることができます。 たとえば、パッケージには Foreach ループ コンテナーなどのコンテナーを含めることができ、Foreach ループ コンテナーには、さらに別の Foreach ループ コンテナーなどを含めることができます。  
  
 また、イベント ハンドラーにも、同じ種類の制御フローの要素を使用して作成される制御フローが含まれます。  
  
## <a name="control-flow-implementation"></a>制御フローの実装  
 パッケージの制御フローを作成するには、 **デザイナーの** [制御フロー] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] タブを使用します。 
  **[制御フロー]** タブがアクティブになっている場合、ツールボックスには、制御フローに追加できるタスクとコンテナーが表示されます。  
  
 次の図は、制御フロー デザイナーに表示された、簡単なパッケージの制御フローを示しています。 この図で表示されている制御フローは、パッケージレベルの 3 つのタスク、および 3 つのタスクが含まれるパッケージレベルの 1 つのコンテナーで構成されています。 タスクとコンテナーは、優先順位制約を使用して連結されます。  
  
 ![パッケージの制御フロー デザイナーのスクリーンショット](../media/samplecontrolflow.gif "パッケージの制御フロー デザイナーのスクリーンショット")  
  
 制御フローを作成するには、次の作業を行います。  
  
-   パッケージ内で繰り返すワークフローを実装するコンテナー、または制御フローをサブセットに分割するコンテナーを追加します。  
  
-   データ フローのサポート、データの準備、ワークフローとビジネス インテリジェンス機能の実行、およびスクリプトの実装を行うタスクを追加します。  
  
     
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] には、パッケージのビジネス要件を満たす制御フローを作成するための、さまざまなタスクが含まれています。 パッケージでデータを処理する必要がある場合、制御フローには少なくとも 1 つのデータ フロー タスクを含める必要があります。 たとえば、データの抽出、データ値の集計、およびデータ ソースへの結果の書き込みをパッケージで行う必要がある場合などです。  詳細については、「 [Integration Services タスク](integration-services-tasks.md) 」と「 [制御フローのタスクまたはコンテナーを追加または削除する](add-or-delete-a-task-or-a-container-in-a-control-flow.md)」を参照してください。  
  
-   優先順位制約を使用してコンテナーとタスクを連結し、順序付けされた制御フローを作成します。  
  
     
  **[制御フロー]** タブのデザイン画面にタスクまたはコンテナーを追加すると、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーは、アイテムにコネクタを自動的に追加します。 パッケージに 2 つ以上のアイテム、つまりタスクまたはコンテナーが含まれている場合、コネクタを 1 つのアイテムから別のアイテムにドラッグすると、それらを制御フローに結合できます。  
  
     2 つのアイテム間のコネクタは、優先順位制約を表します。 優先順位制約では、連結された 2 つのアイテムの関連性を定義します。 ここでは、実行時にタスクとコンテナーが実行される順序、およびタスクとコンテナーが実行される条件を指定します。 たとえば、優先順位制約は、あるタスクが成功した場合にのみ、制御フロー内の次のタスクが実行されるように指定できます。 詳細については、「 [優先順位制約](precedence-constraints.md)」を参照してください。  
  
-   接続マネージャーを追加します。  
  
     多くのタスクではデータ ソースに接続する必要があるため、タスクに必要な接続マネージャーをパッケージに追加する必要があります。 使用する列挙子の型に応じて、Foreach ループ コンテナーにも接続マネージャーが必要となる場合があります。 接続マネージャーは、制御フローをアイテム別に作成するときに追加できます。または、制御フローの作成を開始する前に追加することもできます。 詳細については、「[Integration Services (SSIS) の接続](../connection-manager/integration-services-ssis-connections.md)」および「[接続マネージャーを作成する](../create-connection-managers.md)」を参照してください。  
  
 また、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーには、デザイン画面を管理したり、制御フローを自己文書化するための、多数のデザイン時機能も含まれています。  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [制御フローのタスクまたはコンテナーを追加または削除する](add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
-   [タスクまたはコンテナーのプロパティを設定する](../set-the-properties-of-a-task-or-container.md)  
  
-   [コンポーネントのグループ化とグループの解除](../group-or-ungroup-components.md)  
  
  
