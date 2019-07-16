---
title: SQL Server Management Studio (SSMS) のハングまたはクラッシュをトラブルシューティングする
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: dnethi
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
manager: jroth
ms.custom: ''
ms.date: 07/01/2019
ms.openlocfilehash: 424b0863da9d0d2cfb56676bed5c368efc4d9349
ms.sourcegitcommit: 0b0f5aba602732834c8439c192d95921149ab4c3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67501189"
---
# <a name="get-diagnostic-data-after-a-sql-server-management-studio-ssms-crash"></a>SQL Server Management Studio (SSMS) がクラッシュした後に診断データを取得する

[!INCLUDE[適用対象](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)

## <a name="get-full-memory-dump-of-sql-server-management-studio-ssms-when-it-hangs-or-crashes"></a>SQL Server Management Studio (SSMS) がハングまたはクラッシュしたときに、その完全メモリ ダンプを取得する

SSMS のクラッシュまたはハングをトラブルシューティングするために診断情報を取得するには、以下の手順を行います。

1. [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) をダウンロードします。

2. ダウンロードしたものをフォルダーに解凍します。

3. コマンド プロンプトを開き、次のコマンドを実行します。

    ```command prompt
    <PathToProcDumpFolder>\procdump.exe -e -h -ma -w ssms.exe
    ```

    使用許諾契約書に同意するように求められた場合は、 *[同意する]* を選択します。

4. SQL Server Management Studio をまだ起動していない場合は起動します。

5. 問題を再現します。

6. ダンプ ファイルの書き込みに関する cmd プロンプトにテキストが表示されるはずです。書き込みが完了するまで待ちます。

7. 新しいフォルダーを作成し、そのフォルダーに書き込む *.dmp ファイルをコピーします。

8. 次のファイルを同じフォルダーにコピーします。

    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"
    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"
    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. フォルダーを圧縮します。

## <a name="user-content-get-full-memory-dump-of-ssms-when-it-throws-an-outofmemoryexception"></a>SSMS が OutOfMemoryException をスローしたときに、その完全メモリ ダンプを取得する

マネージド例外ならば完全メモリ ダンプを取得できます。

SSMS の OutOfMemoryException をトラブルシューティングするために診断情報を取得するには、以下の手順を行います。

1. [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) をダウンロードします。

2. ダウンロードしたものをフォルダーに解凍します。

3. コマンド プロンプトを開き、次のコマンドを実行します。

    ```command prompt
    <PathToProcDumpFolder>\procdump.exe -e 1 -f System.OutOfMemoryException -ma -w ssms.exe
    ```

    使用許諾契約書に同意するように求められた場合は、 *[同意する]* を選択します。

4. SQL Server Management Studio をまだ起動していない場合は起動します。

5. 問題を再現します。

6. ダンプ ファイルの書き込みに関する cmd プロンプトにテキストが表示されるはずです。書き込みが完了するまで待ちます。

7. 新しいフォルダーを作成し、そのフォルダーに書き込む *.dmp ファイルをコピーします。

8. 次のファイルを同じフォルダーにコピーします。

    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. フォルダーを圧縮します。