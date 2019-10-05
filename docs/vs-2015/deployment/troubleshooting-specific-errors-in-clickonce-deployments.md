---
title: ClickOnce 배포 관련 오류 문제 해결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: troubleshooting
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 348cb15ebc348d6c0ece5e7118e896cc6a21b23b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62420152"
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>ClickOnce 배포 관련 오류 문제 해결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 배포 하는 경우 발생할 수 있는 다음과 같은 일반적인 오류가 나열을 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 하 고 각 문제를 해결 하는 단계를 제공 합니다.  
  
## <a name="general-errors"></a>일반 오류  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>경우.application 파일을 찾으려고 아무 일도 발생 하거나 Internet Explorer에서 XML 렌더링 또는 실행 하거나 다른 이름으로 저장 대화 상자가 나타나면  
 이 오류는 콘텐츠 형식 (MIME 형식 라고도 함)는 서버 또는 클라이언트에 잘못 등록 되었을 원인일 가능성이 큽니다.  
  
 먼저 서버 콘텐츠 형식을 "application/x-ms-응용 프로그램"을 사용 하 여.application 확장명을 연결 하려면 구성 되어 있는지 확인 합니다.  
  
 서버가 올바르게 구성 되어, 경우 되도록는 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 컴퓨터에 설치 됩니다. 경우는 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 가 설치 되어 계속 나타나면이 문제를 제거 하 고 다시 설치 하 고는 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 를 다시 클라이언트에서 콘텐츠 형식을 등록 합니다.  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>오류 메시지가 표시 되 면 "응용 프로그램을 검색할 수 없습니다. 배포에서 누락 된 파일"또는"응용 프로그램 다운로드가 중단 되었습니다, 네트워크 오류를 확인 하 고 나중에 다시 시도"  
 이 메시지는 하나 이상의 파일에서 참조 하 고 나타냅니다는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 매니페스트를 다운로드할 수 없습니다. 이 오류를 디버그 하는 가장 쉬운 방법은 URL 다운로드를 시도 하는 것을 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 라는 다운로드할 수 없습니다. 일부 원인은 다음과 같습니다.  
  
- 하는 경우 로그 파일 표시 "(403) 사용할 수 없음" 또는 "(404) 찾을 수 없음"이이 파일의 다운로드를 차단 하지 않도록 웹 서버에 구성 되어 있는지 확인 합니다. 자세한 내용은 [ClickOnce 배포 시 서버 및 클라이언트 구성 문제](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)를 참조하세요.  
  
- .Config 파일 서버에서 차단 되어 섹션을 참조 "다운로드를 설치 하려고 할 때 오류를 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .config 파일에 있는 응용 프로그램"이이 항목의 뒷부분에 나오는.  
  
- 이 때문에 발생 했는지 여부를 결정 합니다 `deploymentProvider` 배포 매니페스트의 URL가 정품 인증에 사용 된 URL 다른 위치를 가리키는 합니다.  
  
- 서버에서 모든 파일이 있는지 확인 합니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 로그 알려 주어 야는 파일을 찾을 수 없습니다.  
  
- 네트워크 연결 문제; 있는지 여부를 참조 하세요. 다운로드 하는 동안 클라이언트 컴퓨터가 오프 라인으로 전환한 경우이 메시지를 받을 수 있습니다.  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>.Config 파일에 있는 ClickOnce 응용 프로그램을 설치 하려고 할 때 다운로드 오류  
 기본적으로 Visual Basic Windows 기반 응용 프로그램을 App.config 파일을 포함합니다. 사용자가 해당 운영 체제 보안상의 이유로.config 파일의 설치를 차단 하기 때문에 Windows Server 2003을 사용 하는 웹 서버에서 설치 하려고 할 때 문제가 됩니다. 설치할.config 파일을 사용 하도록 설정 하려면 **".deploy" 파일 확장명을 사용 하 여** 에 **게시 옵션** 대화 상자.  
  
 또한 설정 해야 콘텐츠 형식 (MIME 형식 라고도 함) 적절 하 게.application,.manifest 및.deploy 파일에 대 한 합니다. 자세한 내용은 웹 서버 설명서를 참조 하세요.  
  
 자세한 내용은 "Windows Server 2003: 잠긴 콘텐츠 형식 " [서버 및 클라이언트 구성 문제 ClickOnce 배포에서](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)합니다.  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>오류 메시지: "응용 프로그램의 형식이 잘못 되었습니다." 로그 파일에 "XML 서명이 잘못 되었습니다."  
 매니페스트 파일을 업데이트 하 고 다시 서명 확인 합니다. 사용 하 여 응용 프로그램을 다시 게시 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 하거나 마법사를 사용 하 여 응용 프로그램을 다시 로그인 합니다.  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>서버에서 응용 프로그램을 업데이트 하지만 클라이언트 업데이트를 다운로드 하지 않습니다.  
 다음 작업 중 하나를 완료 하 여이 문제를 해결할 수 있습니다.  
  
