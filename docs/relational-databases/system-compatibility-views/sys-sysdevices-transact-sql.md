---
title: sys. sysdevices (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdevices
- sysdevices_TSQL
- sys.sysdevices
- sys.sysdevices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdevices compatibility view
- sysdevices system table
ms.assetid: ac5bcaf4-8fb6-4855-8856-d7643f469361
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cbd14a7ce8dd1cfb1571874a83a615065200014
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053523"
---
# <a name="syssysdevices-transact-sql"></a>sys. sysdevices (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディスクバックアップファイル、テープバックアップファイル、およびデータベースファイルごとに1行のデータを格納します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|バックアップ ファイルまたはデータベース ファイルの論理名。|  
|**幅**|**int**|ファイルのサイズ (2 kb ページ単位)。|  
|**低画質**|**int**|旧バージョンとの互換性のためにだけ用意されています。|  
|**高い**|**int**|旧バージョンとの互換性のためにだけ用意されています。|  
|**オンライン**|**smallint**|デバイスの種類を示すビットマップ:<br /><br /> 1 = 既定のディスク<br /><br /> 2 = 物理ディスク<br /><br /> 4 = 論理ディスク<br /><br /> 8 = ヘッダーをスキップ<br /><br /> 16 = バックアップファイル<br /><br /> 32 = シリアル書き込み<br /><br /> 4096 = 読み取り専用|  
|**cntrltype**|**smallint**|コントローラーの種類:<br /><br /> 0 = CD-ROM 以外のデータベースファイル<br /><br /> 2 = ディスクバックアップファイル<br /><br /> 3-4 = フロッピーディスクバックアップファイル<br /><br /> 5 = テープバックアップファイル<br /><br /> 6 = 名前付きパイプファイル|  
|**phyname**|**nvarchar (260)**|物理ファイルの名前。|  
  
## <a name="see-also"></a>参照  
 [システムビューへのシステムテーブルのマッピング &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-sql&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
