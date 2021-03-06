---
title: レポートのプレビュー
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 21928cd6637815000983e8a0fe05aa4e77d1c216
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67412970"
---
# <a name="preview-reports-in-sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS) でレポートをプレビューする

  レポートをデザインするときに、そのレポートを実稼働環境にパブリッシュする前に表示することができます。 これを行うには、レポート デザイナーでプレビュー モードに切り替えるか、レポート デザイナーのプレビュー ウィンドウを使用するか、テスト環境のレポート サーバーにレポートをパブリッシュします。  
  
> [!NOTE]  
> レポートをプレビューすると、レポートのデータがローカル コンピューターのファイルにキャッシュされます。 同じレポートを、同じクエリ、パラメーター、および資格情報を使用して再びプレビューすると、レポート デザイナーはクエリを再実行する代わりにキャッシュされたコピーを表示します。 データファイルは、レポート定義ファイルと同じディレクトリに* \<reportname>* として保存されます。 レポート デザイナーを終了してもファイルは削除されません。  
  
## <a name="preview-mode"></a>プレビュー モード

 [**プレビュー**] をクリックすると、レポートデザイナーでレポートをプレビューできます。 この場合、レポート サーバーで提供されるものと同じレポート処理および表示機能を使用して、レポートがローカルで実行されます。 表示されるレポートは対話型のイメージです。ユーザーは、パラメーターの選択、リンクのクリック、ドキュメント マップの表示、レポートの非表示部分の展開と折りたたみなどを行うことができます。 また、インストールされている任意の表示形式にレポートをエクスポートできます。  
  
## <a name="standalone-preview"></a>スタンドアロン プレビュー

 レポートをプレビューするもう 1 つの方法は、作成したカスタム アセンブリをデバッグする際などに、デバッグ構成でレポート プロジェクトを実行することです。 プロジェクトの実行方法には、次の 3 とおりがあります。  
  
- [**デバッグ**] メニューの [**開始**] をクリックします。  
  
- [ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]標準] ツールバーの [**開始**] ボタンをクリックします。  
  
- F5 キーを押す。  
  
 レポートを作成しても配置しないプロジェクト構成を使用している場合は、現在の構成の `StartItem` プロパティで指定されたレポートが、別のプレビュー ウィンドウで開きます。 プレビュー ウィンドウは、プレビュー モードと同じ方法でレポートを表示し、同じ機能を提供します。  
  
> [!NOTE]  
> レポートをデバッグする前に、開始アイテムを設定する必要があります。 開始項目を設定するには、ソリューションエクスプローラーでレポートプロジェクトを右クリックし、[**プロパティ**] をクリック`StartItem`します。次に、で、表示するレポートの名前を選択します。  
  
 プロジェクトの開始アイテムではない特定のレポートをプレビューする場合は、レポートを作成しても配置しない構成 (DebugLocal 構成など) を選択し、レポートを右クリックして、 **[実行]** をクリックします。 レポートを配置しない構成を選択する必要があります。そうしないと、レポートはローカルのプレビュー ウィンドウに表示されずに、レポート サーバーにパブリッシュされます。  
  
## <a name="print-preview"></a>印刷プレビュー

 プレビュー モードまたはプレビュー ウィンドウに最初に表示されるレポートは、HTML 表示拡張機能によって生成されるレポートと似ています。 プレビューは HTML 形式ではありませんが、レポートのレイアウトおよび改ページは HTML 出力と似ています。  
  
 印刷プレビュー モードに切り替えることによって、表示を変更し、印刷されるレポートを表示できます。 プレビュー ツール バーの **[印刷プレビュー]** ボタンをクリックします。 レポートは、実際のページに近い状態で表示されます。 この表示は、画像表示拡張機能および PDF 表示拡張機能によって生成される出力と似ています。 印刷プレビューは画像または PDF ファイルではありませんが、レポートのレイアウトおよびページ割り当ては、それらの形式での出力と似ています。  
  
## <a name="publish-to-a-test-server"></a>テスト サーバーにパブリッシュする

 レポートのテストは、テスト サーバーにレポートをパブリッシュして行うこともできます。 テスト サーバーにレポートをパブリッシュする操作は、実稼働サーバーにレポートをパブリッシュする場合と同じです。 レポートのパブリッシュ方法の詳細については、「 [レポート サーバーへのレポートのパブリッシュ](publishing-reports-to-a-report-server.md)」を参照してください。  
  
## <a name="next-steps"></a>次のステップ

 - [レポートの印刷 &#40;レポート ビルダーおよび SSRS&#41;](../report-builder/print-reports-report-builder-and-ssrs.md)
 - [レポートの印刷 (レポート ビルダーおよび SSRS)](../report-builder/print-a-report-report-builder-and-ssrs.md)
 - [レポートのパブリッシュ](../publish-reports.md)
 - [レポートでのカスタム アセンブリの使用](../custom-assemblies/using-custom-assemblies-with-reports.md)