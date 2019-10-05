---
title: 원격 디버그 ASP.NET Core에서 원격 IIS 컴퓨터 | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 48c5d365c632deb4d654d5115a141ba9933d7a6f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410238"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Visual Studio에서 원격 IIS 컴퓨터의 원격 디버그 ASP.NET Core
IIS에 배포 된 ASP.NET 응용 프로그램을 디버깅 하려면 설치 하 고 앱을 배포할 컴퓨터에서 원격 도구를 실행 한 다음 Visual Studio에서 실행 중인 앱에 연결 합니다.

![원격 디버거 구성 요소](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

이 가이드에서는 설정 및 Visual Studio ASP.NET Core 구성 하 고, IIS로 배포 하 고 Visual Studio에서 원격 디버거를 연결 하는 방법을 설명 합니다. 원격 디버그 ASP.NET 4.5.2 참조 하세요 [IIS 컴퓨터의 원격 디버그 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)합니다. 배포 하 고 Azure를 사용 하 여 IIS에서 디버깅할 수도 있습니다. Azure App Service에 대해 쉽게 배포 하 고 디버그할 수의 IIS와 원격 디버거 중 하나를 사용 하 여 미리 구성 된 인스턴스에서 [스냅숏 디버거](../debugger/debug-live-azure-applications.md) 하거나 [서버 탐색기에서 디버거를 연결](../debugger/remote-debugging-azure.md)합니다.

## <a name="prerequisites"></a>전제 조건

::: moniker range=">=vs-2019"
Visual Studio 2019은이 문서에 나와 있는 단계를 수행 해야 합니다.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017은이 문서에 나와 있는 단계를 수행 해야 합니다.
::: moniker-end

이러한 절차 이러한 서버 구성에서 테스트 되었습니다.
* Windows Server 2012 R2 및 IIS 8
* Windows Server 2016 및 IIS 10

## <a name="network-requirements"></a>네트워크 요구 사항

프록시를 통해 연결 하는 두 컴퓨터 간에 디버깅이 지원 되지 않습니다. 국가 간 높은 대기 시간 또는 낮은 대역폭 연결을 인터넷에 접속 등을 통해 또는 인터넷을 통해 디버깅 권장 되지 않습니다 및 실패 하거나 느리고 수 있습니다. 요구 사항의 전체 목록은 참조 하세요 [요구 사항](../debugger/remote-debugging.md#requirements_msvsmon)합니다.

## <a name="app-already-running-in-iis"></a>IIS에서 이미 실행 중인 앱?

이 문서에는 Windows 서버에 iis 기본 구성 설정 및 Visual Studio에서 앱을 배포 하는 단계가 포함 됩니다. 이러한 단계는 서버에 필요한 구성 요소를 설치, 앱이 올바르게 실행할 수 있는지 및 원격 디버깅할 준비가 되도록 포함 됩니다.

* 앱은 IIS에서 실행 되 고 원격 디버거를 다운로드 하 고 디버깅을 시작으로 이동 하세요만 하려는 경우 [다운로드 하 여 Windows Server에서 원격 도구 설치](#BKMK_msvsmon)합니다.

* 앱 설정 되어 있는지를 배포 해야 하는 데 도움이 필요 하 고이 항목의 모든 단계에 따라 디버그할 수 있도록 IIS에서 올바르게 실행 했습니다.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio 컴퓨터에서 ASP.NET Core 응용 프로그램 만들기

1. 새 ASP.NET Core 웹 애플리케이션을 만듭니다. 

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 입력 **Ctrl + Q** 입력 검색 상자를 열려면 **asp.net**, 선택 **템플릿**를 선택한 **새 ASP.NET Core 웹 응용 프로그램 만들기** . 나타나는 대화 상자에서 프로젝트 이름을 **MyASPApp**를 선택한 후 **만들기**합니다. 그런 다음 선택 **웹 응용 프로그램 (모델-뷰-컨트롤러)** 를 선택한 후 **만들기**합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017에서 선택 **파일 > 새로 만들기 > 프로젝트**을 선택한 후 **시각적 C# > 웹 > ASP.NET Core 웹 응용 프로그램**합니다. ASP.NET Core 템플릿 섹션에서 선택 **웹 응용 프로그램 (모델-뷰-컨트롤러)** 합니다. ASP.NET Core 2.1 선택 되어 있는지 확인 하는 **Docker 지원 활성화** 선택 하지 않으면 하 고 **인증** 로 설정 되어 **인증 안 함**합니다. 프로젝트 이름을 **MyASPApp**합니다.
    ::: moniker-end

4. About.cshtml.cs 파일을 열고 중단점을 설정 합니다 `OnGet` 메서드 (이전 템플릿에서 HomeController.cs 대신 열고에서 중단점을 설정 합니다 `About()` 메서드).

## <a name="bkmk_configureIIS"></a> 설치 하 고 Windows Server에서 IIS를 구성 합니다.

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server에서 브라우저 보안 설정 업데이트

보안 강화 구성 (기본적으로 사용 됩니다) Internet Explorer에서 사용 하는 경우 일부 웹 서버 구성 요소를 다운로드할 수 있도록 신뢰할 수 있는 사이트로 일부 도메인을 추가 해야 있습니다. 으로 이동 하 여 신뢰할 수 있는 사이트 추가 **인터넷 옵션 > 보안 > 신뢰할 수 있는 사이트 > 사이트**합니다. 다음 도메인을 추가 합니다.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

소프트웨어를 다운로드 하면 다양 한 웹 사이트 스크립트 및 리소스를 로드 하는 권한 부여에 대 한 요청 표시 될 수 있습니다. 이러한 리소스 중 일부는 필요 하지 않지만 프로세스를 간소화 하기 위해 클릭 **추가** 메시지가 표시 되 면 합니다.

## <a name="install-aspnet-core-on-windows-server"></a>Windows Server에서 ASP.NET Core를 설치 합니다.

1. 호스팅 시스템에 [.NET Core Windows Server 호스팅](https://aka.ms/dotnetcore-2-windowshosting) 번들을 설치합니다. 번들은 .NET Core 런타임, .NET Core 라이브러리 및 ASP.NET Core 모듈을 설치합니다. 더 자세한 지침은 [IIS에 게시](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)합니다.

    > [!NOTE]
    > 시스템이 인터넷에 연결되지 않은 경우 *[Microsoft Visual C++ 2015 재배포 가능 패키지](https://www.microsoft.com/download/details.aspx?id=53840)* 를 설치한 후에 .NET Core Windows Server 호스팅 번들을 설치합니다.

3. 시스템을 다시 시작하거나 명령 프롬프트에서 **net stop was /y**에 이어 **net start w3svc**를 실행하여 시스템 PATH에 대한 변경 내용을 선택합니다.

## <a name="choose-a-deployment-option"></a>배포 옵션을 선택 합니다.

IIS에 앱을 배포 하는 데 도움이 필요, 이러한 옵션을 고려 합니다.

* IIS에서 게시 설정 파일을 만들고 Visual Studio에서 설정 가져오기 하 여 배포 합니다. 일부 시나리오에서는 앱을 배포 하는 빠른 방법을 이것이입니다. 게시 설정 파일을 만들 때 사용 권한은 자동으로 설정 됩니다 IIS에서.

* 로컬 폴더에 게시 하 고 IIS에서 준비 된 앱 폴더에 기본 방법으로 출력을 복사 하 여 배포 합니다.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(선택 사항) 게시 설정 파일을 사용 하 여 배포

이 옵션을 사용할 수 있습니다 게시 설정 파일을 만들고 Visual Studio로 가져오기.

> [!NOTE]
> 이 배포 방법은 웹 배포를 사용합니다. 웹 배포를 수동으로 구성에 Visual Studio 설정을 가져오지 않고 하려는 경우에 호스팅 서버에 대 한 웹 배포 3.6 대신 웹 배포 3.6을 설치할 수 있습니다. 그러나 수동으로 웹 배포을 구성 하는 경우 해야 서버에 있는 앱 폴더 사용 권한을 확인 하 고 올바른 값을 사용 하 여 구성 되어 있는지 확인 (참조 [ASP.NET 웹 구성 사이트](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>설치 및 Windows server 호스팅 서버에 대 한 웹 배포를 구성 합니다.

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server의 IIS에서 게시 설정 파일 만들기

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio에서 게시 설정 가져오기 및 배포

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

앱을 성공적으로 배포한 후 자동으로 시작해야 합니다. Visual Studio에서 앱 시작 되지 않는 경우 IIS에서 앱을 시작 합니다. ASP.NET Core의 경우 **DefaultAppPool**에 대한 애플리케이션 풀 필드가 **관리 코드 없음**으로 설정되었는지 확인해야 합니다.

1. 에 **설정** 대화 상자, 클릭 하 여 디버깅을 사용 하도록 설정 **다음**, 선택는 **디버그** 구성을 선택한 후 **에서 추가 파일 제거 대상** 아래의 합니다 **파일 게시** 옵션입니다.

    > [!NOTE]
    > 디버깅을 비활성화 하는 릴리스 구성을 선택 하면 합니다 *web.config* 게시할 때 파일입니다.

1. 클릭 **저장할** 한 다음 앱을 다시 게시 합니다.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(선택 사항) 로컬 폴더에 게시 하 여 배포

RoboCopy, Powershell을 사용 하 여 IIS에 응용 프로그램을 복사 하려는 경우 수동으로 파일을 복사 하려는 앱을 배포 하려면이 옵션을 사용할 수 있습니다.

### <a name="BKMK_deploy_asp_net"></a> Windows Server 컴퓨터에서 ASP.NET 웹 사이트 구성

1. Windows 탐색기를 열고 새 폴더를 만듭니다 **C:\Publish**ASP.NET 프로젝트를 나중에 배포할가 있습니다.

2. 열려 있지 않으면 엽니다는 **인터넷 정보 서비스 (IIS) 관리자**합니다. (서버 관리자의 왼쪽된 창에서 선택 **IIS**합니다. 서버를 마우스 오른쪽 단추로 클릭하고 **IIS(인터넷 정보 서비스) 관리자**를 선택합니다.)

3. 아래 **연결** 왼쪽된 창에서로 이동 **사이트**합니다.

4. 선택 합니다 **기본 웹 사이트**, 선택 **기본 설정**, 설정 및는 **실제 경로** 에 **C:\Publish**합니다.

4. **기본 웹 사이트** 노드를 마우스 오른쪽 단추로 클릭하고 **응용 프로그램 추가**를 선택합니다.

5. 설정 합니다 **별칭** 필드를 **MyASPApp**, 응용 프로그램 풀 기본값 (**DefaultAppPool**), 설정 및 합니다 **실제 경로** 를 **C:\Publish**합니다.

6. 아래 **연결**를 선택 **응용 프로그램 풀**합니다. 오픈 **DefaultAppPool** 응용 프로그램 풀 필드를 설정 하 고 **관리 코드 없음**합니다.

7. 새 사이트를 IIS 관리자를 마우스 오른쪽 단추로 클릭, 선택 **사용 권한 편집**, 해당 IUSR, IIS_IUSRS, 또는 사용자 웹 앱에 대 한 액세스는 읽기 및 실행 권한이 있는 권한 있는 사용자에 대해 구성 되었는지 확인 합니다.

    액세스를 사용 하 여 이러한 사용자 중 하나로 표시 되지 않으면, IUSR 읽기 및 실행 권한이 있는 사용자로 추가 하는 단계를 통해 이동 합니다.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>게시 하 고 Visual Studio에서 로컬 폴더에 게시 하 여 앱 배포

게시 하 고 파일 시스템 또는 다른 도구를 사용 하 여 앱을 배포할 수도 있습니다.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> 다운로드 하 여 Windows Server에서 원격 도구 설치

Visual Studio의 버전과 일치 하는 원격 도구의 버전을 다운로드 합니다.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="BKMK_setup"></a> Windows Server에서 원격 디버거 설정

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 추가 사용자에 대 한 사용 권한을 추가 하는 인증 모드를 변경 하거나 원격 디버거의 포트 번호에 필요한 경우 참조 [원격 디버거 구성](../debugger/remote-debugging.md#configure_msvsmon)합니다.

원격 디버거 서비스 실행에 대 한 내용은 참조 하세요 [원격 디버거를 서비스로 실행](../debugger/remote-debugging.md#bkmk_configureService)합니다.

## <a name="BKMK_attach"></a> Visual Studio 컴퓨터에서 ASP.NET 애플리케이션에 연결

1. Visual Studio 컴퓨터에서 디버그 하려는 된 솔루션을 엽니다 (**MyASPApp** 이 문서의 모든 단계를 따르는 경우).
2. Visual Studio에서 클릭 **디버그 > 프로세스에 연결** (Ctrl + Alt + P).

    > [!TIP]
    > Visual Studio 2017 이상 버전에서 이전에 연결을 사용 하 여 동일한 프로세스에 다시 **디버그 > 프로세스에 다시 연결 하는 중...** (Shift + Alt + P)입니다.

3. 한정자 필드에 설정할  **\<원격 컴퓨터 이름 >** 누릅니다 **Enter**합니다.

    Visual Studio 형식으로 표시 되는 컴퓨터 이름에 필요한 포트를 추가 함을 확인 합니다.  **\<원격 컴퓨터 이름 >: 포트**

    ::: moniker range=">=vs-2019"
    Visual Studio 2019에 나타납니다  **\<원격 컴퓨터 이름 >: 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017에서 표시 되어야  **\<원격 컴퓨터 이름 >: 4022**
    ::: moniker-end
    포트는 필수입니다. 찾을 수 없으면 포트 번호를 수동으로 추가 합니다.

4. **새로 고침**을 클릭합니다.
    일부 프로세스가 **사용 가능한 프로세스** 창에 표시됩니다.

    모든 프로세스가 표시 되지 않는 경우 (포트는 필수) 원격 컴퓨터 이름 대신 IP 주소를 사용해 보세요. 사용할 수 있습니다 `ipconfig` IPv4 주소를 가져오려면 명령줄에서.

    사용 하려는 경우는 **찾을** 단추를 해야 할 수 있습니다 [UDP 포트 3702 열고](#bkmk_openports) 서버의 합니다.

5. **모든 사용자의 프로세스 표시**를 선택합니다.

6. 앱을 빠르게 찾으려면 프로세스 이름의 첫 글자를 입력 합니다.

    * 선택 **dotnet.exe**합니다.

      여러 프로세스를 보여 주는 경우 **dotnet.exe**를 확인 합니다 **사용자 이름** 열입니다. 일부 시나리오에서는 합니다 **사용자 이름** 와 같은 앱 풀 이름, 열에 표시 **IIS APPPOOL\DefaultAppPool**합니다. 응용 프로그램 풀을 표시, 올바른 프로세스를 식별 하는 간편한 방법은 새 디버그 하려는 앱 인스턴스에 대 한 응용 프로그램 풀 이름이 고 다음에서 쉽게 찾을 수 있습니다 합니다 **사용자 이름** 열입니다.

    * IIS 시나리오도 있습니다 앱 이름을 프로세스 목록에서와 같은 **MyASPApp.exe**합니다. 대신이 프로세스에 연결할 수 있습니다.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. **연결**을 클릭합니다.

8. 원격 컴퓨터의 웹 사이트를 엽니다. 브라우저에서 **http://\<원격 컴퓨터 이름>** 으로 이동합니다.

    ASP.NET 웹 페이지가 표시됩니다.

9. 실행 중인 ASP.NET 응용 프로그램에 대 한 링크를 클릭 합니다 **에 대 한** 페이지입니다.

    Visual Studio에서 중단점이 적중됩니다.

## <a name="bkmk_openports"></a> 문제 해결: Windows Server에서 필요한 포트를 열려면

대부분의 설치 프로그램에서 ASP.NET와 원격 디버거 설치를 통해 필요한 포트가 열려 있습니다. 그러나 포트가 열려 있는지 확인 해야 합니다.

> [!NOTE]
> Azure VM에서 포트를 통해 열어야 합니다 [네트워크 보안 그룹](/azure/virtual-machines/windows/nsg-quickstart-portal)합니다.

필요한 포트:

* 80-IIS에 대 한 필요합니다.
::: moniker range=">=vs-2019"
* 4024-Visual Studio 2019 원격 디버깅을 위해 필요 합니다. (참조 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) 자세한).
::: moniker-end
::: moniker range="vs-2017"
* 4022-Visual Studio 2017에서 원격 디버깅을 위해 필요 합니다. (참조 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) 자세한).
::: moniker-end
* UDP 3702-(선택 사항) 검색 포트 사용 하도록 설정 하는 **찾을** 단추 Visual Studio에서 원격 디버거를 연결 하는 경우.

1. Windows Server에서 포트를 열려면 합니다 **시작** 메뉴에서 검색 **Windows Firewall with Advanced Security**합니다.

2. 선택한 **인바운드 규칙 > 새 규칙 > 포트**를 클릭 하 고 **다음**합니다. (선택 UDP 3702 **아웃 바운드 규칙** 대신 합니다.)

3. 아래 **특정 로컬 포트**포트 번호를 입력, 클릭 **다음**합니다.

4. 클릭 **연결 허용**, 클릭 **다음**합니다.

5. 하나 이상의 네트워크 형식을 선택 포트에 대해 사용 하도록 설정 하 고 클릭 **다음**합니다.

    선택한 유형은 원격 컴퓨터가 연결된 네트워크를 포함해야 합니다.
6. 이름을 추가 합니다 (예를 들어 **IIS**, **Web Deploy**, 또는 **msvsmon**) 인바운드 규칙을 클릭 **마침**합니다.

    인바운드 규칙 또는 아웃바운드 규칙 목록에 새 규칙이 표시되어야 합니다.

    Windows 방화벽 구성에 대 한 자세한 내용은 참조 하세요 [원격 디버깅용 Windows 방화벽 구성](../debugger/configure-the-windows-firewall-for-remote-debugging.md)합니다.

3. 기타 필요한 포트에 대 한 추가 규칙을 만듭니다.
