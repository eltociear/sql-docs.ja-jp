---
title: バックアップサーバーの容量計画
description: この容量計画ワークシートは、並列データウェアハウスデータベースのバックアップ操作と復元操作を実行するためのバックアップサーバーの要件を決定するのに役立ちます。 これを使用して、既存のバックアップサーバーを新規購入またはプロビジョニングするためのプランを作成します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 46dbdded5adf41a847f017cf4ee203597df13962
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401344"
---
# <a name="backup-server-capacity-planning-worksheet---parallel-data-warehouse"></a>Backup server キャパシティプランニングワークシート-並列データウェアハウス
この容量計画ワークシートは、SQL Server PDW データベースのバックアップ操作と復元操作を実行するためのバックアップサーバーの要件を決定するのに役立ちます。 これを使用して、既存のバックアップサーバーを新規購入またはプロビジョニングするためのプランを作成します。  
  
このワークシートは、「[バックアップサーバーの取得と構成](acquire-and-configure-backup-server.md)」の手順を補足するものです。  
  
## <a name="capacity-planning-worksheet-for-backup-servers"></a>バックアップサーバーの容量計画ワークシート  

### <a name="notes"></a>メモ  
  
1.  このワークシートは、PDW データベースのバックアップ操作と復元操作を実行するサーバーに適用されます。  
  
2.  PDW データベースをバックアップおよび復元する唯一の方法は、BACKUP DATABASE と RESTORE DATABASE SQL コマンドを使用することです。 ただし、バックアップサーバーにバックアップデータがある場合は、一連の Windows ファイルとして存在します。 従来の Windows ファイルベースのバックアップ方法を使用して、バックアップファイルをサーバーから別の記憶域の場所にアーカイブできます。  
  
### <a name="clipboard-iconmediaclipboard-iconpng-clipboard-icon-capacity-planning-worksheet"></a>![クリップボードアイコン](media/clipboard-icon.png "クリップボードアイコン")容量計画ワークシート 
  
このワークシートを印刷し、独自の要件を入力します。  
  
|コンポーネント|要件|この列に独自の要件を入力してください|Recommendations|  
|-------------|---------------|--------------------------------------------------|-------------------|  
|ストレージ|指定した期間にバックアップサーバーに格納する最大バイト数。|![鉛筆アイコン](media/pencil-icon.png "鉛筆アイコン")|記憶域の要件を決定するには、特定の期間にバックアップサーバーに格納するデータ量を確認します。<br /><br />バックアップデータは、バックアップサーバーの圧縮形式で保存されます。 データ圧縮率は、データの特性によって異なります。<br /><br />たとえば、大まかな見積もりとして、圧縮されていないデータのサイズに対して、7:1 の圧縮率を見積もることをお勧めします。 これは、少なくとも80% のデータがクラスター化列ストアインデックスに格納されていることを前提としています。 たとえば、データベースに 700 GB の非圧縮データがあり、クラスター化列ストアインデックスに格納されている場合、データベースバックアップに約 100 GB が必要であると推定できます。<br /><br />バックアップサーバーにデータベースバックアップのコピーを複数作成する場合は、それらを考慮する必要があります。<br /><br />たとえば、それぞれに 5 TB の非圧縮データが含まれている10個のデータベースをバックアップする場合、データベースのサイズは 50 TB になります。 これら10個のデータベースを毎日毎日5日間バックアップする予定の場合、圧縮されていない合計サイズは 250 TB になります。 7:1 の圧縮率を考慮すると、バックアップサーバーに 250/7 = 35.7 TB のストレージが必要になります。 変動と成長に対応するために、控えめにして30% の追加容量を取得することをお勧めします。  この例では、46.6 TB の方が適しています。|  
|ネットワーク|ネットワーク接続の種類。|![鉛筆アイコン](media/pencil-icon.png "鉛筆アイコン")|負荷率の要件を満たすのに最適なネットワーク接続の種類を決定します。<br /><br />たとえば、InfiniBand または10Gbit ビットイーサネットでは、最適な読み込み速度が提供されます。 1ギガビットイーサネットでは、負荷率が1時間あたり 360 GB に制限されます。|  
|I/O|書き込みの1時間あたりのバイト数。|![鉛筆アイコン](media/pencil-icon.png "鉛筆アイコン")|ディスクにバックアップを書き込む場合は、1時間あたり 4 TB の書き込み速度が最適です。<br /><br />たとえば、50 MB/秒の書き込みが可能なドライブの場合は、少なくとも24台のドライブが必要であり、さらにミラーリングまたはパリティが必要です。<br /><br />I/o 容量については、読み込み中のサーバーで発生したすべての i/o を考慮してください。 ETL サーバーからのデータファイルの受信など、読み込みサーバーにデータの読み込みに加えて他の i/o トラフィックがある場合は、i/o の要件が増加します。|  
|CPU|ソケットの数。|![鉛筆アイコン](media/pencil-icon.png "鉛筆アイコン")|バックアップファイルの受信と保存は、CPU を集中的に消費するアプリケーションではありません。  最小要件として、最近製造された2ソケットサーバーを使用することをお勧めします。|  
|RAM|読み込み中に Windows がファイルをキャッシュできるようにするメモリ容量 (GB)。|![鉛筆アイコン](media/pencil-icon.png "鉛筆アイコン")|バックアップファイルを受信して格納するには、読み込みサーバーの RAM がほとんど必要ありません。<br /><br />RAM の要件を確認するには、Windows Server のインストールとサードパーティ製のアプリケーションの要件を参照してください。 他のソースからの要件がない場合は、少なくとも 32 GB をお勧めします。|  
  
容量の要件の決定が完了したら、「[読み込みサーバーの取得と構成](acquire-and-configure-loading-server.md)」トピックに戻り、購入を計画します。  
  
## <a name="see-also"></a>参照  
[ハードウェアのバックアップと読み込み](backup-and-loading-hardware.md)  
  
