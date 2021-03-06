---
title: '[バックアップ デバイス] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdevice.general.f1
ms.assetid: c557e37d-319e-4adb-a0c1-94189b15d2ac
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7a4f23fd3d6d8208410c520676ee4e0c8bbe00fd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62922143"
---
# <a name="backup-device-general-page"></a>[バックアップ デバイス] ([全般] ページ)
  **[全般**] ページを使用して、論理バックアップデバイスの全般プロパティを指定または表示します。  
  
 **SQL Server Management Studio を使用してバックアップデバイスの内容を表示するには**  
  
-   [バックアップテープまたはファイル &#40;SQL Server の内容を表示&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [論理バックアップデバイスのプロパティと内容を表示 &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>オプション  
 **デバイス名**  
 既存の論理バックアップ デバイスの名前を表示するか、新しい論理バックアップ デバイスの名前を指定します。  
  
 **テープ**  
 
  **[テープ]** の一覧からバックアップ先テープ デバイスを表示したり、選択したりします。 このオプションは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスを実行しているコンピューターにテープドライブが接続されている場合にのみ使用できます。  
  
> [!NOTE]  
>  リモート コンピューターのテープ バックアップ デバイスは、有効なバックアップ先ではありません。  
  
 **拡張子**  
 既存の論理バックアップ デバイスのバックアップ先ファイルを表示するか、新しい論理バックアップ デバイスのバックアップ先ファイルを指定します。  
  
-   既存の論理バックアップ デバイスを使用する場合、バックアップ ファイルのパスが表示されます。 
  **[ファイル]** フィールドは編集できません。また、参照ボタンは使用できません。  
  
-   新しい論理バックアップ デバイスでは、論理バックアップ デバイスを定義しているバックアップ ファイルのパスを設定する必要があります。 このファイルは、まだ存在していなくてもかまいません。  
  
     ローカル バックアップ ファイルを指定するには、 **[ファイル]** ボックスの右の参照ボタンをクリックできます。 その後、 **[データベース ファイルの検索]** ダイアログ ボックスを使用して、サーバー インスタンスを実行しているコンピューターの固定ドライブの任意の場所に移動できます。 バックアップ ファイルが存在しない場合、ダイアログ ボックスの **[ファイル名]** に使用するファイル名を入力する必要があります。  
  
     
  **[ファイル]** を手動で編集して、既定のパス、ファイル名、および拡張子をオーバーライドすることもできます。 バックアップ先としてリモート ファイルを指定するには、完全修飾の汎用名前付け規則 (UNC) 名を入力してください。 詳細については、「 [バックアップ デバイス &#40;SQL Server&#41;](backup-devices-sql-server.md)」を参照してください。  
  
    > [!IMPORTANT]  
    >  ネットワークを経由してデータをバックアップすると、ネットワーク エラーが発生する可能性があります。バックアップ終了後にバックアップ操作を確認することをお勧めします。 詳細については、「[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)」をご覧ください。  
  
## <a name="remarks"></a>解説  
 単一または一連のバックアップ デバイス上にあるバックアップによって、1 つのメディア セットが構成されます。 
  *メディア セット* とは、テープやディスク ファイルなどのバックアップ メディアに順番を付けてまとめたものです。バックアップ メディアには、1 回以上のバックアップ操作によって、固定型の複数のバックアップ デバイスを使用して書き込まれます。 メディア セットの詳細については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。  
  
 論理バックアップ デバイスに対応している物理バックアップ デバイスは、メディア セットの最初のバックアップを論理バックアップ デバイスに書き込むときに初期化されます。 物理バックアップ デバイスが、まだ存在していないファイルの場合は、この時点で作成されます。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [ディスクファイル &#40;SQL Server の論理バックアップデバイスを定義&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [テープドライブ &#40;SQL Server の論理バックアップデバイスを定義&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [バックアップ先としてディスクまたはテープを指定 &#40;SQL Server&#41;](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [バックアップデバイス &#40;SQL Server を削除&#41;](delete-a-backup-device-sql-server.md)  
  
-   [バックアップ &#40;SQL Server の有効期限を設定する&#41;](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [バックアップテープまたはファイル &#40;SQL Server の内容を表示&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [バックアップセット &#40;SQL Server のデータファイルとログファイルを表示&#41;](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [論理バックアップデバイスのプロパティと内容を表示 &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [デバイスからバックアップを復元 &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [バックアップデバイス &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [メディアセット、メディアファミリ、およびバックアップセット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
