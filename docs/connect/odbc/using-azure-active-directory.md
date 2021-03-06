---
title: ODBC ドライバーでの Azure Active Directory の使用 | SQL Server に関する Microsoft Docs
ms.custom: ''
ms.date: 11/08/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 52205f03-ff29-4254-bfa8-07cced155c86
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c0f9d73dace4e17d87e1c93da703786fc920b2fb
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "70176169"
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>ODBC ドライバーでの Azure Active Directory の使用
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>目的

バージョン 13.1 以降の Microsoft ODBC Driver for SQL Server では、ODBC アプリケーションは、Azure Active Directory のフェデレーション ID を使用して、ユーザー名/パスワード、Azure Active Directory アクセス トークン、Azure Active Directory マネージド サービス ID、または Windows 統合認証 (_Windows ドライバーのみ_) によって SQL Azure のインスタンスに接続できます。 ODBC ドライバー バージョン 13.1 の場合、Azure Active Directory アクセス トークン認証は _Windows のみ_です。 ODBC ドライバー バージョン 17 以降では、すべてのプラットフォーム (Windows、Linux、Mac) でこの認証がサポートされます。 ログイン ID を使用した新しい Azure Active Directory 対話型認証は、Windows で ODBC ドライバー バージョン 17.1 に導入されています。 新しい Azure Active Directory マネージド サービス ID 認証方法は、ODBC ドライバー バージョン 17.3.1.1 で、システム割り当てとユーザー割り当ての両方の ID に対して追加されました。 これらはすべて、新しい DSN と接続文字列のキーワード、および接続属性を使用することによって実現します。

> [!NOTE]
> Linux と macOS 上の ODBC ドライバーでは、Active Directory フェデレーション サービス (AD FS) はサポートされません。 Linux または macOS クライアントから Azure Active Directory のユーザー名/パスワード認証を使用していて、お使いの Active Directory 構成にフェデレーション サービスが含まれている場合は、認証が失敗する可能性があります。

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>新しいまたは変更された DSN と接続文字列のキーワード

DSN または接続文字列を使用して接続する場合、`Authentication` キーワードを使用して認証モードを制御できます。 接続文字列で設定された値は、DSN の値 (指定されている場合) をオーバーライドします。 `Authentication` 設定の "_事前属性値_" は、接続文字列および DSN の値から計算された値です。

|Name|値|Default|説明|
|-|-|-|-|
|`Authentication`|(未設定)、(空の文字列)、`SqlPassword`、`ActiveDirectoryPassword`、`ActiveDirectoryIntegrated`、`ActiveDirectoryInteractive`、`ActiveDirectoryMsi` |(未設定)|認証モードを制御します。<table><tr><th>Value<th>説明<tr><td>(未設定)<td>認証モードは他のキーワード (既存のレガシ接続オプション) によって決定されます。<tr><td>(空の文字列)<td>(接続文字列のみ。)DSN で設定されている `Authentication` 値をオーバーライドおよび設定解除します。<tr><td>`SqlPassword`<td>ユーザー名とパスワードを使用して、SQL Server インスタンスに対して直接認証を行います。<tr><td>`ActiveDirectoryPassword`<td>ユーザー名とパスワードを使用して、Azure Active Directory の ID で認証を行います。<tr><td>`ActiveDirectoryIntegrated`<td>"_Windows ドライバーのみ_"。 統合認証を使用して、Azure Active Directory の ID で認証を行います。<tr><td>`ActiveDirectoryInteractive`<td>"_Windows ドライバーのみ_"。 対話型認証を使用して、Azure Active Directory の ID で認証を行います。<tr><td>`ActiveDirectoryMsi`<td>マネージド サービス ID 認証を使用して、Azure Active Directory の ID で認証を行います。 ユーザー割り当て ID の場合、UID はユーザー ID のオブジェクト ID に設定されます。</table>|
|`Encrypt`|(未設定)、`Yes`、`No`|(説明を参照)|接続の暗号化を制御します。 DSN または接続文字列で `Authentication` 設定の事前属性値が _none_ でない場合、既定値は `Yes` です。 それ以外の場合、既定値は `No` です。 属性 `SQL_COPT_SS_AUTHENTICATION` によって `Authentication` の事前属性値がオーバーライドされる場合は、DSN か接続文字列または接続属性で暗号化の値を明示的に設定します。 暗号化の事前属性値は、その値が DSN または接続文字列のいずれかで `Yes` に設定されている場合は `Yes` です。|

## <a name="new-andor-modified-connection-attributes"></a>新しいまたは変更された接続属性