- 검사는 `deploymentProvider` 배포 매니페스트의 URL입니다. 동일한 위치에서 비트를 업데이트 하 고 있는지 확인 하는 `deploymentProvider` 가리킵니다.  
  
- 배포 매니페스트의 업데이트 간격을 확인 합니다. 이 간격을 6 시간 마다 한 번씩 같은 일정 한 간격으로 설정 된 경우 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 이 간격이 경과할 때까지 업데이트에 대 한 검색 됩니다. 응용 프로그램이 시작 될 때마다 업데이트를 검색 하는 매니페스트를 변경할 수 있습니다. 업데이트 간격을 변경 하는 것은 업데이트가 설치 되는, 있지만 응용 프로그램 활성화 저하를 확인 하려면 개발 기간 동안 편리 합니다.  
  
- 시작 메뉴에서 응용 프로그램을 다시 시작 하십시오. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 백그라운드에서 업데이트를 발견 했을 수 있지만 다음 정품 인증에서 비트를 설치 하 라는 메시지가 표시 됩니다.  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>업데이트 하는 동안 다음 로그 항목에 오류가 나타날 수 있습니다. "배포에 대 한 참조 응용 프로그램 매니페스트에 정의 된 id를 일치 하지 않습니다"  
 이 오류는 서로 동기화 한 매니페스트에 어셈블리의 id에 대 한 설명을 했 고 배포 및 응용 프로그램 매니페스트를 수동으로 편집한 때문에 발생할 수 있습니다. 어셈블리의 id를 해당 이름, 버전, 문화권 및 공개 키 토큰으로 구성 됩니다. 프로그램 매니페스트에 id 설명을 확인 하 고 모든 차이점을 수정 합니다.  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>처음으로 로컬 디스크 또는 CD-ROM에서 활성화는 성공 하지만 후속 활성화 시작 메뉴에서 성공 하지  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 공급자 URL을 사용 하 여 응용 프로그램에 대 한 업데이트를 받습니다. URL가 가리키고 있는 위치가 올바른지 확인 합니다.  
  
#### <a name="error-cannot-start-the-application"></a>오류: "응용 프로그램을 시작할 수 없습니다."  
 이 오류 메시지는 일반적으로이 응용 프로그램을 설치 하는 문제 임을 나타냅니다는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 저장 합니다. 응용 프로그램에 오류가 발생 하거나 저장소 손상 되었습니다. 오류가 발생 알 로그 파일 수 있습니다.  
  
 다음을 수행 해야 합니다.  
  
- 배포 매니페스트의 id, 응용 프로그램 매니페스트의 id 및 기본 응용 프로그램 EXE의 id 모든 고유한 지 확인 합니다.  
  
- 파일 경로가 100 자를 초과 되지 않았는지 확인 합니다. 너무 긴 파일 경로 포함 하는 응용 프로그램을 저장할 수 있습니다 최대 경로에 대 한 제한을 초과할 수 있습니다. 경로 단축 하 고 다시 설치 합니다.  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>응용 프로그램 구성 파일에서 PrivatePath 설정이 무시 되며  
 PrivatePath (Fusion 검색 경로)를 사용 하려면 응용 프로그램에는 완전 신뢰 권한을 요청 해야 합니다. 완전 신뢰를 요청 하 고 다시 시도 하도록 응용 프로그램 매니페스트를 변경해 보세요.  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>제거하는 동안 "응용 프로그램 제거 실패"메시지가 나타납니다.  
 이 메시지는 일반적으로 응용 프로그램이 이미 제거 되었거나 또는 저장소가 손상 되었음을 나타냅니다. 클릭 한 후 **확인**서 **프로그램 추가/제거** 항목이 제거 됩니다.  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>설치 하는 동안 메시지가 표시 하는 플랫폼 종속성이 설치 되지 않습니다 됩니다.  
 GAC (전역 어셈블리 캐시)에 응용 프로그램을 실행 하기 위해 필요한 필수 구성 요소가 없습니다.  
  
