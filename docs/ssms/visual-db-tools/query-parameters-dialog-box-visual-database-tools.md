---
title: '[クエリ パラメーター] ダイアログ ボックス'
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 05e99d2fc2365ab39b68ad6211889047a1564113
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75255368"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>[クエリ パラメーター] ダイアログ ボックス (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
このダイアログ ボックスを使用すると、クエリに定義されたパラメーターの値を入力できます。 このダイアログ ボックスは、エンド ユーザーが値を入力する必要があるパラメーターを含むクエリを実行するときに表示されます。  
  
## <a name="options"></a>オプション  
**名前**  
実行するクエリに対して定義されているパラメーターを一覧表示します。 クエリに名前付きのパラメーターが含まれる場合は、名前が表示されます。 クエリに名前のないパラメーターが含まれる場合、クエリ内のパラメーターごとに、システム定義のパラメーター名が一覧表示されます。  
  
**Value**  
**[名前]** に一覧表示された各パラメーターの値を入力します。 最後に使用した値が既定の値として表示されます。  
  
## <a name="example"></a>例  
SQL ペインに入力された次のクエリが [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースで実行されると、[クエリ パラメーター] ダイアログ ボックスが開きます。  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a>参照  
[パラメーターを使用したクエリ (Visual Database Tools)](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
  
