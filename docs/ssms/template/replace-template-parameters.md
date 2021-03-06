---
title: '[テンプレート パラメーターの置換]'
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.templates.replaceparameters.f1
helpviewer_keywords:
- template parameters [Template Explorer]
- templates [Transact-SQL], replacing parameters
- Replace (Query) Template Parameters dialog box
- replacing template parameters
ms.assetid: 1234aa14-3464-4a3e-922a-5cfb8fb23627
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b0c4cc26fddff13e388b74593aa9d8f9331359f8
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75245682"
---
# <a name="replace-template-parameters"></a>[テンプレート パラメーターの置換]
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
テンプレートには、テンプレートを使用するたびに実装固有の値に置き換えることができるパラメーターが含まれています。 コード エディターでテンプレートを開いた後、パラメーターを実装に関する値に置き換えることができます。  
  
## <a name="before-you-begin"></a>はじめに  
**[テンプレート パラメーターの値の指定]** ダイアログは、3 つの列を含むグリッドです。 **[パラメーター]** 列と **[種類]** 列は読み取り専用であり、変更できません。 **[値]** 列の内容を確認し、既定値を実装に応じた値に変更します。  
  
このダイアログ ボックスを使用するには、スクリプトに山かっこ (`< >`) で囲んだパラメーターを `<`*parameter_name*`,` *data_type*`,` *default_value*`>`の形式で含める必要があります。  
  
## <a name="replace-template-parameters"></a>[テンプレート パラメーターの置換]  
コード エディター ウィンドウでテンプレートを開いた後、次の操作を行います。  
  
1.  **[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** をクリックします。  
  
2.  **[テンプレート パラメーターの値の指定]** ダイアログ ボックスの **[値]** 列には、各パラメーターの推奨値が表示されます。 推奨値をそのまま使用するか、または別の値を入力します。  
  
3.  **[OK]** をクリックして **[テンプレート パラメーターを置き換える]** ダイアログ ボックスを閉じ、クエリ エディターでスクリプトを変更します。  
  
## <a name="see-also"></a>参照  
[テンプレート エクスプローラー](../../ssms/template/template-explorer.md)  
[テンプレートを開く](../../ssms/template/open-a-template.md)  
  
