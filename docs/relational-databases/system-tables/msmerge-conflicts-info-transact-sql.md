---
title: MSmerge_conflicts_info (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_conflicts_info_TSQL
- MSmerge_conflicts_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_conflicts_info system table
ms.assetid: 6b76ae96-737a-4000-a6b6-fcc8772c2af4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7629bff37fb33080f8057fc1799437fff182882f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68044803"
---
# <a name="msmerge_conflicts_info-transact-sql"></a>MSmerge_conflicts_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_conflicts_info**テーブルは、サブスクリプションをマージパブリケーションと同期するときに発生する競合を追跡します。 競合している行データの損失は、競合が発生したアーティクルの[MSmerge_conflict_publication_article](../../relational-databases/system-tables/msmerge-conflict-publication-article-transact-sql.md)テーブルに格納されます。 このテーブルは、パブリッシャー側のパブリケーションデータベースに格納され、サブスクライバー側のサブスクリプションデータベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|パブリッシュされたテーブルのニックネーム。|  
|**rowguid**|**UNIQUEIDENTIFIER**|競合している行の識別子です。|  
|**origin_datasource**|**nvarchar(255)**|競合している変更が発生したデータベースの名前です。|  
|**conflict_type**|**int**|発生した競合の種類。次のいずれかを指定できます。<br /><br /> **1** = 更新の競合: 行レベルで競合が検出されます。<br /><br /> **2** = 列更新の競合: 列レベルで競合が検出されました。<br /><br /> **3** = 更新の削除 Wins の競合: 削除によって競合が優先されます。<br /><br /> **4** = 更新 Wins 削除の競合: 競合が失われた削除済みの rowguid がこのテーブルに記録されます。<br /><br /> **5** = 挿入のアップロードに失敗しました: サブスクライバーからの挿入をパブリッシャーで適用できませんでした。<br /><br /> **6** = ダウンロードの挿入に失敗しました: パブリッシャーからの挿入をサブスクライバーで適用できませんでした。<br /><br /> **7** = 削除のアップロードに失敗しました: サブスクライバーでの削除をパブリッシャーにアップロードできませんでした。<br /><br /> **8** = 削除のダウンロードに失敗: パブリッシャーでの削除をサブスクライバーにダウンロードできませんでした。<br /><br /> **9** = 更新のアップロードに失敗しました: サブスクライバーでの更新をパブリッシャーで適用できませんでした。<br /><br /> **10** = 更新のダウンロードに失敗しました: パブリッシャーでの更新をサブスクライバーに適用できませんでした。<br /><br /> **11** = 解決策<br /><br /> **12** = 論理レコードの更新による Wins の削除: 競合が失われた削除された論理レコードがこのテーブルに記録されます。<br /><br /> **13** = 論理レコードの競合の挿入更新: 論理レコードへの挿入が更新と競合しています。<br /><br /> **14** = 論理レコードの削除 Wins 更新の競合: 競合が失われる更新された論理レコードがこのテーブルに記録されます。|  
|**reason_code**|**int**|状況に依存する可能性があるエラーコード。 更新-更新および更新-削除の競合の場合、この列に使用される値は**conflict_type**と同じになります。 ただし、失敗した変更の競合については、理由コードは、マージエージェントが変更を適用できない原因となったエラーです。 たとえば、主キー違反のためにマージエージェントがサブスクライバーで挿入を適用できない場合、6の**conflict_type** ("download insert failed") と2627の**reason_code**がログに記録されます。これ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、主キー違反の内部エラーメッセージです。 "% ls 制約 '%. * ls ' の違反です。 オブジェクト '% には重複するキーを挿入できません。\*ls '. "|  
|**reason_text**|**nvarchar (720)**|状況に依存する可能性があるエラーの説明。|  
|**pubid**|**UNIQUEIDENTIFIER**|パブリケーションの識別子。|  
|**MSrepl_create_time**|**DATETIME**|競合が発生した時刻。|  
|**origin_datasource_id**|**UNIQUEIDENTIFIER**|競合する変更が発生したデータベースの識別子。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
