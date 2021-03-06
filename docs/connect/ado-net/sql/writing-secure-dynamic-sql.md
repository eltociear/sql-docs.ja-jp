---
title: SQL Server での安全な動的 SQL の作成
description: ストアド プロシージャを使用して、安全な動的 SQL を作成する方法について説明します。
ms.date: 09/26/2019
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 22d64b260d8d700afc8ed354d87de730e8c3b21f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75253370"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>SQL Server での安全な動的 SQL の作成

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET をダウンロードする](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL インジェクションとは、悪意のあるユーザーが有効な入力の代わりに Transact-SQL ステートメントを入力するプロセスです。 入力が検証されずにサーバーに直接渡され、挿入されたコードがアプリケーションによって誤って実行された場合に、この攻撃によってデータが破損、または破壊される可能性があります。  
  
SQL Server では、構文的に有効であれば受信したクエリがすべて実行されるため、SQL ステートメントを構成するすべてのプロシージャにおいて、インジェクションに対する脆弱性を検証する必要があります。 高いスキルを持つ決然たる攻撃者は、パラメーター化されたデータであっても操作できるのです。 動的 SQL を使用する場合は、必ずコマンドをパラメーター化し、パラメーター値をクエリ文字列に直接含めないようにしてください。  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>SQL インジェクション攻撃の構造  
インジェクション プロセスは、途中でテキスト文字列を終了し、新しいコマンドを追加することによって行われます。 挿入されたコマンドが実行される前に別の文字列が追加される可能性があるため、攻撃者は挿入する文字列をコメント記号 "--" で終了させます。 後続のテキストは実行時には無視されます。 セミコロン (;) 区切り記号を使用して複数のコマンドを挿入できます。  
  
挿入された SQL コードが構文的に正しい限り、改ざんをプログラムによって検出するのは不可能です。 このため、すべてのユーザー入力を検証し、使用しているサーバーで作成された SQL コマンドを実行するコードを注意深く確認する必要があります。 検証されていないユーザー入力は連結しない。 文字列の連結は、スクリプト インジェクションを行うための主なポイントとなります。  
  
有用なガイドラインを次に示します。  
  
- Transact-SQL ステートメントをユーザー入力から直接作成しないでください。ストアド プロシージャを使用して、ユーザー入力を検証します。  
  
- 型、長さ、形式、範囲をテストすることでユーザー入力を必ず検証してください。 Transact-SQL QUOTENAME() 関数を使用してシステム名をエスケープするか、REPLACE() 関数して文字列内の任意の文字をエスケープします。  
  
- アプリケーションの各層に複数の検証レイヤーを実装します。  
  
- 入力のサイズとデータ型をテストし、適切な制限を適用する。 これは、意図的なバッファー オーバーランを防ぐのに役立ちます。  
  
- 文字列変数の内容をテストし、予測される値のみを受け入れる。 バイナリ データ、エスケープ シーケンス、およびコメント文字を含む入力は拒否します。  
  
- XML ドキュメントを扱う場合、入力時にすべてのデータをスキーマに照らして検証する。  
  
- 多層環境では、信頼関係ゾーンへ入る前にすべてのデータを検証する必要がある。  
  
- ファイル名の作成に使用できるフィールドでは、次の文字列を受け付けない:AUX、CLOCK$、COM1 から COM8、CON、CONFIG$、LPT1 から LPT8、NUL、PRN。  
  
- ストアド プロシージャおよびコマンドで <xref:Microsoft.Data.SqlClient.SqlParameter> オブジェクトを使用して、型チェックと長さの検証を行います。  
  
- クライアント コードで <xref:System.Text.RegularExpressions.Regex> 式を使用して、無効な文字をフィルター処理します。  
  
## <a name="dynamic-sql-strategies"></a>動的 SQL 戦略  
手続き型コードで動的に作成された SQL ステートメントを実行すると、所有権の継承が切断され、SQL Server によって、動的 SQL でアクセスされるオブジェクトに対する呼び出し元のアクセス許可がチェックされます。  
  
SQL Server には、動的 SQL を実行するストアド プロシージャとユーザー定義関数を使用したデータ アクセスをユーザーに許可するための新しい方法が 2 つあります。  
  
- Transact-SQL EXECUTE AS 句による権限の借用を利用します。  
  
- 証明書を使用したストアド プロシージャへの署名。  
  
### <a name="execute-as"></a>EXECUTE AS  
EXECUTE AS 句では、呼び出し元のアクセス許可を、EXECUTE AS 句に指定されたユーザーのアクセス許可で置き換えます。 入れ子になったストアド プロシージャまたはトリガーは、プロキシ ユーザーのセキュリティ コンテキストで実行されます。 これにより、行レベルのセキュリティに依存する、または監査を必要とするアプリケーションが中断される可能性があります。 ユーザーの ID を返す一部の関数では、元の呼び出し元ではなく、EXECUTE AS 句に指定されたユーザーを返します。 プロシージャの実行後、または REVERT ステートメントが発行されたときにのみ、実行コンテキストが元の呼び出し元に戻されます。  
  
### <a name="certificate-signing"></a>証明書の署名  
証明書によって署名されたストアド プロシージャが実行されると、証明書ユーザーに付与されたアクセス許可が、呼び出し元のアクセス許可と組み合わされます。 実行コンテキストはそのままです。証明書ユーザーが呼び出し元を偽装することはありません。 ストアド プロシージャに署名するには、いくつかの手順を実装する必要があります。 プロシージャを変更するたびに、再署名する必要があります。  
  
### <a name="cross-database-access"></a>複数データベース間アクセス  
動的に作成された SQL ステートメントが実行される場合、複数データベース間での所有権の継承は機能しません。 SQL Server では、別のデータベースのデータにアクセスするストアド プロシージャを作成し、両方のデータベースに存在する証明書でそのプロシージャに署名することによって、この制限を回避できます。 これにより、ユーザーは、データベースのアクセス権やアクセス許可を付与されなくても、プロシージャで使用されるデータベース リソースにアクセスできるようになります。  
  
## <a name="external-resources"></a>外部リソース  
詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|--------------|-----------------|  
|SQL Server オンライン ブックの[ストアド プロシージャ](../../../relational-databases/stored-procedures/stored-procedures-database-engine.md)と [SQL インジェクション](../../../relational-databases/security/sql-injection.md)|各トピックでは、ストアド プロシージャの作成方法と SQL インジェクションのしくみについて説明します。|  
  
## <a name="next-steps"></a>次のステップ
- [SQL Server におけるアプリケーション セキュリティのシナリオ](application-security-scenarios-sql-server.md)