次の接続前接続属性は、Azure Active Directory 認証をサポートするために導入または変更されています。 接続属性に対応する接続文字列または DSN キーワードがあり、接続属性が設定されている場合は、接続属性が優先されます。

|Attribute|Type|値|Default|説明|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`､`SQL_AU_PASSWORD`、`SQL_AU_AD_INTEGRATED`、`SQL_AU_AD_PASSWORD`、`SQL_AU_AD_INTERACTIVE`、`SQL_AU_AD_MSI`、`SQL_AU_RESET`|(未設定)|上記の `Authentication` キーワードの説明を参照してください。 `SQL_AU_NONE` は、DSN または接続文字列で設定された `Authentication` 値を明示的にオーバーライドするために用意されています。それに対し、`SQL_AU_RESET` は、属性が設定されている場合にそれを設定解除し、DSN または接続文字列の値が優先されるようにします。|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|`ACCESSTOKEN` へのポインターまたは NULL|NULL|null 以外の場合は、使用する AzureAD アクセス トークンを指定します。 アクセス トークンを指定し、同時に `UID`、`PWD`、`Trusted_Connection`、または `Authentication` 接続文字列キーワードまたはそれと同等の属性を指定すると、エラーになります。 <br> **注:** ODBC ドライバー バージョン 13.1 では、_Windows_ でのみこれがサポートされます。|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(説明を参照)|接続の暗号化を制御します。 `SQL_EN_OFF` を指定すると暗号化が無効になり、`SQL_EN_ON` を指定すると有効になります。 `Authentication` 設定の事前属性値が _none_ でないか、または `SQL_COPT_SS_ACCESS_TOKEN` が設定されていて、DSN または接続文字列のいずれかで `Encrypt` が指定されていなかった場合、既定値は `SQL_EN_ON` です。 それ以外の場合、既定値は `SQL_EN_OFF` です。 接続属性 `SQL_COPT_SS_AUTHENTICATION` が _none_ 以外に設定されていて、DSN または接続文字列で `Encrypt` が指定されていなかった場合は、`SQL_COPT_SS_ENCRYPT` を必要な値に明示的に設定してください。 この属性の有効な値によって、[接続に暗号化を使用するかどうか](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation)が制御されます。|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Azure Active Directory ではサポートされません。AAD プリンシパルに対するパスワードの変更は、ODBC 接続を通じて行うことができないためです。 <br><br>SQL Server 2005 では、SQL Server 認証におけるパスワードの期限切れが導入されました。 クライアントから接続の古いパスワードと新しいパスワードの両方を提供できるようにするために、`SQL_COPT_SS_OLDPWD` 属性が追加されました。 この属性が設定されている場合、接続文字列には変更された "古いパスワード" が含まれているので、プロバイダーは最初の接続またはそれ以降の接続で接続プールを使用しません。|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`、`SQL_IS_ON`|`SQL_IS_OFF`|"_非推奨_" です。代わりに `SQL_COPT_SS_AUTHENTICATION` を `SQL_AU_AD_INTEGRATED` に設定して使用してください。 <br><br>サーバー ログインでのアクセス検証に Windows 認証 (Linux と macOS では Kerberos) を使用するように強制します。 Windows 認証を使用すると、ドライバーでは `SQLConnect`、`SQLDriverConnect`、または `SQLBrowseConnect` の処理の一環として提供されるユーザー ID とパスワードが無視されます。|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Azure Active Directory での UI の追加 (Windows ドライバーのみ)

ドライバーの DSN セットアップと接続の UI が拡張され、Azure AD による認証を使用するために必要なオプションが追加されました。

### <a name="creating-and-editing-dsns-in-the-ui"></a>UI で DSN を作成および編集する

ドライバーのセットアップ UI を使用して既存の DSN を作成または編集する際に、新しい Azure AD 認証オプションを使用できます。

SQL Azure への Azure Active Directory 統合認証の場合: `Authentication=ActiveDirectoryIntegrated`

![CreateNewDSN_ADIntegrated.png](windows/CreateNewDSN_ADIntegrated.png)

SQL Azure に対する Azure Active Directory ユーザー名/パスワード認証の場合: `Authentication=ActiveDirectoryPassword`

![CreateNewDSN_ADPassword.png](windows/CreateNewDSN_ADPassword.png)

`Authentication=ActiveDirectoryInteractive` SQL Azure に Azure Active Directory 対話型認証

![CreateNewDSN_ADInteractive.png](windows/CreateNewDSN_ADInteractive.png)

SQL Server に対するユーザー名/パスワード認証の場合 (Azure またはそれ以外): `Authentication=SqlPassword`

![CreateNewDSN_SQLServer.png](windows/CreateNewDSN_SQLServer.png)

