---
title: カスタムレポートアイテムがレポートサーバーで検出されました (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- custom report items, upgrading
ms.assetid: aee32006-65b2-4dfe-9570-d85a249d17b2
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 5788b94356ec887b8c83850a4cb2c47d34b7388f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952282"
---
# <a name="custom-report-items-were-detected-on-the-report-server-upgrade-advisor"></a>カスタム レポート アイテムがレポート サーバーで検出された (アップグレード アドバイザー)
  以前の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]リリースの用に作成されたカスタムレポートアイテムは[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、と互換性がありません。 アップグレードを続行できますが、そのカスタム レポート アイテムを使用するレポートは想定どおりに実行されません。 アップグレード アドバイザーによって、カスタム レポート アイテムが検出されました。 アップグレードを続行できますが、アップグレードの完了後、カスタム レポート アイテム ファイルを新しいインストール フォルダーに手動で移動する必要があります。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>[説明]  
 アップグレード アドバイザーによって、構成ファイル内にカスタム [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 拡張設定が検出されました。これは、レポート用のカスタム アセンブリが 1 つ以上インストールに含まれていることを示しています。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードの完了後、カスタム レポート アイテム ファイルを新しいインストール フォルダーに手動で移動します。  
  
## <a name="see-also"></a>参照  
 [アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
