---
title: 서버 및 ClickOnce 배포에서 클라이언트 구성 문제 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b8f81f22ffe566524e45a62330bc95c8ce00016
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686378"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>ClickOnce 배포 시 서버 및 클라이언트 구성 문제
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

인터넷 정보 서비스 (IIS)를 사용 하 여 Windows Server에서 배포에는 Windows에서 인식 하지 못하는 파일 형식을 포함 하 고 Microsoft Word 파일을 같은 IIS는 해당 파일을 전송할 거부 하 고 배포에 실패 합니다.  
  
 또한 일부 웹 서버 응용 프로그램 소프트웨어와 같이 및 웹 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], 파일의 목록을 포함 및 파일 형식을 다운로드할 수 없습니다. 예를 들어 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 모든 Web.config 파일의 다운로드를 차단 합니다. 이러한 파일에는 사용자 이름과 암호 같은 중요 한 정보가 들어 있습니다.  
  
 이 제한은 인해 core를 다운로드 하는 데는 문제가 없더라도 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 매니페스트 및 어셈블리와 같은 파일을이 제한으로 인해 수의 일부로 포함 된 데이터 파일을 다운로드 하면 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램입니다. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], IIS 구성 관리자에서 해당 파일의 다운로드를 금지 하는 처리기를 제거 하 여이 오류를 해결할 수 있습니다. 추가 세부 정보에 대 한 IIS server 설명서를 참조 합니다.  
  
 일부 웹 서버에.dll,.config 등.mdf 확장명의 파일을 차단할 수 있습니다. Windows 기반 응용 프로그램은 일반적으로 이러한 확장 중 일부를 사용 하 여 파일을 포함 합니다. 사용자가 실행 하려고 하는 경우는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 웹 서버에서 차단된 된 파일에 액세스 하는 응용 프로그램 오류가 발생 합니다. 모든 파일 확장명을 차단 해제 하는 대신 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 기본적으로 ".deploy" 파일 확장명을 사용 하 여 모든 응용 프로그램 파일을 게시 합니다. 따라서 관리자가 다음 세 개의 파일 확장명을 차단 해제 하도록 웹 서버를 구성 해야 하는 합니다.  
  
- .application  
  
- .manifest  
  
