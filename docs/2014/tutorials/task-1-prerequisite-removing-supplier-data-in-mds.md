---
title: 'タスク 1 (前提条件): MDS で仕入先データを削除する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6f0a4287-7fd4-4f18-b7e4-a5191a9d4a3c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 84c0acceb4953b819cb5696c4ef90c39e4376846
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65481222"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a>タスク 1 (前提条件): MDS の仕入先データを削除する
  ここでは、MDS に格納されている仕入先データを削除します。 前のレッスンで**MDS Excel アドイン**を使用してデータを手動でアップロードしました。 このレッスンで作成する SSIS パッケージは、MDS にデータを自動的にアップロードします。 したがって、SSIS パッケージをテストする前に、MDS からの仕入先データの削除、派生階層の削除、Supplier および State エンティティの削除、データのない Supplier エンティティの作成が必要となります。  
  
1.  **マスターデータマネージャー**を起動するに**http://localhost/MDS**は、または MDS の構成時に指定した web サイトとアプリケーションに移動します。 **マスターデータマネージャー**を開いたままにしている場合は、上部にある**SQL Server 2012 マスターデータサービス**をクリックして、**ホームページ**に切り替えます。  
  
2.  [**管理タスク**] セクションで [**システム管理**] をクリックします。  
  
3.  メニューの [**管理**] にマウスポインターを合わせ、[**派生階層**] をクリックします。 **サプライヤー**モデル内のエンティティを削除する前に、派生階層の**SuppliersInState**を削除する必要があります。  
  
4.  [**派生階層**] ボックスの一覧の [ **SuppliersInState** ] を選択し、ツールバーの [ **X] (削除)** ボタンをクリックします。  
  
5.  [ **OK** ] をクリックして削除を確定します。  
  
6.  メニューの [**管理**] の上にマウスポインターを置き、[**エンティティ**] をクリックします。  
  
7.  [ **Supplier** ] をクリックし、ツールバーの [**削除] (X)** ボタンをクリックしてエンティティを削除します。 メッセージボックスで [ **OK]** をクリックします。  
  
8.  前の手順を繰り返して、 **State**エンティティを削除します。  
  
9. **マスターデータマネージャー**を閉じないでください。  
  
10. クレンジングされた**仕入先 .xls**ファイルが開いている Excel ウィンドウに切り替えます。 下部にある [ **Sheet1** ] タブに切り替えます。  
  
11. **ヘッダーが含まれている最初の行**のみを選択します。 他の行は選択しないでください。 データをアップロードするのではなく、Excel の列に基づいてエンティティを作成する場合。 したがって、行見出しがある先頭行のみを選択することになります。  
  
12. メニューバーの [**マスターデータ**] をクリックします。  
  
13. リボンで [**エンティティの作成**] をクリックします。  
  
14. [**接続の管理**] ダイアログボックスで、[**既存の接続**] に [**ローカル MDS サーバー**への接続] が表示されない場合は、次の手順を実行します。  
  
    1.  [**新しい接続の作成**] を選択し、[**新規**] ボタンをクリックします。  
  
    2.  [新しい接続の追加] ダイアログボックスで、[**説明**] に「 **http://localhost/MDS**ローカル mds サーバー」と入力し、 **Mds サーバーアドレス**に「**ローカル mds サーバー** 」と入力して、[ **OK** ] をクリックしてダイアログボックスを閉じます。  
  
15. [**接続の管理**] ダイアログボックスで [**ローカル MDS サーバー** http://localhost/MDS)] を選択し、[**テスト**] をクリックして接続をテストします。 メッセージボックスで [ **OK]** をクリックします。  
  
16. [**接続**] をクリックして、MDS サーバーに接続します。  
  
17. [**エンティティの作成**] ダイアログボックスで、次の操作を行います。  
  
    1.  **範囲**が **$ 1: $** 1 に設定されていることを確認します。  
  
    2.  **モデル**の**仕入先**を選択します。  
  
    3.  [**バージョン**] で [ **VERSION_1** ] を選択します。  
  
    4.  **新しいエンティティ名**として「 **Supplier** 」と入力します。  
  
    5.  [**コード**の**仕入**先] を選択します。  
  
    6.  [**名前**] に [ **Supplier name** ] を選択します。  
  
    7.  [ **OK** ] をクリックしてエンティティを作成し、ダイアログボックスを閉じます。  
  
18. **Excel**を閉じ、ファイルを**保存しません**。  
  
19. **マスターデータマネージャー**で、インターネットブラウザーを更新し、 **Supplier**エンティティが一覧に表示されていることを確認します。  
  
20. 上部にある**SQL Server 2012 マスターデータサービス**をクリックして、**ホームページ**に切り替えます。  
  
21. [**モデル**] に [**仕入先**モデル] が選択されており、[**バージョン**] に [ **VERSION_1** ] が選択されていることを確認  
  
22. 
  **[エクスプローラー]** をクリックします。 すべての属性を持つ**Supplier**エンティティが、**値なし**で作成されていることに注意してください。  
  
## <a name="next-step"></a>次のステップ  
 [タスク 2 &#40;オプションの&#41;: マスターデータマネージャーを使用した MDS サブスクリプションビューの作成](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
