---
title: Microsoft Surface デバイスと Apple iOS デバイスで Reporting Services レポートを表示する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- iPad
- Safari
- SSRS
- Report Viewer [Reporting Services]
- iOS
ms.assetid: 2124bcf5-d60a-475f-a4ae-de6df44d2860
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3937f227d025da054a28f73fffde4a57dc365c3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098656"
---
# <a name="view-reporting-services-reports-on-microsoft-surface-devices-and--apple-ios-devices"></a>Microsoft Surface デバイスと Apple iOS デバイスでの Reporting Services レポートの表示
  このトピックでは、Microsoft Surface デバイス、Apple iOS 6 と Apple Safari を搭載したデバイス (iPad など) でサポートされる [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の機能とワークフローについて説明します。  
  
## <a name="view-and-interact-with-reports"></a>レポートの表示および操作  
 
  [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]以降の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、Microsoft Surface デバイス、Apple iOS 6 と Apple Safari ブラウザーを搭載したデバイス (iPad など) でのレポートの表示と基本的な対話操作がサポートされます。 Microsoft Surface デバイスを使用してレポートをパブリッシュすることもできます。  
  
 ![IPad デスクトップ](media/videothumbnail.jpg "IPad デスクトップ")  
iPad でレポートを表示する方法の例をご覧ください。  
  
 Windows Phone 8 デバイスで [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポートを表示することもできます。  
  
 ここで説明する機能を使用するには、次のいずれかをインストールします。  
  
-   ネイティブ モードのレポート サーバーの場合は、 [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] 以降のバージョンをインストールします。  
  
     [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]は、 [Microsoft ダウンロードセンター](https://www.microsoft.com/download/details.aspx?id=35575)からダウンロードできます。  
  
-   SharePoint モードのレポート サーバーの場合は、SharePoint 製品用 [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] アドインの [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 以降をインストールします。  
  
 **iPad デバイスまたは Microsoft Surface デバイスでレポートを表示および操作するには**  
  
1.  レポートが存在するレポート サーバーまたは SharePoint サイトに接続できることを確認します。  
  
2.  次のいずれかの手順に従って、レポートを開きます。  
  
    -   **電子メールからの起動:**[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]サブスクリプションによって作成された電子メールから、レポートの URL をタップします。 レポートがブラウザーで開かれます。  
  
    -   **レポートサーバーからの起動:** レポートサーバー上[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]のディレクトリを参照し、レポート名をタップしてレポートを開きます。  
  
    -   **SharePoint ドキュメントライブラリからの起動:** レポートを含む[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint ドキュメントライブラリを参照し、レポート名をタップします。 レポートを表示および操作できます。  
  
        > [!IMPORTANT]  
        >  iPad の場合は、Safari の **[プライベート ブラウズ]** プロパティがオフになっていることを確認します。  
  
    -   **SharePoint web パーツ:** Web パーツが SharePoint ページに追加されている場合は、レポート[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]を表示できます。  
  
3.  Microsoft Surface デバイスでは、レポート マネージャーを使用してレポートを開くこともできます。 
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート マネージャーでディレクトリを参照し、レポート名をタップしてレポートを開きます。  
  
    > [!IMPORTANT]  
    >  iPad では、レポート マネージャーでのレポートの表示はサポートされていません。  
  
4.  次のように操作することによって、スクロールやズームを行います。  
  
    -   レポートをスクロールするには、画面上で指をドラッグします (上、下、左、または右)。 これはスワイプ ジェスチャです。  
  
    -   拡大するには、画面に指を 2 本当て、指と指の距離を広げます。 縮小するには、画面に指を 2 本当て、指と指の距離を狭めます。 これはピンチ ジェスチャです。  
  
5.  次のように操作することによって、レポートでの移動と操作を行います。  
  
    -   レポート アイテムや、グループに関連付けられている行と列を折りたたむにはプラス記号 (+) をタップし、展開するにはマイナス記号 (-) をタップします。  
  
    -   テーブルの行またはマトリックスの行と列を昇順および降順で並べ替えるには、並べ替えボタンをタップします。 並べ替えボタンは、通常、列ヘッダーにあります。  
  
    -   パラメーター ペインを展開したり折りたたんだりするには、レポートの上部にある矢印ボタンをタップします。  
  
    -   パラメーター値を選択するには、パラメーターの横にあるボックスまたはコントロールをタップします。 パラメーター値をレポートに適用するには、 **[レポートの表示]** をタップします。  
  
    -   レポートの内容を検索するには、 **[検索]** の横にあるボックスをタップし、検索語句を入力して、 **[検索]** をタップします。  
  
    -   レポートのページ間を移動するには、ナビゲーション ボタンをタップするか、ボタンの横にあるテキスト ボックスをタップしてページ番号を入力します。  
  
    -   URL に移動するには、レポート アイテムに追加されたテキスト ボックス、画像、グラフ、ゲージなどのハイパーリンクをタップします。  
  
    -   レポートをエクスポートするには、 **[エクスポート]** メニューのアイコンをタップし、ファイル形式をタップします。  
  
        -   Microsoft Surface デバイスでレポートを表示している場合は、次のいずれかの形式にレポートをエクスポートできます。  
  
            -   レポート データが含まれている XML ファイル  
  
            -   CSV (コンマ区切り)  
  
            -   PDF  
  
            -   MHTML (Web アーカイブ)  
  
            -   Excel  
  
            -   TIFF  
  
            -   Word  
  
        -   IPad でレポートを表示している場合は、TIFF または PDF ファイルとしてレポートをエクスポートできます。  
  
## <a name="authentication"></a>認証  
 RSWindowsNTLM 認証および RSWindowsBasic 認証は、ネイティブ モードと iPad の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で動作します。  
  
 一般に、この種類の認証は転送資格認証に機密性を提供しないため、RSWindowsBasic は HTTPS 環境以外では使用しないことをお勧めします。  
  
 RSWindowsNTLM 認証と RSWindowsBasic 認証の詳細については、「 [Authentication with the Report Server](security/authentication-with-the-report-server.md)」を参照してください。  
  
## <a name="uploading-reports"></a>レポートのアップロード  
 適切な権限がある場合は、次のどちらかの方法を使用して Microsoft Surface デバイスからレポートをパブリッシュできます。  
  
> [!IMPORTANT]  
>  iPad ではこれらの方法はサポートされません。  
  
-   ライブラリを開き、 **[ドキュメントのアップロード]** をタップして、SharePoint ドキュメント ライブラリにレポート定義ファイル (.rdl) をアップロードします。  
  
-   レポート マネージャーを開き、 **[ファイルのアップロード]** をタップして、レポート サーバー データベースにレポート定義ファイルをアップロードします。  
  
## <a name="additional-information"></a>追加情報  
 
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] およびサポートされているブラウザーの詳細については、以下を参照してください。  
  
-   [Reporting Services と Power View のブラウザーサポートの計画 &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)  
  
 Microsoft Business Intelligence およびモバイル デバイスの詳細については、以下を参照してください。  
  
-   [モバイルデバイスと SharePoint 2013 の概要](https://technet.microsoft.com/library/fp161351\(v=office.15\).aspx)(https://technet.microsoft.com/library/fp161351(v=office.15).aspx)をご説明します。  
  
-   [SharePoint 2013 でサポートされているモバイルデバイスブラウザー](https://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161353(v=office.15).aspx))  
  
-   [Apple iPad デバイスでのレポートとスコアカードの表示 (SharePoint Server 2010)](https://technet.microsoft.com/library/hh697482.aspx) (https://technet.microsoft.com/library/hh697482.aspx)を参照してください。  
  
-   [IPad での Reporting Services レポートの表示 (ビデオ)](https://technet.microsoft.com/sqlserver/jj873792.aspx) (https://technet.microsoft.com/sqlserver/jj873792.aspx)を参照してください。  
  
-   [Microsoft Surface RT デバイスでの Reporting Services レポートの表示 (ビデオ)](https://technet.microsoft.com/sqlserver/dn146017)  
  
  
