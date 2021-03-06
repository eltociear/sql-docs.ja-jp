---
title: sp_OACreate (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OACreate
- sp_OACreate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OACreate
ms.assetid: eb84c0f1-26dd-48f9-9368-13ee4a30a27c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2ad8059466ac520b6f9f793af7670cbd73b96b38
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107932"
---
# <a name="sp_oacreate-transact-sql"></a>sp_OACreate (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  OLE オブジェクトのインスタンスを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_OACreate { progid | clsid } , objecttoken OUTPUT [ , context ]   
```  
  
## <a name="arguments"></a>引数  
 *progid*  
 作成する OLE オブジェクトのプログラム識別子 (ProgID) を示します。 この文字列は、OLE オブジェクトのクラスについて説明し、" ****_OLEComponent_" という形式になってい**ます**。_オブジェクト_**'**  
  
 *OLEComponent*は ole オートメーションサーバーのコンポーネント名で、 *object*は ole オブジェクトの名前です。 指定された OLE オブジェクトは有効である必要があり、 **IDispatch**インターフェイスをサポートしている必要があります。  
  
 たとえば、SQLDMO のようになります。SQLServer は、SQL-DMO **sqlserver**オブジェクトの ProgID です。 Sql-dmo には、コンポーネント名 SQLDMO、 **sqlserver**オブジェクトが有効であること、および (すべての sql-dmo オブジェクトと同様に)、 **Sqlserver**オブジェクトが**IDispatch**をサポートしています。  
  
 *clsid*  
 作成する OLE オブジェクトのクラス ID (CLSID) を指定します。 この文字列は、OLE オブジェクトのクラスを記述し、 **' {**_nnnnnnnn_-nnnn-nnnn-nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn **} '** という形式になっています。 指定された OLE オブジェクトは有効である必要があり、 **IDispatch**インターフェイスをサポートしている必要があります。  
  
 たとえば、{00026BA1-0000-0000-C000-000000000046} は SQL-DMO **SQLServer**オブジェクトの CLSID です。  
  
 _objecttoken_の**出力**  
 返されるオブジェクトトークンです。データ型が**int**のローカル変数である必要があります。このオブジェクトトークンは、作成された OLE オブジェクトを識別し、他の OLE オートメーションストアドプロシージャの呼び出しで使用されます。  
  
 *context*  
 新しく作成した OLE オブジェクトを実行するときの実行条件を指定します。 指定する場合、この値は次のいずれかである必要があります。  
  
 **1** = インプロセス (.DLL) OLE サーバーのみ。  
  
 **4** = ローカル (.EXE) OLE サーバーのみ。  
  
 **5** = インプロセスとローカル OLE サーバーの両方が許可されます。  
  
 指定しない場合、既定値は**5**です。 この値は、 **CoCreateInstance**への呼び出しの*dwclscontext*パラメーターとして渡されます。  
  
 インプロセス OLE サーバーが許可されている場合 (コンテキスト値が**1**または**5**の場合、またはコンテキスト値が指定されていない場合)、それはに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]よって所有されているメモリおよびその他のリソースにアクセスできます。 組み込み OLE サーバーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメモリやリソースに損傷を与え、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のアクセス違反など予期しない結果を招く場合があります。  
  
 コンテキスト値を**4**に指定すると、ローカルの OLE サーバーは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]リソースにアクセスできず、メモリやリソースに損傷[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を与えることはありません。  
  
> [!NOTE]  
>  このストアドプロシージャのパラメーターは、名前ではなく位置によって指定されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または0以外の数 (失敗)。これは、OLE オートメーションオブジェクトによって返される HRESULT の整数値です。  
  
 HRESULT のリターンコードの詳細については、「 [OLE オートメーションのリターンコードとエラー情報](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 OLE オートメーションプロシージャが有効になっている場合、 **sp_OACreate**を呼び出すと、ole オートメーションの共有実行環境が開始されます。 OLE オートメーションを有効にする方法の詳細については、「 [Ole Automation Procedures サーバー構成オプション](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)」を参照してください。  
  
 作成された OLE オブジェクトは、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント バッチの最後に自動的に破棄されます。  
  
## <a name="permissions"></a>アクセス許可  
 **Sysadmin**固定サーバーロールのメンバーシップ、またはこのストアドプロシージャに対して直接実行権限が必要です。 `Ole Automation Procedures`OLE オートメーションに関連するシステムプロシージャを使用するには、構成を**有効**にする必要があります。  
  
## <a name="examples"></a>例  
  
### <a name="a-using-progid"></a>A. ProgID を使用する  
 次の例では、ProgID を使用して、SQL-DMO **SQLServer**オブジェクトを作成します。  
  
```  
DECLARE @object int;  
DECLARE @hr int;  
DECLARE @src varchar(255), @desc varchar(255);  
EXEC @hr = sp_OACreate 'SQLDMO.SQLServer', @object OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object, @src OUT, @desc OUT   
   raiserror('Error Creating COM Component 0x%x, %s, %s',16,1, @hr, @src, @desc)  
    RETURN  
END;  
GO  
```  
  
### <a name="b-using-clsid"></a>B. CLSID の使用  
 次の例では、CLSID を使用して、SQL-DMO **SQLServer**オブジェクトを作成します。  
  
```  
DECLARE @object int;  
DECLARE @hr int;  
DECLARE @src varchar(255), @desc varchar(255);  
EXEC @hr = sp_OACreate '{00026BA1-0000-0000-C000-000000000046}',  
    @object OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object, @src OUT, @desc OUT   
   raiserror('Error Creating COM Component 0x%x, %s, %s',16,1, @hr, @src, @desc)  
    RETURN  
END;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;の OLE オートメーションストアドプロシージャ](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [Ole Automation Procedures サーバー構成オプション](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)   
 [OLE オートメーションのサンプル スクリプト](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
