---
title: LocalDB ヘッダーとバージョン情報の SQL Server Express |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_location:
- sqluserinstance.dll
ms.assetid: 506b5161-b902-4894-b87b-9192d7b1664a
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6e390430115daf394c5e94267dad30a87851375d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63128694"
---
# <a name="sql-server-express-localdb-header-and-version-information"></a>SQL Server Express LocalDB ヘッダーとバージョン情報
  SQL Server Express LocalDB インスタンス API には、独立したヘッダー ファイルはありません。LocalDB の関数署名とエラー コードは、SQL Server Native Client ヘッダー ファイル (sqlncli.h) に定義されています。 LocalDB インスタンス API を使用するには、プロジェクトに sqlncli.h ヘッダー ファイルをインクルードする必要があります。  
  
## <a name="localdb-versioning"></a>LocalDB のバージョン管理  
 LocalDB インストールでは、主要な SQL Server バージョンごとの単一のバイナリ セットを使用します。 これらの LocalDB バージョンは維持され、個別にパッチが適用されます。 つまり、ユーザーはどの LocalDB ベースライン リリース (主要な SQL Server バージョン) を使用するのかを指定する必要があるということです。 バージョンは **、.NET Framework バージョン**クラスで定義されている標準バージョン形式で指定されます。  
  
 *major. minor [. build [. revision]]*  
  
 バージョン文字列の最初の2つの数値 (*major*および*minor*) は必須です。 バージョン文字列の最後の2つの数値 (*build*と*revision*) は省略可能で、ユーザーがそのままにした場合の既定値は0です。これは、ユーザーが LocalDB バージョン番号として "12.2" だけを指定した場合、ユーザーが "12.2.0.0" を指定したかのように処理されることを意味します。  
  
 LocalDB インストールのバージョンは、SQL Server インスタンス レジストリ キーの下の MSSQLServer\CurrentVersion レジストリ キーに定義されます。次に例を示します。  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL12E.LOCALDB\ MSSQLServer\CurrentVersion: "CurrentVersion"="12.0.2531.0"  
```  
  
 同じ 1 台のワークステーション上で複数の LocalDB バージョンが同時にサポートされます。 ただし、ユーザーコードは、常にローカルコンピューター上で使用可能な最新の**Sqluserinstance.dll** DLL を使用して LocalDB インスタンスに接続します。  
  
## <a name="locating-the-sqluserinstance-dll"></a>SQLUserInstance DLL の検索  
 クライアントプロバイダーは、 **Sqluserinstance.dll** DLL を検索するために、次のレジストリキーを使用します。  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions]  
```  
  
 このキーの下に、キーのリストがあります。このコンピューターにインストールされている LocalDB のバージョンごとに 1 つのキーがあります。 これらの各キーには、 * \<メジャーバージョン>* の形式で LocalDB バージョン番号が付けられています。マイナーバージョン>(たとえば、の[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]キーは12.0 という名前です)。 * \<* 各バージョン キーの下に、`InstanceAPIPath` の名前と値のペアが 1 つあります。このペアは、そのバージョンでインストールされた SQLUserInstance.dll ファイルの絶対パスを定義します。 次に、LocalDB バージョン 11.0 と 12.0 がインストールされたコンピューターのレジストリ エントリの例を示します。  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"]  
```  
  
 クライアントプロバイダーは、インストールされているすべてのバージョンの最新バージョン**** を検索し、関連付け`InstanceAPIPath`られている値から sqluserinstance.dll DLL ファイルを読み込みます。  
  
### <a name="wow64-mode-on-64-bit-windows"></a>64 ビット版 Windows 上の WOW64 モード  
 LocalDB の 64 ビット インストールには、追加のレジストリ キー セットがあるため、Windows-32-on-Windows-64 (WOW64) モードで実行される 32 ビット版アプリケーションで LocalDB を使用することができます。 具体的には、64 ビット版 Windows では、LocalDB MSI が次のレジストリ キーを作成します。  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"]  
  
```  
  
 64ビットの`Installed Versions`プログラムキーを読み取ると、64ビットバージョンの**sqluserinstance.dll** DLL を指す値が表示されます。一方、32ビットプログラム (WOW64 モードでは、64ビットの Windows で実行され`Installed Versions`ている) は`Wow6432Node` 、hive の下にあるキーに自動的にリダイレクトされます。 このキーには、 **Sqluserinstance.dll** DLL の32ビットバージョンをポイントする値が含まれています。  
  
## <a name="using-localdb_define_proxy_functions"></a>LOCALDB_DEFINE_PROXY_FUNCTIONS の使用  
 LocalDB インスタンス API は、 **Sqluserinstance.dll** DLL の検出と読み込みを自動化する LOCALDB_DEFINE_PROXY_FUNCTIONS という名前の定数を定義します。  
  
 この定数によって有効化されるコードのセクションにより、各 LocalDB API のプロキシが実装されます。 プロキシの実装では、共通の関数を使用して、インストールされている最新の**Sqluserinstance.dll** DLL 内のエントリポイントにバインドしてから、要求を転送します。  
  
 プロキシ関数が有効化されるのは、定数 LOCALDB_DEFINE_PROXY_FUNCTIONS がユーザー コードで定義された後に、sqlncli.h ファイルがインクルードされた場合だけです。 この定数は、すべての API エントリ ポイントの外部関数名を定義するので、1 つのソース モジュール (.cpp ファイル) だけに定義する必要があります。 この定数により、各 LocalDB API のプロキシが実装されます。  
  
 次のコード例では、ネイティブの C++ コードのマクロを使用する方法を示します。  
  
```  
// Define the LOCALDB_DEFINE_PROXY_FUNCTIONS constant to enable the LocalDB proxy functions   
// The #define has to take place BEFORE the API header file (sqlncli.h) is included  
#define LOCALDB_DEFINE_PROXY_FUNCTIONS  
#include <sqlncli.h>  
...  
HRESULT hr = S_OK;  
  
// Create LocalDB instance by calling the create API proxy function included by macro  
if (FAILED(hr = LocalDBCreateInstance( L"12.0", L"name", 0)))  
{  
...  
}  
...  
  
```  
  
  
