---
title: PowerPivot for SharePoint 2010 の構成または修復 (PowerPivot 構成ツール) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d61f49c5-efaa-4455-98f2-8c293fa50046
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 350aadcdd44dcc4424b94792286a7421e2613b2e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087387"
---
# <a name="configure-or-repair-powerpivot-for-sharepoint-2010-powerpivot-configuration-tool"></a>PowerPivot for SharePoint 2010 の構成または修復 (PowerPivot 構成ツール)
  
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] PowerPivot for SharePoint 2010 のインストールを構成または修復するには、PowerPivot 構成ツールを使用します。 構成ツールはまずシステムをスキャンし、インストールを完了または修復するために必要なアクションの一覧を返します。 セットアップ[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]ウィザードでは、sharepoint 2010 用の Powerpivot 構成ツールと、sharepoint 2013 用 Powerpivot 構成ツールがインストールされます。 このトピックでは、SharePoint 2010 用 PowerPivot 構成ツールについて説明します。 SharePoint 2010 の詳細については、「 [PowerPivot 構成ツール&#41;&#40;PowerPivot for SharePoint 2013 の構成または修復](power-pivot-sharepoint/configure-or-repair-power-pivot-for-sharepoint-2013.md)」を参照してください。  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010  
  
 
  
##  <a name="bkmk_before"></a>開始する前に  
 PowerPivot for SharePoint 2010 構成ツールでは、プログラム ファイル、レジストリ設定、および使用可能なポートをスキャンします。 ツールを最も有効に利用するには、次をご確認ください。  
  
-   構成ツール [PowerPivot Configuration Tools](power-pivot-sharepoint/power-pivot-configuration-tools.md)を実行するための一般的な要件。  
  
-   PowerPivot for SharePoint 2010 には、クラシック モード認証用に構成された Web アプリケーションが必要です。 PowerPivot for SharePoint 2010 構成ツールでアプリケーションを作成すると、アプリケーションはクラシック モード用に構成されます。  
  
-   構成ツールで選択したタスクのいずれかで Web アプリケーションを作成および構成する場合は、ポート 80 が使用できる必要があります。  
  
##  <a name="bkmk_using"></a>PowerPivot 構成ツールの使用  
 このツールの最初のページには、SharePoint ファームの構成に使用する入力値の概要が示されます。 システムの構成には、ユーザーが指定する入力値のほか、既定値が使用されます。 サービス アプリケーション、サービス アプリケーション データベース、およびサービス アプリケーション プロパティには既定の名前が使用されます。  
  
> [!TIP]  
>  PowerPivot 構成ツールがコンピューターをスキャンし、左ペインに空のタスク一覧が返された場合、機能や設定を構成する必要はありません。 SharePoint または PowerPivot の構成を変更するには、Windows PowerShell または SharePoint サーバーの全体管理の管理ページを使用します。 詳細については、「[サーバーの全体管理での PowerPivot サーバーの管理と構成](power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)」を参照してください。  
  
 サービス アカウントの値は複数のサービスに利用されます。 たとえば、PowerPivot 構成ツールの最初のページの既定のアカウントがすべてのアプリケーション プール ID の設定に使用されます。 これらのアカウントは、サーバーの全体管理のサービス アプリケーション プロパティを変更することで、後から変更できます。  
  
-   ただし、Analysis Services サービス アカウントは例外です (PowerPivot for SharePoint 2010 構成ツールの場合)。 このアカウントはセットアップ時に指定し、[ **SQL Server Analysis Services (PowerPivot On ローカルサーバー) の登録**] アクションでこのアカウントのパスワードを入力します。 概要ページには、このパスワードのフィールドは含まれていないため、このアクションのページで必ず入力してください。  
  
 このツールにはタブ付きインターフェイスが用意されており、パラメーターの入力、Windows PowerShell スクリプト、および状態メッセージが含まれています。  
  
 PowerPivot 構成ツールでは、Windows PowerShell を使用してサーバーを構成します。 [**スクリプト**] タブをクリックすると、Windows PowerShell スクリプトを確認できます。  
  
 ![構成ツールのユーザー インターフェイス](media/ssas-pctui.gif "構成ツールのユーザー インターフェイス")  
  
##  <a name="bkmk_steps"></a>構成手順  
 構成ツールへのリンクは、ローカルサーバーに PowerPivot for SharePoint 2010 がインストールされている場合にのみ表示されます。  
  
1.  [**スタート**] ボタンをクリックし、[**すべて**の[!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]プログラム] をポイントします。次に、[]、[**構成ツール**]、[ **PowerPivot 構成ツール**] の順にクリックします。  
  
2.  
  **[PowerPivot for SharePoint の構成または修復]** をクリックします。  
  
3.  ウィンドウを最大化します。 ウィンドウの下部に **[検証]** 、 **[実行]** 、および **[終了]** の各コマンドを含むボタン バーが表示されます。  
  
4.  **既定のアカウント:**[パラメーター] タブで、**既定のアカウントユーザー名**のドメインユーザーアカウントを入力します。 このアカウントは、PowerPivot サービス アプリケーション プールなどの重要なサービスを準備する場合に使用されます。 Network Service や Local System などのビルトイン アカウントは指定しないでください。 ビルトイン アカウントを指定する構成はブロックされます。  
  
     **パスフレーズ:** パスフレーズを入力します。 新しい SharePoint ファームでは、SharePoint ファームに新しいサーバーまたはアプリケーションを追加するたびにこのパスフレーズが使用されます。 既存のファームの場合、ファームにサーバー アプリケーションを追加するためのパスフレーズを入力します。  
  
5.  **ポート:** 必要に応じて、サーバーの全体管理 web アプリケーションに接続するためのポート番号を入力するか、ランダムに生成された番号を使用します。 オプションとして提示される番号は、使用できるかどうかがあらかじめチェックされています。  
  
6.  [**ローカルサーバーに SQL Server Analysis Services (PowerPivot) を登録**する] をクリックします。  
  
     Analysis Services サービス アカウントのパスワードを入力します。  
  
7.  必要に応じて、各アクションを完了するために使用された残りの入力値を確認します。 それぞれの入力値の詳細については、このトピックの [サーバーの構成に使用する入力値](#bkmk_input) をご覧ください。  
  
8.  必要に応じて、処理しないすべてのアクションを削除します。 たとえば、Secure Store Service を後で構成する場合は、 **[Secure Store Service の構成]** をクリックし、 **[この操作をタスク一覧に含めます]** チェック ボックスをオフにします。  
  
9. 
  **[検証]** をクリックして、一覧のアクションを処理するための十分な情報があるかどうかを確認します。  
  
    > [!NOTE]  
    >  ファーム構成エラーが発生した場合、SharePoint 2010 Server SP1 がインストールされていないことが原因である可能性があります。  
  
10. 
  **[実行]** をクリックして、タスクの一覧にあるすべてのアクションを処理します。 
  **[実行]** は、アクションの検証後に有効になります。 
  **[実行]** が有効になっていない場合は、まず **[検証]** をクリックしてください。  
  
11. [PowerPivot for SharePoint のインストールを確認](instances/install-windows/verify-a-power-pivot-for-sharepoint-installation.md)します。  
  
##  <a name="bkmk_input"></a>サーバーの構成に使用する入力値  
 PowerPivot 構成ツールでは、ユーザーが入力する入力値と自動的に検出または使用される既定値を組み合わせて使用します。  
  
 構成ツールに表示されるアクションの一覧は、SharePoint ファームの現在の構成によって異なります。 たとえば、SharePoint ファームが既に構成されている場合、このツールにはアクションが表示されません。 いつでもこのツールを実行して、構成、構成エラーの修復、または検出を行うことができます。 ファームで Excel Services や Secure Store Service などの必要なサービスが実行されていない場合は、そのサービスが検出され、それを有効にするオプションが提供されます。 必要なアクションがない場合は、タスクの一覧は空になります。  
  
 次の表は、サーバーの構成に使用する値を示しています。  
  
|ページ|入力値|source|[説明]|  
|----------|-----------------|------------|-----------------|  
|**PowerPivot for SharePoint の構成または修復**|既定のアカウント|現在のユーザー|既定のアカウントは、ファーム内の共有サービスの準備に使用するドメイン Windows ユーザー アカウントです。 PowerPivot サービス アプリケーション、Secure Store Service、Excel Services、Web アプリケーション プールの ID、サイト コレクション管理者、および PowerPivot 自動データ更新アカウントの準備に使用します。<br /><br /> 既定では、このツールは現在のユーザーのドメインアカウントを入力します。 評価の目的でサーバーを構成する場合を除き、この値を別のドメイン ユーザー アカウントに置き換える必要があります。<br /><br /> また、サービス ID は、後からサーバーの全体管理を使用して変更することもできます。<br /><br /> 必要に応じて、PowerPivot 構成ツールで次の専用のアカウントを指定できます。<br /><br /> Web アプリケーション。 [**既定の Web アプリケーションの作成**] ページを使用します (このツールでファームの web アプリケーションが作成されていることを前提としています)。<br /><br /> PowerPivot 自動データ更新アカウント。このツールの [**データ更新の自動アカウントの作成**] ページを使用します。|  
||データベース サーバー|ローカルの PowerPivot 名前付きインスタンス (存在する場合)|データベース エンジン インスタンスが PowerPivot 名前付きインスタンスとしてインストールされている場合は、[データベース サーバー] フィールドにこのインスタンスが入力されます。 データベース エンジンをインストールしていない場合は、このフィールドは空です。 インスタンスを指定する必要があります。 SharePoint ファームでサポートされる SQL Server であれば、バージョンやエディションは問いません。|  
||Passphrase|ユーザー入力|新しいファームを作成する場合、ユーザーが入力するパスフレーズがファームのパスフレーズになります。 既存のファームに PowerPivot for SharePoint を追加する場合は、ファームの作成時に定義したパスフレーズを指定する必要があります。|  
||SharePoint サーバーの全体管理のポート|既定 (必要な場合)|ファームが構成されていない場合は、サーバーの全体管理への HTTP エンドポイントなど、ファームを作成するためのオプションが提供されます。 既定では、使用されていない、ランダムに生成されたポート番号に設定されます。|  
|**新しいファームの構成**|データベース サーバー<br /><br /> ファーム アカウント<br /><br /> パスフレーズ<br /><br /> SharePoint サーバーの全体管理のポート|既定 (必要な場合)|既定では、メイン ページで入力した設定になります。|  
|**ローカル サービスのインスタンスの構成**|Analysis Services サービス アカウントのパスワード|ユーザー入力|**[ローカルサーバーの SQL Server Analysis Services (PowerPivot) の登録**] ページで Analysis Services サービスアカウントのパスワードを入力する必要があります。<br /><br /> サービス アカウントは、セットアップの際に指定したものです。 ここで、SharePoint にローカル サービス インスタンスを登録するためのパスワードを入力する必要があります。|  
|**PowerPivot サービス アプリケーションの作成**|PowerPivot サービス アプリケーション名|Default|既定の名前は、"既定の PowerPivot サービス アプリケーション" です。 ツールで別の値に置き換えることができます。|  
||PowerPivot サービス アプリケーション データベース サーバー|Default|PowerPivot サービス アプリケーション データベースをホストするデータベース サーバー。 既定のサーバー名は、ファームに使用するのと同じデータベース サーバーです。 ツールで別の値に置き換えることができます。|  
||PowerPivot サービス アプリケーション データベース名|Default|既定のデータベース名は、サービス アプリケーション名の後ろに GUID を付けて一意の名前にしたものです。 ツールで別の値に置き換えることができます。|  
||ブックをアップグレードして、データ更新を有効にします|ユーザー入力|データ更新は失敗します。SQL Server 2008 R2 PowerPivot ブックではサポートされていません。 [ブックをアップグレードして**データ更新を有効にする**] オプションを選択すると、ブックが SQL Server 2012 PowerPivot バージョンにアップグレードされます。|  
|**既定の Web アプリケーションの作成**|Web アプリケーション名|既定 (必要な場合)|Web アプリケーションが存在しない場合は 1 つ作成されます。 Web アプリケーションは、クラシックモード認証用に構成され、**ポート 80**でリッスンします。 ファイルの最大アップロード サイズは、SharePoint で許容される最大値の 2047 MB に設定されます。 大きい PowerPivot ファイルに対応するために、ファイル アップロード サイズが拡大されます。|  
||URL|既定 (必要な場合)|SharePoint と同じファイル名前付け規則を使用して、サーバー名に基づく URL が作成されます。|  
||Web アプリケーション プール|既定 (必要な場合)|IIS で既定のアプリケーション プールが作成されます。|  
||Web アプリケーション プール アカウントとパスワード|既定 (必要な場合)|アプリケーション プール アカウントは既定のアカウントに基づいていますが、このツールでオーバーライドできます。|  
||Web アプリケーション データベース サーバー|既定 (必要な場合)|アプリケーション データベースの格納先として既定のデータベース インスタンスがあらかじめ選択されていますが、このツールで別の SQL Server インスタンスを指定できます。|  
||Web アプリケーション データベース名|既定 (必要な場合)|データベース名は SharePoint のファイル名前付け規則に基づいていますが、別の名前を選択できます。|  
|**Web アプリケーションソリューションの配置**|URL|既定 (必要な場合)|既定の URL は、既定の Web アプリケーションから取得されます。|  
||ファイルの最大サイズ (MB)|既定 (必要な場合)|既定の設定は 2047 です。 SharePoint ドキュメント ライブラリにも最大サイズがあり、PowerPivot の設定がドキュメント ライブラリの設定を超えないようにする必要があります。 詳細については、「 [PowerPivot for SharePoint&#41;&#40;最大ファイルアップロードサイズを構成する](power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint.md)」を参照してください。|  
|**サイトコレクションの作成**|サイト管理者|既定 (必要な場合)|既定のアカウントが使用されます。 これは **[サイト コレクションの作成]** ページでオーバーライドできます。|  
||連絡先の電子メール|既定 (必要な場合)|サーバーに Microsoft Outlook が構成されている場合は、現在のユーザーの電子メール アドレスが使用されます。 それ以外の場合は、プレースホルダー値が使用されます。|  
||サイトの URL|既定 (必要な場合)|SharePoint と同じ URL 名前付け規則を使用して、サイト URL が作成されます。|  
||サイトのタイトル|既定 (必要な場合)|既定のタイトルとして **[PowerPivot サイト]** が追加されます。|  
|**サイト コレクション内の PowerPivot 機能のアクティブ化**|サイトの URL||PowerPivot 機能をアクティブにするサイト コレクションの URL。|  
||このサイトのプレミアム機能を有効にします||SharePoint サイト機能 "PremiumSite" を有効にします。|  
|**Secure Store Service アプリケーションの作成**|サービス アプリケーション名||Secure Store Service アプリケーションの名前を入力します。|  
||データベース サーバー||Secure Store Service アプリケーションに使用するデータベース サーバーの名前を入力します。|  
|**Secure Store Service アプリケーションプロキシの作成**|サービス アプリケーション名||Secure Store Service アプリケーションの名前を入力します。|  
||サービス アプリケーション プロキシ||Secure Store Service アプリケーション プロキシの名前を入力します。  この名前は、アプリケーションと SharePoint コンテンツ Web アプリケーションを関連付ける既定の接続グループに表示されます。|  
|**マスターキーの更新 Secure Store Service**|サービス アプリケーション プロキシ||Secure Store Service アプリケーション プロキシの名前を入力します。|  
||Passphrase||データ暗号化にはマスター キーが使用されます。 既定では、キーの生成に使用されるパスフレーズは、ファーム内の新しいサーバーの準備に使用されるパスフレーズと同じです。 既定のパスフレーズを一意のパスフレーズに置き換えることができます。|  
|**Datarefresh の自動アカウントの作成**|ターゲット アプリケーションの ID||アプリケーション ID には、わかりやすいテキストを指定できます。|  
||ターゲット アプリケーションのフレンドリ名|||  
||自動アカウントのユーザー名とパスワード||ターゲット アプリケーションで自動データ更新を実行するために使用される Windows ユーザー アカウントの資格情報を入力します。|  
||サイトの URL||ターゲット アプリケーションが関連付けられるサイト コレクションのサイト URL を入力します。 追加のサイト コレクションに関連付けるには、SharePoint サーバーの全体管理を使用します。|  
|**Excel Services サービスアプリケーションの作成**|サービス アプリケーション名||サービス アプリケーションの名前を入力します。 同じ名前のサービスアプリケーションデータベースが SharePoint ファームのデータベースサーバーに作成されます。|  
|**MSOLAP.5 を信頼できるプロバイダーとして追加**|サービス アプリケーション名||SharePoint 2010 の Excel Services は、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] OLE DB プロバイダーを使用して [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データに接続します。 この手順では、PowerPivot for SharePoint と共にインストールされた OLE DB プロバイダーのバージョンを、信頼できるプロバイダーとして Excel Services に追加します。|  
||PowerPivot サーバーの名前|||  
|||||  
  
 PowerPivot 構成ツールでファームを作成すると、SharePoint と同じファイル名前付け規則を使用してデータベース サーバーに必要なデータベースが作成されます。 ファーム データベース名は変更できません。  
  
 このツールでサイト コレクションを作成すると、SharePoint と同じファイル名前付け規則を使用してデータベース サーバーにコンテンツ データベースが作成されます。 コンテンツ データベース名は変更できません。  
  
##  <a name="bkmk_nextsteps"></a>次のステップ  
 サーバーのインストールが完了したら、次のいくつかのインストール後の作業を実行する必要があります。  
  
-   個人やグループに SharePoint 権限を付与します。 このタスクは、サイトとコンテンツにアクセスできるようにするために必要です。  
  
-   別のアカウントで実行するように、サービス アプリケーション プール ID を変更します。 サービスとアプリケーションに別の ID を指定することは、SharePoint を安全に配置するための推奨事項の 1 つです。  
  
-   PowerPivot データ アクセスに最も効果的な権限と構成設定に変更できるように、Excel Services に追加の信頼できるサイトを作成します。  
  
-   SharePoint リストからのデータ フィードのエクスポートを可能にする ADO.NET Data Services 3.5 SP1 をインストールします。  
  
-   サーバー側のデータ更新を有効にするには、一般的に使用されるデータ プロバイダーをインストールします。  
  
-   PowerPivot 作成ツールをワークステーション コンピューターにダウンロードして PowerPivot ブックを作成し、SharePoint にパブリッシュします。 ツールのインストールと PowerPivot ブックのパブリッシュによって、インストールしたサーバー コンポーネントの相互運用性が確認され、インストール サイクルが完了します。  
  
### <a name="grant-sharepoint-permissions-to-workbook-users"></a>ブックのユーザーへの SharePoint 権限の付与  
 ユーザーがブックをパブリッシュまたは表示するには、SharePoint 権限が必要です。 パブリッシュされたブックを表示する必要があるユーザーには**表示**権限を付与し、ブックをパブリッシュまたは管理するユーザーには**投稿**権限を与えるようにしてください。 権限を付与するには、サイト コレクションの管理者である必要があります。  
  
1.  サイトで、[**サイトの操作**] をクリックします。  
  
2.  [**サイトの権限**] をクリックします。  
  
3.  
  **投稿** 権限を持つ一連のユーザーと **表示** 権限のみを持つ一連のユーザーの別のグループが必要な場合は、必要に応じてグループを作成します。  
  
4.  グループのメンバーシップを持っている Windows ドメインのユーザー アカウントまたはグループ アカウントを入力します。 上で説明した手順と同様に、アプリケーションで従来の認証が構成されている場合は、電子メール アドレスまたは配布グループを使用しないでください。  
  
### <a name="install-adonet-data-services-35-sp1"></a>ADO.NET Data Services 3.5 SP1 のインストール  
 ADO.NET Data Services は、SharePoint リストのデータ フィードのエクスポートに必要です。 SharePoint 2010 では、このコンポーネントは PrerequisiteInstaller プログラムに含まれていないため、手動でインストールする必要があります。  
  
1.  SharePoint 2010 のハードウェアとソフトウェアの要件に関するドキュメントを参照し、[ハードウェアとソフトウェアの要件を決定する (sharepoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  「前提条件となっているソフトウェアをインストールする」で、使用しているオペレーティング システムに対応する ADO.NET Data Services 3.5 のリンクを見つけます。  
  
3.  リンクをクリックし、サービスをインストールするセットアップ プログラムを実行します。  
  
### <a name="install-data-providers-used-in-data-refresh-and-check-user-permissions"></a>データ更新で使用するデータ プロバイダーのインストールとユーザー権限の確認  
 サーバー側のデータ更新により、ユーザーは更新されたデータをブックに自動モードで再インポートできます。 データ更新を正常に行うためには、最初にデータをインポートするために使用したものと同じデータ プロバイダーがサーバーに必要になります。 さらに、通常は、データ更新を実行するユーザー アカウントに外部データ ソースに対する読み取り権限が必要です。 データ更新を正常に実行できるように、データ更新の有効化と構成の要件をご確認ください。 詳細については、「 [SharePoint 2010 での PowerPivot データ更新](powerpivot-data-refresh-with-sharepoint-2010.md)」を参照してください。  
  
### <a name="change-application-pool-and-service-identities-in-sharepoint"></a>SharePoint のアプリケーション プールおよびサービス ID の変更  
 PowerPivot 構成ツールでは、ファーム機能、アプリケーション、およびサービスが 1 つのアカウントを使用して実行されるように準備されます。 これによりインストールは簡略化されますが、SharePoint ファームのセキュリティ要件を満たす配置にはなりません。 配置の堅牢性を高めるには、セットアップの完了後に、異なるアカウントで実行するためにアプリケーション プールおよびサービス ID を変更します。 詳細については、「 [PowerPivot サービスアカウントの構成](power-pivot-sharepoint/configure-power-pivot-service-accounts.md)」を参照してください。  
  
### <a name="create-additional-trusted-sites-in-excel-services"></a>Excel Services に追加の信頼できるサイトの作成  
 Excel Services に信頼できるサイトを追加して、Excel ブックおよび PowerPivot のデータを提供するサイトの権限および構成設定を変更できます。 詳細については、「 [Create a trusted location for PowerPivot sites in Central Administration](power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)」を参照してください。  
  
### <a name="add-servers-or-applications"></a>サーバーまたはアプリケーションの追加  
 後でデータ ストレージや処理能力を追加する必要が生じた場合は、ファームに 2 つ目の PowerPivot for SharePoint サーバー インスタンスを追加することができます。 手順については、「[配置のチェックリスト: SharePoint 2010 ファームへの PowerPivot サーバーの追加によるスケールアウト](../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)」を参照してください。  
  
## <a name="additional-resources"></a>その他のリソース  
 ![SharePoint の設定](media/as-sharepoint2013-settings-gear.gif "SharePoint の設定")では Microsoft SQL Server Connect (https://connect.microsoft.com/SQLServer/Feedback))[を使用してフィードバックと連絡先情報を送信し](https://connect.microsoft.com/SQLServer/Feedback)ます。  
  
## <a name="see-also"></a>参照  
 [PowerPivot 構成ツール](power-pivot-sharepoint/power-pivot-configuration-tools.md)   
 [サーバーの全体管理での PowerPivot サーバーの管理と構成](power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  