## <a name="publishing-with-visual-studio"></a>Visual Studio 사용 하 여 게시  
  
#### <a name="publishing-in-visual-studio-fails"></a>Visual Studio에서 게시 실패  
 수 있는 권한이 서버에 게시를 대상으로 하는 것을 확인 합니다. 예를 들어 터미널 서버의 컴퓨터 관리자가 아니라 일반 사용자로 로그인 하는 경우 아마도 하지 해야 로컬 웹 서버에 게시 하는 데 필요한 권한입니다.  
  
 URL로 게시 하는 경우 대상 컴퓨터에 FrontPage Server Extensions를 사용할 수 있는지 확인 합니다.  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>오류 메시지: 웹 사이트를 만들 수 없습니다. '\<사이트 >'입니다. FrontPage Server Extensions와 통신 하기 위한 구성 요소가 설치 되지 않습니다.  
 Microsoft Visual Studio Web Authoring 구성 요소에서 게시 중인 컴퓨터에 설치 했는지 확인 합니다. Express 사용자에 대 한이 구성 요소는 기본적으로 설치 되지 않았습니다. 자세한 내용은 [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310)를 참조하세요.  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>오류 메시지: Could not find file 'Microsoft.Windows.Common-Controls, Version=6.0.0.0, Culture=*, PublicKeyToken=6595b64144ccf1df, ProcessorArchitecture=\*, Type=win32'  
 이 오류 메시지에 사용 하도록 설정 하는 비주얼 스타일을 사용 하 여 WPF 응용 프로그램을 게시 하려고 할 때 나타납니다. 이 문제를 해결 하려면 참조 [방법: 사용 하도록 설정 하는 비주얼 스타일을 사용 하 여 WPF 응용 프로그램을 게시](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)합니다.  
  
## <a name="using-mage"></a>마법사를 사용 하 여  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>인증서 저장소와 받은 빈 메시지 상자에 인증서를 사용 하 여 로그인 하려고 했습니다.  
 에 **서명** 대화 상자에서 수행 해야 합니다.  
  
- 선택 **저장된 된 인증서로 서명**, 및  
  
- 목록에서 인증서를 선택 합니다. 첫 번째 인증서가 기본적으로 선택 합니다.  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>서명 하지 않음 "단추를 클릭 하면 예외  
 이 문제는 알려진된 버그가 있습니다. 모든 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 매니페스트는 서명 되어야 합니다. 서명 옵션 중 하나를 선택 하 고 클릭 **확인**합니다.  
  
## <a name="additional-errors"></a>추가 오류  
 다음 표에서 사용자가 설치 된 클라이언트 컴퓨터 사용자 받을 수 있는 몇 가지 일반적인 오류 메시지는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램입니다. 가장 큰 원인은 오류 설명은 옆에 있는 각 오류 메시지가 나열 됩니다.  
  