- .deploy  
  
  선택을 취소 하 여이 옵션을 해제할 수는 있지만 합니다 **".deploy" 파일 확장명을 사용 하 여** 옵션을 합니다 [Publish Options Dialog Box](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), 모든 파일 확장명을 차단 해제 하려면 웹 서버를 구성 해야 하는 경우 응용 프로그램에서 사용 합니다.  
  
  IIS를 설치 하지 않은 위치를 사용 하는 경우.manifest,.application, 및.deploy, 예를 들어 구성 해야 합니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], 또는 다른 웹 서버 (예: Apache)를 사용 하는 경우.  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce 및 Secure Sockets Layer (SSL)  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램이 작동 제대로 SSL을 통해 Internet Explorer에서 SSL 인증서에 대 한 프롬프트를 발생 하는 경우를 제외 하 고 있습니다. 프롬프트 만료 등 사이트 이름이 일치 하지 않는 경우 인증서 또는 인증서를 사용 하 여 문제가 있을 때 발생할 수 있습니다. 있도록 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] SSL 연결을 통해 작업, 인증서, 최신 되었고 인증서 데이터를 사이트 데이터와 일치 하는지 확인 합니다.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce 및 프록시 인증  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .NET Framework 3.5 부터는 Windows 통합 프록시 인증에 대 한 지원을 제공 합니다. 없는 특정 machine.config 지시문은 필수입니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 기본 또는 다이제스트와 같은 다른 인증 프로토콜에 대 한 지원을 제공 하지 않습니다.  
  
 또한이 기능을 사용 하도록.NET Framework 2.0 핫픽스를 적용할 수 있습니다. 자세한 내용은 http://go.microsoft.com/fwlink/?LinkId=158730을 참조하세요.  
  
 자세한 내용은 [ \<defaultProxy > 요소 (네트워크 설정)](https://msdn.microsoft.com/library/9d663c4b-07b4-4f6f-9b12-efbd3630354f)합니다.  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce 및 웹 브라우저 호환성  
 현재 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 설치 배포 매니페스트 URL을 Internet Explorer를 사용 하 여 열려 있는 경우에 시작 됩니다. Microsoft Office Outlook과 같은 다른 응용 프로그램에서 URL를 시작 하는 배포는 Internet Explorer는 기본 웹 브라우저로 설정 된 경우에 성공적으로 시작 됩니다.  
  
> [!NOTE]
> Mozilla Firefox는 비어 있지 배포 공급자 또는 Microsoft.NET Framework Assistant 확장은 설치 하는 경우 지원 됩니다. 이 확장은.NET Framework 3.5 SP1을 사용 하 여 패키지 됩니다. XBAP 지원에 대 한 플러그 인 NPWPF 필요할 때 활성화 됩니다.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>브라우저에서 스크립팅을 통해 ClickOnce 응용 프로그램 활성화  
 시작 하는 사용자 지정 웹 페이지를 개발한 경우는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 액티브 스크립팅을 사용 하 여 응용 프로그램 일부 컴퓨터에서 응용 프로그램 시작 되지 않는 경우가 있습니다. 이라는 설정을 포함 하는 Internet Explorer **파일 다운로드에 대 한 자동 확인**는이 동작에 영향을 줍니다. 이 설정의 수를 **보안** 탭에서 해당 **옵션** 이 동작에 영향을 주는 메뉴. 라고 **파일 다운로드에 대 한 자동 확인**, 아래에 표시 되는 **다운로드** 범주입니다. 속성 설정할지 **사용 하도록 설정** 인트라넷 웹 페이지를 기본적으로 **사용 하지 않도록 설정** 인터넷 웹 페이지는 기본적으로 합니다. 이 설정 설정 된 경우 **사용 하지 않도록 설정**를 활성화 하려고를 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램 프로그래밍 방식으로 (예를 들어, 해당 URL을 할당 하 여는 `document.location` 속성) 차단 됩니다. 이러한 상황에서는 사용자가 시작할 수만 사용자가 시작한 다운로드를 통해 응용 프로그램 예를 들어, 응용 프로그램의 URL로 하이퍼링크를 클릭 하 여 합니다.  
  
## <a name="additional-server-configuration-issues"></a>추가 서버 구성 문제  
  
##### <a name="administrator-permissions-required"></a>관리자 권한 필요  
 HTTP를 사용 하 여 게시 하는 경우 대상 서버에서 관리자 권한이 있어야 합니다. IIS는이 권한 수준이 필요합니다. HTTP를 사용 하 여 게시 하지 않는 경우만 쓰기 권한이 필요 대상 경로에 있습니다.  
  
##### <a name="server-authentication-issues"></a>서버 인증 문제  
 해제 "익명 액세스" 권한이 있는 원격 서버에 게시할 때 다음과 같은 경고가 표시 됩니다.  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
> 기본 자격 증명 이외의 자격 증명을 요구 하는 사이트를 클릭 하면 보안 대화 상자에서 작동 하는 NTLM (NT 챌린지-응답) 인증을 할 수 있습니다 **확인** 제공 된 저장 하려는 경우 메시지가 나타나면 이후 세션에 대 한 자격 증명입니다. 그러나이 해결 방법은 기본 인증에 대 한 작동 하지 않습니다.  
  
## <a name="using-third-party-web-servers"></a>타사 웹 서버를 사용 하 여  
 배포 하는 경우는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] IIS 이외의 웹 서버에서 응용 프로그램에 문제가 발생할 수는 서버 키에 대 한 잘못 된 콘텐츠 형식을 반환 하는 경우 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 같은 배포 매니페스트와 응용 프로그램 매니페스트 파일. 이 문제를 해결 하려면 준비에서 서버에 새 콘텐츠 형식을 추가 하 고 모든 파일 이름 확장명 매핑이 다음 표에 나열 되는지 확인 하는 방법에 대 한 설명서는 웹 서버의 도움말을 참조 하십시오.  
  
|파일 이름 확장명|콘텐츠 형식|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce 및 매핑된 드라이브  
 ClickOnce 응용 프로그램을 게시 하려면 Visual Studio를 사용 하는 경우에 설치 위치로 매핑된 드라이브를 지정할 수 없습니다. 그러나 ClickOnce 응용 프로그램 매니페스트 생성기 및 편집기 (Mage.exe 및 MageUI.exe)를 사용 하 여 매핑된 드라이브에서 설치를 수정할 수 있습니다. 자세한 내용은 [Mage.exe (매니페스트 생성 및 편집 도구)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) 하 고 [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)합니다.  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>응용 프로그램을 설치 하는 것에 대 한 FTP 프로토콜이 지원 되지  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] HTTP 1.1 웹 서버나 파일 서버에서 응용 프로그램을 설치 하도록 지원 합니다. 응용 프로그램을 설치 하는 것에 대 한 FTP (파일 전송 프로토콜) 지원 되지 않습니다. 응용 프로그램에만 게시에 FTP를 사용할 수 있습니다. 다음 표에서 이러한 차이점을 보여 줍니다.  
  
