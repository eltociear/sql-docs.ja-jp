---
title: PowerPivot for SharePoint アドインのインストールまたはアンインストール (SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: fe13ce8b-9369-4126-928a-9426f9119424
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f7a5abbb831d6630ebb7846534c7a9a96c83e861
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "72797370"
---
# <a name="install-or-uninstall-the-powerpivot-for-sharepoint-add-in-sharepoint-2013"></a>PowerPivot for SharePoint アドインのインストールまたはアンインストール (SharePoint 2013)
  
  [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] は、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ファームでの [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] データ アクセスを提供するアプリケーション サーバー コンポーネントとバックエンド サービスのコレクションです。 
  [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint アドイン (**spPowerpivot.msi**) は、アプリケーション サーバー コンポーネントのインストールに使用されるインストーラー パッケージです。  
  
-   このアドインは、SharePoint 2010 の配置に必須ではありません。  
  
-   このアドインは、SharePoint 2013 と SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が含まれるシングル サーバー配置では必須ではありません。 アドインによってインストールされたコンポーネントは、SharePoint モードで [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーをインストールするときに含まれます。 アドインを使用した配置例の図については、「 [SharePoint の SQL SERVER BI 機能の配置トポロジ](../../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)」を参照してください。  
  
 **注:** このトピックでは、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]ソリューションファイルと[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 構成ツールのインストールについて説明します。 インストール後に、構成ツールとその他の機能の詳細については、次のトピックを参照してください。 [SharePoint 2013&#41;&#40;、PowerPivot の構成とソリューションの配置](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)です。  
  
 
  **spPowerPivot.msi**をダウンロードする方法の詳細については、「 [Microsoft® SQL Server® 2014 PowerPivot® for Microsoft SharePoint®](https://go.microsoft.com/fwlink/?LinkID=324854)」を参照してください。  
  
 **このトピックの内容:**  
  
-   [バックグラウンド](#bkmk_background)  
  
-   [SpPowerPivot .msi のインストール場所](#bkmk_where_to_install)  
  
-   [要件と前提条件](#bkmk_prereq)  
  
-   [PowerPivot for SharePoint をインストールするには](#bkmk_install)  
  
-   [PowerPivot for SharePoint 2013 構成ツールを使用した SharePoint ソリューション ファイルの配置](#bkmk_deploy_solution)  
  
-   [アドインをアンインストールまたは修復する](#bkmk_remove_addin)  
  
##  <a name="bkmk_background"></a> 背景情報  
  
-   **アプリケーションサーバー:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] SharePoint 2013 の機能には、データソースとしてのブックの使用、定期[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]データ更新、管理ダッシュボードが含まれます。  
  
     [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)]は、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Analysis Services クライアントライブラリを配置し、インストールファイルをコンピューターにコピー [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)]する Windows インストーラーパッケージ (**sppowerpivot .msi**) です。 インストーラーは、SharePoint での [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 機能の配置や構成は行いません。 既定では、次のコンポーネントがインストールされます。  
  
    -   
  [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013。このコンポーネントには、PowerShell スクリプト (.ps1 ファイル)、SharePoint ソリューション パッケージ (.wsp)、および SharePoint 2013 ファームに [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] を配置するための [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 2013 構成ツールが含まれています。  
  
    -   
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for Analysis Services (MSOLAP)。  
  
    -   ADOMD.NET データ プロバイダー。  
  
    -   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分析管理オブジェクト。  
  
-   **バックエンドサービス:** For Excel を[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]使用して分析データを含むブックを作成する場合、サーバー環境でそのデータにアクセスする[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]には、SharePoint モードで実行されている BI サーバーで excel Services が構成されている必要があります。 SQL Server セットアップは、SharePoint Server 2013 がインストールされているコンピューターで実行することも、SharePoint ソフトウェアがインストールされていない別のコンピューターで実行することもできます。 Analysis Services には、SharePoint との依存関係はありません。  
  
     バックエンド サービスのインストール、アンインストール、構成の詳細については、次のトピックを参照してください。  
  
    -   [PowerPivot for SharePoint 2013 のインストール](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)  
  
    -   [PowerPivot for SharePoint のアンインストール](../../../sql-server/install/uninstall-power-pivot-for-sharepoint.md)  
  
##  <a name="bkmk_where_to_install"></a>SpPowerPivot .msi のインストール場所  
 ベスト プラクティスとして、構成の一貫性を確保するために、SharePoint ファームのすべてのサーバー (アプリケーション サーバーや Web フロントエンド サーバーなど) に **spPowerPivot.msi** をインストールすることをお勧めします。 インストーラー パッケージには、Analysis Services データ プロバイダーと [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 構成ツールが含まれています。 
  **spPowerPivot.msi** をインストールするときに、個々のコンポーネントを除外することで、インストールをカスタマイズできます。  
  
 **データプロバイダー:** いくつかの SharePoint および SQL Server テクノロジでは、Excel Services、PerformancePoint Services、Power View などの Analysis Services データプロバイダーが使用されます。 
  **spPowerPivot.msi** をすべての SharePoint サーバーにインストールすると、Analysis Services データ プロバイダーの完全なセットと PowerPivot の接続をファーム全体で常に使用できるようになります。  
  
> [!NOTE]  
>  Analysis Services データ プロバイダーは、 **spPowerPivot.msi**を使用して SharePoint 2013 サーバーにインストールする必要があります。 
  [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Feature Pack に用意されている他のインストーラー パッケージには、この環境でデータ プロバイダーが必要とする SharePoint 2013 サポート ファイルが含まれていないため、これらのパッケージはサポートされていません。  
  
 **構成ツール:** PowerPivot for SharePoint 2013 構成ツールは、1つの SharePoint サーバーに対してのみ必要です。 ただし、ベスト プラクティスとして、マルチサーバー ファームでは少なくとも 2 台のサーバーに構成ツールをインストールし、一方のサーバーがオフラインの場合でも構成ツールにアクセスできるようにしておくことをお勧めします。  
  
##  <a name="bkmk_prereq"></a>要件と前提条件  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)]SharePoint Server 2013。  
  
-   **Sppowerpivot .msi**は、SharePoint 製品およびテクノロジの要件に従って、64ビットのみです。  
  
-   PowerPivot モードの [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] サーバー。 Excel Services では、PowerPivot サーバーとして SQL Server Analysis Services インスタンスを使用します。 Analysis Services は、ローカル コンピューターでもリモート コンピューターでも実行できます。  
  
-   **アクセス許可:** をインストール[!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)]するには、現在のユーザーがコンピューターの管理者であり、SharePoint ファーム管理者グループである必要があります。  
  
-   [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]要件と前提条件の詳細については、「 [SharePoint モードの Analysis Services Server のハードウェアとソフトウェアの要件 &#40;SQL Server 2014&#41;」](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md)を参照してください。  
  
##  <a name="bkmk_install"></a>PowerPivot for SharePoint をインストールするには  
 
  **spPowerpivot.msi** インストーラー パッケージは、グラフィカル ユーザー インターフェイスとコマンド ライン モードの両方をサポートしています。 どちらのインストール方法でも、管理者特権で .msi を実行する必要があります。 インストール後に、構成ツールとその他の機能の詳細については、次のトピックを参照してください。 [SharePoint 2013&#41;&#40;、PowerPivot の構成とソリューションの配置](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013)です。  
  
### <a name="user-interface-installation"></a>ユーザー インターフェイスを使用したインストール  
 グラフィカル ユーザー インターフェイスを使用して [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] をインストールするには、次の手順を実行します。  
  
1.  
  **SpPowerPivot.msi**を実行します。  
  
2.  [ようこそ] ページで **[次へ]** をクリックします。  
  
3.  使用許諾契約書を確認して同意し、 **[次へ]** をクリックします。  
  
4.  
  **[機能の選択]** ページでは、すべての機能が既定で選択されています。  
  
5.  **[次へ]** をクリックします。  
  
6.  
  **[インストール]** をクリックしてインストールを実行し、インストールを終了します。  
  
### <a name="command-line-installation"></a>コマンド ライン インストール  
 コマンド ライン インストールでは、管理権限でコマンド プロンプトを開き、 **spPowerPivot.msi**を実行します。 次に例を示します。  
  
 `Msiexec.exe /i SpPowerPivot.msi`.  
  
 インストール ログを作成するには、MsiExec の標準のログ スイッチを使用します。 次の例では、"v" 詳細ログスイッチを使用してログファイル "Install_Log" を作成します。  
  
```cmd
Msiexec.exe /i SpPowerPivot.msi /L v c:\test\Install_Log.txt  
```  
  
### <a name="quiet-command-line-installation-for-scripting"></a>スクリプト作成のためのサイレント コマンド ライン インストール  
 
  **/q** スイッチまたは **/quiet** スイッチを使用すると、ダイアログや警告が表示されない "サイレント" インストールを実行できます。 サイレント インストールは、アドインのインストールのスクリプトを作成する場合に役立ちます。  
  
> [!IMPORTANT]  
>  サイレント コマンド ライン インストールで **/q** スイッチを使用する場合、使用許諾契約書は表示されません。 インストール方法にかかわらず、このソフトウェアの使用は、使用許諾契約に基づいています。ユーザーは使用許諾契約に準拠する責任があります。  
  
#### <a name="to-perform-a-quiet-installation"></a>サイレントインストールを実行するには
  
1.  
  **管理者権限を使用して**コマンド プロンプトを開きます。  
  
2.  次のコマンドを実行します。  
  
    ```cmd
    Msiexec.exe /i spPowerPivot.msi /q  
    ```  
  
### <a name="command-line-installation-to-include-specific-components"></a>コマンド ラインを使用した特定のコンポーネントのインストール  
 
  [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 構成ツールは、すべての SharePoint サーバーで必須というわけではありません (ただし、必要なときに使用できるように、少なくとも 2 台のサーバーにインストールすることをお勧めします)。  
  
 spPowerPivot.msi をインストールするときに、コマンド ライン オプションを使用して、 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 構成ツールではなく、データ プロバイダーなどの特定の項目をインストールすることができます。 構成ツール以外のすべてのコンポーネントをインストールするコマンド ラインの例を次に示します。  
  
```  
Msiexec /i spPowerPivot.msi AGREETOLICENSE="yes" ADDLOCAL=" SQL_OLAPDM,SQL_ADOMD,SQL_AMO,SQLAS_SP_Common"  
```  
  
|オプション|[説明]|  
|------------|-----------------|  
|Analysis_Server_SP_addin|PowerPivot 構成ツール|  
|SQL_OLAPDM|MSOLAP|  
|SQL_ADOMD|ADOMD.net プロバイダー|  
|SQL_AMO|AMO プロバイダー|  
|SQLAS_SP_Common|SharePoint 2013 の Analysis Services 共通コンポーネント|  
  
##  <a name="bkmk_deploy_solution"></a>PowerPivot for SharePoint 2013 構成ツールを使用した SharePoint ソリューションファイルのデプロイ  
 spPowerPivot.msi によって、3 つの SharePoint ソリューション ファイルがハード ドライブにコピーされます。 ソリューション ファイルのスコープは 1 つが Web アプリケーション レベル、残り 2 つがファーム レベルです。 次のファイルがあります。  
  
-   `PowerPivotFarmSolution.wsp`  
  
-   `PowerPivotFarm14Solution.wsp`  
  
-   `PowerPivotWebApplicationSolution.wsp`  
  
 ソリューション ファイルは次のフォルダーにコピーされます。  
  
 `C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\SPAddinConfiguration\Resources`  
  
 .msi をインストールした後、 [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] 構成ツールを実行して、SharePoint ファームでソリューションを構成し、配置します。  
  
### <a name="to-start-the-configuration-tool"></a>構成ツールを起動するには 
  
 Windows のスタート画面から「power」と入力し、アプリの検索結果で [ **PowerPivot for SharePoint 2013 構成**] をクリックします。 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のセットアップによって SharePoint 2010 と SharePoint 2013 のそれぞれの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成ツールがインストールされるため、検索結果には 2 つのリンクが含まれる場合があります。 必ず SharePoint 2013 構成ツールの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] を起動してください。  
  
 ![2つの powerpivot 構成ツール](https://docs.microsoft.com/analysis-services/analysis-services/media/as-powerpivot-configtools-bothicons.gif "2つの powerpivot 構成ツール")  
  
 **もしくは**  
  
1.  
  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** をポイントします。  
  
2.  
  **[Microsoft SQL Server 2014]** をクリックします。  
  
3.  
  **[構成ツール]** をクリックします。  
  
4.  
  **[PowerPivot for SharePoint 2013 の構成]** をクリックします。  
  
 構成ツールの詳細については、「 [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md)」を参照してください。  
  
##  <a name="bkmk_remove_addin"></a>アドインをアンインストールまたは修復する  
  
> [!CAUTION]  
>  
  **spPowerPivot.msi** をアンインストールすると、データ プロバイダーと構成ツールがアンインストールされます。 データ プロバイダーをアンインストールすると、サーバーは PowerPivot に接続できなくなります。  
  
 
  [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] をアンインストールまたは修復するには、次のいずれかの方法を使用します。  
  
1.  **Windows コントロールパネル:****Microsoft SQL Server 2012 PowerPivot for SharePoint 2013**を選択します。 
  **[アンインストール]** または **[修復]** をクリックします。  
  
2.  spPowerPivot.msi を実行し、 **[削除]** または **[修復]** を選択します。  
  
 **コマンドライン:** コマンドラインを使用して PowerPivot for SharePoint 2013 を修復またはアンインストールするには、**管理者権限で**コマンドプロンプトを開き、次のコマンドのいずれかを実行します。  
  
-   修復するには、次のコマンドを実行します。  
  
    ```cmd
    msiexec.exe /f spPowerPivot.msi  
    ```  
  
 OR  
  
-   アンインストールするには、次のコマンドを実行します。  
  
    ```cmd
    msiexec.exe /uninstall spPowerPivot.msi  
    ```
