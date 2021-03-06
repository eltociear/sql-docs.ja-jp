---
title: テーブル、マトリックス、または一覧の追加、移動、または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 4b97c470-cde0-4bb1-a46e-5f5f5553feaa
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7239efa5a2d64b3751fde34d7cd1e676ea905dd4
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "65581996"
---
# <a name="add-move-or-delete-a-table-matrix-or-list-report-builder-and-ssrs"></a>テーブル、マトリックス、または一覧の追加、移動、または削除 (レポート ビルダーおよび SSRS)
  [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] の改ページ調整されたレポートのデータ領域には、レポート データセットのデータが表示されます。 またデータ領域には、テーブル、マトリックス、一覧、グラフ、およびゲージが含まれます。 1 つのデータ領域を別のデータ領域内に入れ子にするには、各データ領域を個別に追加し、子データ領域を親データ領域にドラッグします。  
  
 テーブルまたはマトリックス データ領域をレポートに追加するには、テーブルまたはマトリックスの新規作成ウィザードを実行するのが最も簡単な方法です。 これらのウィザードを使用すると、データ ソースへの接続の選択、フィールドの配置、およびレイアウトとスタイルの選択の手順を段階的に実行できます。 ウィザードは、レポート ビルダーでのみ利用可能です。  
  
## <a name="to-add-a-table-or-matrix-to-a-report-by-using-the-new-table-or-new-matrix-wizard"></a>テーブルまたはマトリックスの新規作成ウィザードを使用してレポートにテーブルまたはマトリックスを追加するには  
  
1.  **[挿入]** タブの **[テーブル]** または **[マトリックス]** をクリックし、次に **[テーブル ウィザード]** または **[マトリックス ウィザード]** をクリックします。  
  
2.  **[新しいテーブル]** または **[マトリックスの新規作成]** ウィザードの手順に従って操作します。  
  
3.  **[ホーム]** タブで **[実行]** をクリックして、表示されたレポートを確認します。  
  
4.  レポートの作業を続行するには、 **[実行]** タブで **[デザイン]** をクリックします。  
  
## <a name="to-add-a-data-region"></a>データ領域を追加するには  
  
1.  **[データ領域]** グループの **[リボン]** で、追加するデータ領域をクリックします。  
  
2.  デザイン画面をクリックし、次にマウスをドラッグして、必要なサイズのデータ領域のボックスを作成します。  
  
3.  レポート データ ペインからレポート データセット フィールドをデータ領域セルにドラッグします。 ここで、データ領域はレポート データセットのデータにバインドされます。  
  
## <a name="to-select-a-data-region"></a>データ領域を選択するには  
  
-   Tablix データ領域では、コーナー ハンドルを右クリックします。 グラフ データ領域またはゲージ データ領域では、データ領域内をクリックします。  
  
     1 つの選択ハンドルと 8 つのサイズ変更ハンドルが表示されます。  
  
     入れ子になったデータ領域では、領域内を右クリックし、 **[選択]** をクリックして、目的のレポート アイテムを選択します。 どのレポート アイテムが選択されているかを確認するには、プロパティ ペインを使用します。 デザイン画面で選択したアイテムの名前が、プロパティ ペインのツール バーに表示されます。  
  
## <a name="to-move-a-data-region"></a>データ領域を移動するには  
  
-   データ領域を移動するには、データ領域の選択ハンドルをクリックしてドラッグします。 既存のレポート アイテムと揃えるには、スナップ線を使用します。  
  
     ルーラーが表示されていない場合は、[表示] タブをクリックして **[ルーラー]** をクリックします。  
  
     また方向キーを使用して、デザイン画面で選択しているデータ領域を移動することもできます。  
  
## <a name="to-delete-a-data-region"></a>データ領域を削除するには  
  
-   データ領域を選択し、領域内を右クリックして **[削除]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
