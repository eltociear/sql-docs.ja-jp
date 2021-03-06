---
title: fn_translate_permissions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_translate_permissions
- sys.fn_translate_permissions_TSQL
- fn_translate_permissions
- fn_translate_permissions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- permissions bitmask [SQL Server]
- sys.fn_translate_permissions function
- fn_translate_permissions function
ms.assetid: ac97121f-2bd0-4f71-8e45-42c8584edbc5
author: rothja
ms.author: jroth
ms.openlocfilehash: c08fd2235750a8a7be99b5290813331141ddf0de
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68055375"
---
# <a name="sysfn_translate_permissions-transact-sql"></a>sys.fn_translate_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  SQL トレースによって返されるアクセス許可のビットマスクを権限名のテーブルに変換します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_translate_permissions ( level , perms )  
```  
  
## <a name="arguments"></a>引数  
 *平準*  
 権限が適用されるセキュリティ保護可能なリソースの種類を指定します。 *レベル*は**nvarchar (60)** です。  
  
 *perms*  
 権限列に返されるビットマスクを指定します。 *perms*は**varbinary (16)** です。  
  
## <a name="returns"></a>戻り値  
 **一覧**  
  
## <a name="remarks"></a>解説  
 SQL トレースの**permissions**列に返される値は、有効な権限を計算するためにに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]よって使用されるビットマスクを整数で表したものです。 25種類の securables にはそれぞれ、対応する数値を持つ独自のアクセス許可セットがあります。 **fn_translate_permissions**は、このビットマスクを権限名のテーブルに変換します。  
  
## <a name="permissions"></a>アクセス許可  
 **Public**ロールのメンバーシップが必要です。  
  
## <a name="example"></a>例  
 次のクエリで`sys.fn_builtin_permissions`は、を使用して、証明書に適用さ`sys.fn_translate_permissions`れるアクセス許可を表示し、を使用してアクセス許可のビットマスクの結果を返します。  
  
```  
SELECT * FROM sys.fn_builtin_permissions('CERTIFICATE');  
SELECT '0001' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0001);  
SELECT '0010' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0010);  
SELECT '0011' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0011);  
```  
  
## <a name="see-also"></a>参照  
 [アクセス許可 &#40;データベースエンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [server_permissions &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)   
 [database_permissions &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)  
  
  
