---
title: CLR 統合の有効化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1cb5f1f4bcc3a3e796cc99b4da7f14e5a5976b93
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62874100"
---
# <a name="enabling-clr-integration"></a>CLR 統合の有効化
  CLR (共通言語ランタイム) 統合機能は既定では無効になっているので、CLR 統合を使用して実装されるオブジェクトを使用するには、この機能を有効にする必要があります。 CLR 統合を有効にするには、 **sp_configure**ストアドプロシージャの**clr enabled**オプションを使用します。  
  
```  
  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 Clr の統合を無効にするには、 **clr enabled**オプションを0に設定します。 CLR 統合を無効にすると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ではすべての CLR ルーチンの実行が停止され、すべてのアプリケーション ドメインがアンロードされます。  
  
> [!NOTE]  
>  CLR 統合を有効にするには、 **sysadmin**固定サーバーロールおよび**serveradmin**固定サーバーロールのメンバーによって暗黙的に保持される ALTER SETTINGS サーバーレベル権限が必要です。  
  
> [!NOTE]  
>  コンピューターを構成しているメモリ サイズとプロセッサ数が非常に大きい場合、SQL Server の CLR 統合機能をサーバーの起動時に読み込めないことがあります。 この問題に対処するには、 **-gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サービスのスタートアップオプションを使用してサーバーを起動し、十分な大きさのメモリ値を指定します。 詳細については、「 [データベース エンジン サービスのスタートアップ オプション](../../database-engine/configure-windows/database-engine-service-startup-options.md)」を参照してください。  
  
> [!NOTE]  
>  簡易プーリングでは、共通言語ランタイム (CLR) の実行はサポートされていません。 CLR 統合を有効にする前に、簡易プーリングを無効にする必要があります。 詳細については、「 [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [clr enabled サーバー構成オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [GRANT &#40;Transact-sql&#41;](/sql/t-sql/statements/grant-transact-sql)   
 [サーバーレベルのロール](../security/authentication-access/server-level-roles.md)  
  
  
