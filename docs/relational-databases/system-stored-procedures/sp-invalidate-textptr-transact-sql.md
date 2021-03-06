---
title: sp_invalidate_textptr (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_invalidate_textptr_TSQL
- sp_invalidate_textptr
dev_langs:
- TSQL
helpviewer_keywords:
- sp_invalidate_textptr
ms.assetid: dd9920e1-7064-4c05-93d8-9303103fa1d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 81df88f6e451d71dc5778e49162db97def7ed27d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68113192"
---
# <a name="sp_invalidate_textptr-transact-sql"></a>sp_invalidate_textptr (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定された行内テキストポインター、またはトランザクション内のすべての行内テキストポインターを無効にします。 **sp_invalidate_textptr**は行内テキストポインターに対してのみ使用できます。 これらのポインターは、 **text in row**オプションが有効になっているテーブルからのものです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_invalidate_textptr [ [ @TextPtrValue = ] textptr_value ]  
```  
  
## <a name="arguments"></a>引数  
`[ @TextPtrValue = ] textptr_value`無効にする行内テキストポインターを指定します。 *textptr_value*は**varbinary (** 16 **)**,、既定値は NULL です。 NULL の場合、 **sp_invalidate_textptr**はトランザクション内のすべての行内テキストポインターを無効にします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、各データベースの各トランザクションに、アクティブで有効な行内テキスト ポインターを 1,024 個まで使用できます。ただし、複数のデータベースにまたがるトランザクションの場合は、各データベースに行内テキスト ポインターを 1,024 個まで使用できます。 **sp_invalidate_textptr**を使用して行内テキストポインターを無効にしたり、行内テキストポインターを追加するために空き領域を使用したりできます。  
  
 
  text in row オプションの詳細については、「[sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 **Public**ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースエンジン](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_tableoption &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)   
 [TEXTPTR &#40;Transact-sql&#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)   
 [TEXTVALID &#40;Transact-sql&#41;](../../t-sql/functions/text-and-image-functions-textvalid-transact-sql.md)  
  
  