|URL 형식|설명|  
|--------------|-----------------|  
|ftp://|게시할 수는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 이 프로토콜을 사용 하 여 응용 프로그램입니다.|  
|http://|설치할 수는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 이 프로토콜을 사용 하 여 응용 프로그램입니다.|  
|https://|설치할 수는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 이 프로토콜을 사용 하 여 응용 프로그램입니다.|  
|file://|설치할 수는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 이 프로토콜을 사용 하 여 응용 프로그램입니다.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows 방화벽  
 기본적으로 Windows XP SP2에는 Windows 방화벽을 사용 합니다. 게시 및 실행 수는 Windows XP가 설치 된 컴퓨터에서 응용 프로그램을 개발 하는 경우 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] IIS를 실행 하는 로컬 서버에서 응용 프로그램입니다. 그러나 Windows 방화벽을 열지 않으면 다른 컴퓨터에서 IIS를 실행 중인 해당 서버를 액세스할 수 없습니다. Windows 방화벽을 관리 하는 방법은 Windows 도움말을 참조 하세요.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server FrontPage server extensions를 사용 하도록 설정  
 Microsoft의 FrontPage Server Extensions가 HTTP를 사용 하는 Windows 웹 서버에 대 한 응용 프로그램 게시 필요 합니다.  
  
 기본적으로 Windows 서버 없는 FrontPage Server Extensions를 설치 합니다. 사용 하려는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] FrontPage Server Extensions를 사용 하 여 HTTP를 사용 하는 Windows Server 웹 서버에 게시 하려면 FrontPage Server Extensions를 먼저 설치 해야 합니다. Windows Server에서 사용자 서버 관리 관리 도구를 사용 하 여 설치를 수행할 수 있습니다.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server 잠긴 콘텐츠 형식  
 IIS에서 [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] 알려진된 특정 콘텐츠 형식 (예를 들어,.htm,.html,.txt 및 등)를 제외 하 고 모든 파일 형식의 잠급니다. 배포를 사용 하도록 설정 하려면 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 형식.application,.manifest 및 응용 프로그램에서 사용 하는 다른 사용자 지정 파일 형식 파일을 다운로드할 수 있도록 IIS 설정을 변경 해야 하는이 서버를 사용 하 여 응용 프로그램입니다.  
  
 IIS 서버를 사용 하 여 배포 하는 경우 inetmgr.exe를 실행 하 고 기본 웹 페이지에 대 한 새 파일 형식을 추가 합니다.  
  
- .Application 및.manifest 확장을 위한 MIME 형식을 "application/x-ms-응용 프로그램입니다." 여야 합니다. 다른 파일 형식에 대 한 MIME 형식을 "application/octet-stream으로 합니다.." 여야 합니다.  
  
- MIME 형식 확장을 사용 하 여 만든 경우 "*" 다운로드 파일 형식의 파일을 통해 MIME 형식이 "응용 프로그램/옥텟 스트림" 합니다. 그러나 (차단 된 파일 형식 예:.aspx 및.asmx를 다운로드할 수 없습니다.)  
  
  Windows Server에서 MIME 형식 구성에 대 한 자세한 내용은 참조 Microsoft 기술 자료 문서 KB326965, "IIS 6.0에서는 제공 알 수 없는 MIME 형식이 아닌"에서 [ http://support.microsoft.com/default.aspx?scid=kb; en-우리; 326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965)합니다.  
  
## <a name="content-type-mappings"></a>콘텐츠 형식 매핑  
 .Application 파일에 대 한 콘텐츠 형식 (MIME 형식이 라고도 함)에 HTTP를 통해 게시 하는 경우 "application/x-ms-응용 프로그램입니다." 이어야 합니다. 있는 경우 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 서버에 설치, 설정 됩니다를 자동으로 합니다. 이 설치 되지 않은 경우에 대 한 MIME 유형 연결을 만들어야 합니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램 vroot (또는 전체 서버).  
  
 IIS 서버를 사용 하 여 배포 하는 경우 inetmgr.exe를 실행 하 고 "application/x-ms-응용 프로그램의".application 확장명에 대 한 새 콘텐츠 형식을 추가 합니다.  
  
## <a name="http-compression-issues"></a>HTTP 압축 문제  
 사용 하 여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], HTTP 압축을 사용 하는 다운로드, 클라이언트에 보내는 데이터 스트림을 압축 GZIP 알고리즘을 사용 하는 웹 서버 기술이 수행할 수 있습니다. 클라이언트-이 경우 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-파일을 읽기 전에 스트림의 압축을 해제 합니다.  
  
 IIS를 사용 하는 경우에 HTTP 압축을 쉽게 사용할 수 있습니다. 그러나 HTTP 압축을 사용 하도록 설정 하면 활성화만 됩니다 특정 파일 형식에 대 한-즉, HTML 및 텍스트 파일입니다. 어셈블리 (.dll)에 대 한 압축을 사용 하려면 XML (.xml), 배포 매니페스트 (.application) 및 응용 프로그램 매니페스트 (.manifest)을 추가 해야 이러한 파일 형식은 압축 하도록 IIS 위한 형식의 목록에. 파일 형식 배포에 추가할 때까지 텍스트 및 HTML 파일은 압축 됩니다.  
  
 IIS에 대 한 자세한 내용은 참조 하세요. [HTTP 압축에 대 한 추가 문서 유형을 지정 하는 방법을](http://go.microsoft.com/fwlink/?LinkId=178459)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 배포 문제 해결](../deployment/troubleshooting-clickonce-deployments.md)   
 [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [응용 프로그램 배포 필수 조건](../deployment/application-deployment-prerequisites.md)
