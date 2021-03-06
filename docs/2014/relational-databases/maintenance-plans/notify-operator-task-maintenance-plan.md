---
title: '[オペレーターへの通知タスク] (メンテナンス プラン) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.notifyoperator.f1
helpviewer_keywords:
- Notify Operator Task dialog box
ms.assetid: 39c0797c-ad2b-4591-85c9-a23a7f902895
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0ef94ed9e296c588b70789ace0bbbbe79bc8008f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68205967"
---
# <a name="notify-operator-task-maintenance-plan"></a>[オペレーターへの通知タスク] (メンテナンス プラン)
  
  **[オペレーターへの通知タスク]** ダイアログ ボックスを使用すると、このメンテナンス プランに自動通知を追加できます。 このタスクを使用するにはデータベースメールが有効になっていて、MSDB がメールホストデータベースとし[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]て正しく構成されていること、および有効な電子メールアドレスを持つエージェントオペレーターを持っていることが必要です。  
  
 このタスクでは、sp_notify_operator ストアド プロシージャを使用します。  
  
## <a name="options"></a>オプション  
 **接続**  
 このタスクを実行するときに使用するサーバー接続を選択します。  
  
 **[新規作成]**  
 このタスクを実行するときに使用する新しいサーバー接続を作成します。 
  **[新しい接続]** ダイアログ ボックスについては、後で説明します。  
  
 **通知するオペレーター**  
 電子メールの受信者を指定します。  
  
 **通知メッセージの件名**  
 通知メッセージの件名に含めるテキストを指定します。  
  
 **通知メッセージの本文**  
 通知メッセージの本文に含めるテキストを指定します。  
  
 **T-sql の表示**  
 選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。  
  
> [!NOTE]  
>  影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。  
  
## <a name="new-connection-dialog-box"></a>[新しい接続] ダイアログ ボックス  
 **接続名**  
 新しい接続の名前を入力します。  
  
 **サーバー名の選択または入力**  
 このタスクを実行するときに接続するサーバーを選択します。  
  
 **[更新]**  
 使用できるサーバーの一覧を表示します。  
  
 **サーバーにログオンするための情報を入力します**  
 サーバーの認証情報を指定します。  
  
 **Windows 統合セキュリティを使用する**  
 Windows 認証を使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)]してのインスタンスに接続します。  
  
 **特定のユーザー名とパスワードを使用する**  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。 このオプションは利用できません。  
  
 **ユーザー名**  
 認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。 このオプションは利用できません。  
  
 **パスワード**  
 認証に使用するパスワードを指定します。 このオプションは利用できません。  
  
## <a name="see-also"></a>参照  
 [データベース メール](../database-mail/database-mail.md)   
 [sp_notify_operator &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)  
  
  