Windows レガシ SSPI 統合認証の場合: `Trusted_Connection=Yes`

![CreateNewDSN_winSSPI.png](windows/CreateNewDSN_winSSPI.png)

5 つのオプションは、それぞれ `Trusted_Connection=Yes` (既存のレガシ Windows SSPI のみの統合認証) と `Authentication=` `ActiveDirectoryIntegrated`、`SqlPassword`、`ActiveDirectoryPassword`、および `ActiveDirectoryInteractive` に対応しています。

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>SQLDriverConnect プロンプト (Windows ドライバーのみ)

接続を完了するために必要な情報を要求するときに SQLDriverConnect によって表示されるプロンプト ダイアログには、Azure AD 認証に関する 3 つの新しいオプションが含まれています。

![ServerLogin.png](windows/ServerLogin.png)

これらのオプションは、上記の DSN セットアップ UI で使用できるものと同じ 5 つのオプションに対応しています。

### <a name="example-connection-strings"></a>接続文字列の例
1. SQL Server 認証 - レガシ構文。 サーバー証明書は検証されず、暗号化はサーバーで適用される場合にのみ使用されます。 ユーザー名/パスワードは接続文字列内で渡されます。
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. SQL 認証 - 新しい構文。 クライアントが暗号化を要求します (`Encrypt` の既定値は `true` です)。サーバー証明書は、暗号化の設定に関係なく検証されます (`TrustServerCertificate` が `true` に設定されている場合を除きます)。 ユーザー名/パスワードは接続文字列内で渡されます。
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. (SQL Server または SQL IaaS に対する) SSPI を使用した統合 Windows 認証 (Linux と macOS では Kerberos) - 現在の構文。 暗号化を使用しない限り、サーバー証明書は検証されません。 
`server=Server;database=Database;Trusted_Connection=yes;`
4. ("_Windows ドライバーのみ_"。)SSPI を使用した統合 Windows 認証 (ターゲット データベースが SQL Server または SQL IaaS 内にある場合) - 新しい構文。 クライアントが暗号化を要求します (`Encrypt` の既定値は `true` です)。サーバー証明書は、暗号化の設定に関係なく検証されます (`TrustServerCertificate` が `true` に設定されている場合を除きます)。 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. AAD のユーザー名/パスワード認証 (ターゲット データベースが Azure SQL DB 内にある場合)。 暗号化の設定に関係なく、サーバー証明書は検証されます (`TrustServerCertificate` が `true` に設定されている場合を除きます)。 ユーザー名/パスワードは接続文字列内で渡されます。 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. ("_Windows ドライバーのみ_"。)ADAL を使用した統合 Windows 認証。ターゲット データベースが Azure SQL Database 内にあると想定して、AAD によって発行されたアクセス トークンの Windows アカウント資格情報を使用します。 暗号化の設定に関係なく、サーバー証明書は検証されます (`TrustServerCertificate` が `true` に設定されている場合を除きます)。 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. ("_Windows ドライバーのみ_"。)AAD 対話型認証では、Azure Multi-factor Authentication テクノロジを使用して接続をセットアップします。 このモードでは、ログイン ID を指定することで Azure 認証ダイアログがトリガーされ、ユーザーがパスワードを入力して接続を完了できます。 ユーザー名は接続文字列内で渡されます。
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![WindowsAzureAuth.png](windows/WindowsAzureAuth.png)

8. AAD マネージド サービス ID 認証では、システム割り当てまたはユーザー割り当ての ID を認証に使用して接続をセットアップします。 ユーザー割り当て ID の場合、UID はユーザー ID のオブジェクト ID に設定されます。<br>
システムによって割り当てられた ID の場合:<br>
`server=Server;database=Database;Authentication=ActiveDirectoryMsi;`<br>
オブジェクト ID が myObjectId であるユーザー割り当て ID の場合:<br>
`server=Server;database=Database;UID=myObjectId;Authentication=ActiveDirectoryMsi;`