|오류 메시지|설명|  
|-------------------|-----------------|  
|응용 프로그램을 시작할 수 없습니다. 응용 프로그램 게시자에 게 문의 합니다.<br /><br /> 응용 프로그램을 시작할 수 없습니다. 응용 프로그램 공급 업체를 지원을 요청 합니다.|이 응용 프로그램을 시작할 수 없습니다, 그리고 및 다른 특정 한 이유를 확인할 수 있습니다 때 발생 하는 일반 오류 메시지입니다. 응용 프로그램이 어떤 이유로 든 손상 된이 즉 자주 또는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 저장소가 손상 되었습니다.|  
|계속할 수 없습니다. 응용 프로그램 형식이 잘못 되었습니다. 응용 프로그램 게시자에 게 문의 합니다.<br /><br /> 응용 프로그램 유효성 검사에 실패 했습니다. 계속할 수 없습니다.<br /><br /> 응용 프로그램 파일을 검색할 수 없습니다. 배포의 파일이 손상 되었습니다.|배포에서 매니페스트 파일 중 하나가 유효 하지 않은 구문이 이거나 해당 파일을 사용 하 여 조정할 수 없는 해시를 포함 합니다. 이 오류는 어셈블리 내에 포함 하는 매니페스트가 손상 하는 것을 나타낼 수도 있습니다. 다시 배포를 만드는 응용 프로그램을 다시 컴파일할 또는 찾아서 매니페스트에서 오류를 수동으로 수정 합니다.|  
|응용 프로그램을 검색할 수 없습니다. 인증 오류입니다.<br /><br /> 응용 프로그램 설치에 실패 했습니다. 서버의 응용 프로그램 파일을 찾을 수 없습니다. 응용 프로그램 게시자 또는 관리자에 게 문의 합니다.|배포에서 하나 이상의 파일에 액세스할 수 있는 권한이 없기 때문에 다운로드할 수 없습니다. 배포에서 파일 중 하나는 보호 된 파일을 처리 하는 웹 서버 확장 끝나는 경우 발생할 수 있는 웹 서버에서 반환 되는 403 권한 없음 오류 때문일 수 있습니다. 또한 응용 프로그램의 파일 중 하나 이상을 포함 하는 디렉터리에 액세스 하기 위해 사용자 이름과 암호를 필요할 수 있습니다.|  
|응용 프로그램을 다운로드할 수 없습니다. 응용 프로그램에 필요한 파일이 없습니다. 응용 프로그램 공급 업체 또는 시스템 관리자에 게 문의 합니다.|서버에서 하나 이상의 응용 프로그램 매니페스트에 나열 된 파일을 찾을 수 없습니다. 배포의 모든 종속 파일을 업로드 하 고 다시 시도 확인 합니다.|  
|응용 프로그램을 다운로드 하지 못했습니다. 네트워크 연결을 확인 하거나 시스템 관리자 또는 네트워크 서비스 공급자에 게 문의 합니다.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 서버에 네트워크 연결을 설정할 수 없습니다. 서버 가용성 및 네트워크의 상태를 검사 합니다.|  
|URLDownloadToCacheFile 못했으며 HRESULT '\<수 >'입니다. 다운로드 하는 동안 오류가 발생 '\<파일 >'입니다.|사용자가 Internet Explorer의 고급 보안 옵션 설정 "보안 사이 전환할 때 경고 및 비보안 모드" 배포 대상 컴퓨터와 보안 사이트를 설치 하는 ClickOnce 응용 프로그램의 설치 URL 안전 하지 않은에서 리디렉션된 경우 (또는 반대로), Internet Explorer 경고를 중단 하기 때문에 설치가 실패 합니다.<br /><br /> 이 해결 하려면 다음 중 하나를 수행할 수 있습니다.<br /><br /> -보안 옵션의 선택을 취소 합니다.<br />-확인 하는지 설치 URL 보안 모드를 변경 하는 방식으로 리디렉션되지 않습니다.<br />-리디렉션을 완전히 제거 하 고 실제 설치 URL을 가리키도록 합니다.|  
|오류가 하드 디스크에 쓸을 발생 했습니다. 있을 공간이 부족 하 여 사용 가능한 디스크. 응용 프로그램 공급 업체 또는 시스템 관리자에 게 문의 합니다.|이 응용 프로그램을 저장 하는 데 부족 한 디스크 공간을 나타낼 수 있습니다 하지만 응용 프로그램 파일 드라이브에 저장 하려는 경우는 보다 일반적인 I/O 오류를 나타낼 수도 있습니다.|  
|응용 프로그램을 시작할 수 없습니다. 디스크에서 사용 가능한 공간이 충분 하지 않습니다.|하드 디스크가 꽉 찼습니다. 공간을 지우고 응용 프로그램을 다시 실행 하려고 합니다.|  
|너무 많은 배포 된 정품 인증을 한 번에 로드 하려고 합니다.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 동시에 시작할 수 있는 다른 응용 프로그램의 수를 제한 합니다. 이것은 주로을 로컬에 대 한 서비스 거부 공격을 사용 하면 악의적인 시도 방지할 수 있도록 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 서비스를 빠르게 연속 해 서에서 반복적으로 동일한 응용 프로그램을 시작 하려고만의 단일 인스턴스를 사용 하 여 결과적으로, 사용자는 응용 프로그램입니다.|  
|네트워크를 통해 바로 가기 키를 활성화할 수 없습니다.|바로 가기는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 로컬 하드 디스크에만 시작할 수 있습니다. 원격 서버에서 바로 가기 파일을 가리키는 URL을 열어 시작할 수는 없습니다.|  
|응용 프로그램이 부분 신뢰 환경에서 온라인으로 실행 하려면 너무 큽니다. 응용 프로그램 공급 업체 또는 시스템 관리자에 게 문의 합니다.|부분 신뢰에서 실행 되는 응용 프로그램을 기본적으로 250MB 온라인 응용 프로그램 할당량 크기의 절반 보다 클 수 없습니다.|  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce 배포 문제 해결](../deployment/troubleshooting-clickonce-deployments.md)
