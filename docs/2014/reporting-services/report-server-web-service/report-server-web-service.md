---
title: レポート サーバー Web サービス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SSIS, Web service
- Web service [Reporting Services]
- Reporting Services, extending
- SQL Server Reporting Services, Web service
- Reporting Services, Web service
- XML Web service [Reporting Services]
- Report Server Web service
ms.assetid: 16c21dec-6b46-4497-9a0c-1b0f2b6ab8fc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b577fd9a78dbb5f12af79e190709065931ec463a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62520566"
---
# <a name="report-server-web-service"></a>レポート サーバー Web サービス
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]レポートサーバー Web サービスを使用して、レポートサーバーのすべての機能にアクセスできます。 レポート サーバー Web サービスは、SOAP API を使用した XML Web サービスです。 SOAP over HTTP を使用し、クライアント プログラムとレポート サーバー間の通信インターフェイスとして機能します。 Web サービスは 2 つのエンドポイントを提供します。1 つはレポートを実行するためのもので、もう 1 つはレポートを管理するためのものです。加えて、レポート サーバーの機能を公開するメソッドが用意されています。このメソッドにより、レポートのライフ サイクルの任意の時点に対するカスタム ツールを作成できます。  
  
 Web サービスに基づいた [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アプリケーションを開発する主な方法は 3 種類あります。 次のようにすることができます。  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]および[!INCLUDE[msCoName](../../includes/msconame-md.md)] SDK [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]を使用してアプリケーションを開発します。 
  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の使用方法の詳細については、「[Web サービスと、.NET Framework を使用してのアプリケーションの構築](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)」を参照してください。  
  
-   
  ** のスクリプト環境である、** rs[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ユーティリティ (RS.exe) を使用してアプリケーションを開発する。 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] スクリプトを使用すると、レポート サーバー Web サービスのあらゆる操作を実行できます。 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のスクリプトの詳細については、「[rs.exe ユーティリティと Web サービスを使用したスクリプト](../tools/script-with-the-rs-exe-utility-and-the-web-service.md)」を参照してください。  
  
-   SOAP 対応の開発ツールを使用してアプリケーションを開発する。 詳細については、「[Reporting Services における SOAP の役割](../report-server-web-service/the-role-of-soap-in-reporting-services.md)」を参照してください。  
  
## <a name="programming-diagram"></a>プログラミング図  
 ![レポート サーバー Web サービスの配置オプション](../../../2014/reporting-services/media/reportserviceswebserviceprog-01.gif "レポート サーバー Web サービスの配置オプション")  
Reporting Services で利用可能な Web サービス開発オプション  
  
## <a name="in-this-section"></a>このセクションの内容  
 [レポート サーバー Web サービスのメソッド](../report-server-web-service/methods/report-server-web-service-methods.md)  
 各レポート サーバー Web サービスの機能とメソッドについて説明します。  
  
 [Reporting Services における SOAP の役割](../report-server-web-service/the-role-of-soap-in-reporting-services.md)  
 SOAP の概要およびレポート サーバー Web サービスでの使用方法について説明します。  
  
 [SOAP API へのアクセス](../report-server-web-service/accessing-the-soap-api.md)  
 Web サービス記述言語 (WSDL) について説明し、Reporting Services WSDL ファイルにアクセスするための URL を記載します。  
  
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
 Reporting Services SOAP API を呼び出すアプリケーションと Web サービスの開発について説明します。  
  
 [rs.exe ユーティリティと Web サービスを使用したスクリプト](../tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] スクリプト環境の概要を説明します。  
  
 [テクニカル リファレンス (SSRS)](../../../2014/reporting-services/technical-reference-ssrs.md)  
 レポート サーバー Web サービスのメソッドおよび対応する複合型のリファレンス情報です。  
  
## <a name="user-requirements-for-web-service-development"></a>Web サービスを開発するためのユーザーの必要条件  
 レポート サーバー Web サービスを使用してアプリケーションを開発するには、次の必要条件を満たす必要があります。  
  
-   レポート サーバーへのインターネット接続とアクセスが可能なコンピューターに [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 5.5 以降がインストールされていること。  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]または[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 、 [!INCLUDE[msCoName](../../includes/msconame-md.md)]を使用してアプリケーションを開発および配置する場合は、SDK をコンピューターにインストールします。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]  
  
-   機能の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]詳細について説明します。  
  
-   SOAP および [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)]に関する十分な知識があること。  
  
-   を開発プラットフォームと[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]して使用する予定[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)]の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]場合、やなどの互換性のある言語での開発エクスペリエンス。  
  
## <a name="see-also"></a>参照  
 [レポート サーバー web サービス](../report-server-web-service/report-server-web-service.md)  
  
  