> [!NOTE] 
>- Windows ODBC ドライバーで新しい Active Directory オプションを使用する場合は、[SQL Server 用 Active Directory 認証ライブラリ](https://go.microsoft.com/fwlink/?LinkID=513072)がインストールされていることを確認します。 Linux および macOS ドライバーを使用する場合は、`libcurl` がインストールされていることを確認します。 ドライバー バージョン 17.2 以降では、これが明示的な依存関係にはなりません。他の認証方法や ODBC 操作では不要であるためです。
>- SQL Server アカウントのユーザー名とパスワードを使用して接続する場合、新しい `SqlPassword` オプションを使用できるようになりました。このオプションは、より安全性の高い接続の既定値が有効になるので、SQL Azure では特にお勧めします。
>- Azure Active Directory アカウントのユーザー名とパスワードを使用して接続するには、接続文字列に `Authentication=ActiveDirectoryPassword` を指定し、ユーザー名とパスワードではそれぞれ `UID` と `PWD` キーワードを指定します。
>- Windows 統合または Active Directory 統合 (Windows ドライバーのみ) 認証を使用して接続するには、接続文字列に `Authentication=ActiveDirectoryIntegrated` を指定します。 ドライバーによって適切な認証モードが自動的に選択されます。 `UID` と `PWD` は指定できません。
>- Active Directory 対話型 (Windows ドライバーのみ) 認証を使用して接続するには、`UID` を指定する必要があります。

## <a name="authenticating-with-an-access-token"></a>アクセス トークンを使用した認証

`SQL_COPT_SS_ACCESS_TOKEN` 接続前属性を使用すると、ユーザー名とパスワードではなく Azure AD から取得したアクセス トークンを認証に使用できます。また、ドライバーによるアクセス トークンのネゴシエーションと取得もバイパスされます。 アクセス トークンを使用するには、`SQL_COPT_SS_ACCESS_TOKEN` 接続属性を `ACCESSTOKEN` 構造体へのポインターに設定します。

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

`ACCESSTOKEN` は、4 バイト_長_と、その後のアクセス トークンを形成する不透明データのバイト_長_によって構成される、可変長構造体です。 SQL Server によるアクセス トークンの処理方法が原因で、[OAuth 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios) JSON 応答を介して取得されたものを拡張して、ASCII 文字のみを含む UCS 2 文字列のように、各バイトの後に 0 埋め込みバイトを挿入することが必要です。ただし、トークンは不透明値であり、バイト単位で指定する長さに null 終端文字を含めることはできません。 この認証方法は、長さと形式の制約が非常に多いため、`SQL_COPT_SS_ACCESS_TOKEN` 接続属性を使用してプログラムでのみ使用できます。対応する DSN または接続文字列のキーワードはありません。 接続文字列には、`UID`、`PWD`、`Authentication`、または `Trusted_Connection` キーワードを含めることはできません。

> [!NOTE]
> ODBC ドライバー バージョン 13.1 では、_Windows_ でのみこの認証がサポートされます。

## <a name="azure-active-directory-authentication-sample-code"></a>Azure Active Directory 認証サンプル コード

次のサンプルは、Azure Active Directory を使用して接続キーワードによって SQL Server に接続するために必要なコードを示しています。 アプリケーション コード自体を変更する必要はないことに注意してください。認証に AAD を使用するために必要な変更は、接続文字列または DSN (使用されている場合) だけです。
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
次のサンプルは、Azure Active Directory を使用してアクセス トークン認証によって SQL Server に接続するために必要なコードを示しています。 この場合、アクセス トークンを処理し、関連する接続属性を設定するためにアプリケーション コードの変更が必要です。
~~~
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server}"
    SQLCHAR accessToken[] = "eyJ0eXAiOi..."; // In the format extracted from an OAuth JSON response
    ...
    DWORD dataSize = 2 * strlen(accessToken);
    ACCESSTOKEN *pAccToken = malloc(sizeof(ACCESSTOKEN) + dataSize);
    pAccToken->dataSize = dataSize;
    // Expand access token with padding bytes
    for(int i = 0, j = 0; i < dataSize; i += 2, j++) {
        pAccToken->data[i] = accessToken[j];
        pAccToken->data[i+1] = 0;
    }
    ...
    SQLSetConnectAttr(hDbc, SQL_COPT_SS_ACCESS_TOKEN, (SQLPOINTER)pAccToken, SQL_IS_POINTER);
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);      
    ...
    free(pAccToken);
~~~
以下は、Azure Active Directory 対話型認証で使用するサンプルの接続文字列です。 パスワードは Azure 認証画面を使用して入力されるため、PWD フィールドが含まれていないことに注意してください。
~~~
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;Authentication=ActiveDirectoryInteractive"
~~~
以下は、Azure Active Directory マネージド サービス ID 認証で使用するサンプルの接続文字列です。 ユーザー割り当て ID に対して、UID がユーザー ID のオブジェクト ID に設定されていることに注意してください。
~~~
// For system-assigned identity,
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};Authentication=ActiveDirectoryMsi"
...
// For user-assigned identity with object ID equals to myObjectId
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myObjectId;Authentication=ActiveDirectoryMsi"
~~~

## <a name="see-also"></a>参照
[Azure AD 認証を使用した Azure SQL DB のトークンベース認証のサポート](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

