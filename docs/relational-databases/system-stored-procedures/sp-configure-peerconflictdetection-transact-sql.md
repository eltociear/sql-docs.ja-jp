---
title: sp_configure_peerconflictdetection (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_configure_peerconflictdetection_TSQL
- sp_configure_peerconflictdetection
helpviewer_keywords:
- sp_configure_peerconflictdetection
ms.assetid: 45117cb2-3247-433f-ba3d-7fa19514b1c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8a8cc9930ddf85dea60999e3b63dbcebaaf42d8f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68215941"
---
# <a name="sp_configure_peerconflictdetection-transact-sql"></a>sp_configure_peerconflictdetection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ピアツーピアトランザクションレプリケーショントポロジに関係するパブリケーションの競合検出を構成します。 詳細については、「 [ピア ツー ピア レプリケーションにおける競合検出](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」を参照してください。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_configure_peerconflictdetection [ @publication = ] 'publication'  
    [ , [ @action = ] 'action']  
    [ , [ @originator_id = ] originator_id ]  
    [ , [ @conflict_retention = ] conflict_retention ]  
    [ , [ @continue_onconflict = ] 'continue_onconflict']  
    [ , [ @local = ] 'local']  
    [ , [ @timeout = ] timeout ]  
  
```  
  
## <a name="arguments"></a>引数  
 [ @publication=]'*publication*'  
 競合検出を構成するパブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
 [ @action= ]'*action*'  
 パブリケーションの競合検出を有効にするか無効にするかを指定します。 *アクション*は**nvarchar (5)**,、値は次のいずれかを指定することができます。  
  
|値|[説明]|  
|-----------|-----------------|  
|**を**|パブリケーションの競合検出を有効にします。|  
|**切り替える**|パブリケーションの競合検出を無効にします。|  
|NULL (既定値)||  
  
 [ @originator_id= ]*originator_id*  
 ピア ツー ピア トポロジ内のノードの ID を指定します。 *originator_id*は**int**,、既定値は NULL です。 *アクション*が**有効**に設定されている場合、この ID は競合検出に使用されます。 トポロジで使用されていないゼロ以外の正の ID を指定してください。 既に使用されている ID を確認するには、 [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) システム テーブルに対してクエリを実行します。  
  
 [ @conflict_retention= ]*conflict_retention*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @continue_onconflict= ]'*continue_onconflict*']  
 競合が検出された後もディストリビューションエージェントが変更を処理するかどうかを決定します。 *continue_onconflict*は**nvarchar (5)** で、既定値は FALSE です。  
  
> [!CAUTION]  
>  既定値の FALSE を使用することをお勧めします。 このオプションが TRUE に設定されている場合、ディストリビューションエージェントは、発信元 ID が最も大きいノードから競合する行を適用してトポロジ内のデータを収束しようとします。 この方法では、収束は保証されません。 競合が検出された後、トポロジが一貫していることを確認する必要があります。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」の「競合の処理」を参照してください。  
  
 [ @local= ]'*local*'  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @timeout= ]*タイムアウト*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_configure_peerconflictdetection は、ピア ツー ピア トランザクション レプリケーションで使用されます。 競合検出を使用するには、すべての[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]ノードが以降のバージョンを実行している必要があります。すべてのノードに対して検出を有効にする必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 Sysadmin 固定サーバーロールまたは db_owner 固定データベースロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [ピア ツー ピア レプリケーションにおける競合検出](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [ピアツーピアトランザクションレプリケーション](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [レプリケーションストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
