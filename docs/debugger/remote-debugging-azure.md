---
title: 원격 디버그 ASP.NET Core에서 IIS 및 Azure | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 2fbdc27ba7a3ae69494bf8129e4c870f325fe621
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824430"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Visual Studio에서 Azure에는 IIS에서 ASP.NET Core 원격 디버그

이 가이드에는 설정 및 Visual Studio ASP.NET Core 앱을 구성 하 고, Azure를 사용 하 여 IIS에 배포 하 고 Visual Studio에서 원격 디버거를 연결 하는 방법을 설명 합니다.

Azure의 원격 디버그 하는 권장된 방법은 시나리오에 따라 달라 집니다.

* Azure App Service에서 ASP.NET Core를 디버깅 하려면 참조 [스냅숏 디버거를 사용 하 여 디버그 하는 Azure 앱](../debugger/debug-live-azure-applications.md)합니다. 이것이 권장된 방법입니다.
* 보다 일반적인 디버깅 기능을 사용 하 여 Azure App Service에서 ASP.NET Core를 디버깅 하려면이 항목의 단계에 따라 (섹션을 참조 하세요 [Azure App Service에서 원격 디버깅](#remote_debug_azure_app_service)).

    이 시나리오에서는 Azure Visual Studio에서 앱을 배포 해야 하지만 수동으로 설치 하거나 다음 그림에 표시 된 대로 IIS 또는 (이러한 구성 요소는 점선으로 표시 됨) 원격 디버거를 구성할 필요가 없습니다.

    ![원격 디버거 구성 요소](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Azure VM에서 IIS를 디버깅 하려면이 항목의 단계에 따라 (섹션을 참조 하세요 [Azure VM에서 원격 디버깅](#remote_debug_azure_vm)). Iis 사용자 지정된 구성을 사용할 수 있습니다 하지만 설치 및 배포 단계는 더 복잡 합니다.

    Azure VM에 대해 Azure Visual Studio에서 앱 배포 해야 하며, 해야 IIS 역할 및 원격 디버거를 수동으로 설치 하려면 다음 그림에 나와 있는 것 처럼.

    ![원격 디버거 구성 요소](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Azure Service Fabric에서 ASP.NET Core를 디버깅 하려면 참조 [원격 Service Fabric 응용 프로그램을 디버그](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)합니다.

> [!WARNING]
> 이 자습서의 단계를 완료 하는 경우 만든 Azure 리소스를 삭제 해야 합니다. 이렇게 불필요 한 요금이 발생을 방지할 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

::: moniker range=">=vs-2019"
Visual Studio 2019은이 문서에 나와 있는 단계를 수행 해야 합니다.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017은이 문서에 나와 있는 단계를 수행 해야 합니다.
::: moniker-end

### <a name="network-requirements"></a>네트워크 요구 사항

프록시를 통해 연결 하는 두 컴퓨터 간에 디버깅이 지원 되지 않습니다. 국가 간 높은 대기 시간 또는 낮은 대역폭 연결에서는 인터넷에 접속 등을 통해 또는 인터넷을 통해 디버깅 권장 되지 않습니다 및 실패 하거나 느리고 수 있습니다. 요구 사항의 전체 목록은 참조 하세요 [요구 사항](../debugger/remote-debugging.md#requirements_msvsmon)합니다.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Visual Studio 컴퓨터에서 ASP.NET Core 응용 프로그램 만들기

1. 새 ASP.NET Core 응용 프로그램을 만듭니다.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 입력 **Ctrl + Q** 입력 검색 상자를 열려면 **asp.net**, 선택 **템플릿**를 선택한 **새 ASP.NET Core 웹 응용 프로그램 만들기** . 나타나는 대화 상자에서 프로젝트 이름을 **MyASPApp**를 선택한 후 **만들기**합니다. 그런 다음 선택 **웹 응용 프로그램 (모델-뷰-컨트롤러)** 를 선택한 후 **만들기**합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017에서 선택 **파일 > 새로 만들기 > 프로젝트**을 선택한 후 **시각적 C# > 웹 > ASP.NET Core 웹 응용 프로그램**합니다. ASP.NET Core 템플릿 섹션에서 선택 **웹 응용 프로그램 (모델-뷰-컨트롤러)** 합니다. ASP.NET Core 2.1 선택 되어 있는지 확인 하는 **Docker 지원 활성화** 선택 하지 않으면 하 고 **인증** 로 설정 되어 **인증 안 함**합니다. 프로젝트 이름을 **MyASPApp**합니다.
    ::: moniker-end

1. About.cshtml.cs 파일을 열고 중단점을 설정 합니다 `OnGet` 메서드 (이전 템플릿에서 HomeController.cs 대신 열고에서 중단점을 설정 합니다 `About()` 메서드).

## <a name="remote_debug_azure_app_service"></a> Azure App Service에 ASP.NET Core 원격 디버그

Visual Studio에서 게시 하 고 IIS의 인스턴스를 완전히 프로 비전 된 앱을 디버그 신속 하 게 수 있습니다. 그러나 IIS 구성을 미리 설정 됩니다 하 고 사용자 지정할 수 없습니다. 자세한 내용은 참조 [Visual Studio를 사용 하 여 Azure에 ASP.NET Core 웹 앱 배포](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)합니다. (IIS를 사용자 지정 하는 기능을 할 경우 시도 디버깅는 [Azure VM](#remote_debug_azure_vm).)

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>원격 디버그 서버 탐색기를 사용 하 고 앱을 배포 하려면

1. Visual Studio에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 선택 **게시**합니다.

    게시 프로필을 이전에 구성한 경우 **게시** 창이 나타납니다. 클릭 **새 프로필**합니다.

1. 선택 **Azure App Service** 에서 합니다 **게시** 대화 상자에서 **새로 만들기**, 게시할 프롬프트를 따릅니다.

    자세한 지침은 [Visual Studio를 사용하여 Azure에 ASP.NET Core 웹앱 배포](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)를 참조하세요.

    ![Azure App Service에 게시](../debugger/media/remotedbg_azure_app_service_profile.png)

1. 오픈 **서버 탐색기** (**뷰** > **서버 탐색기**), App Service 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 선택 **디버거연결**.

1. 실행 중인 ASP.NET 응용 프로그램에 대 한 링크를 클릭 합니다 **에 대 한** 페이지입니다.

    Visual Studio에서 중단점이 적중됩니다.

    이제 끝났습니다! 이 항목의에서 단계에서는 나머지는 Azure VM에서 원격 디버깅에 적용 됩니다.

## <a name="remote_debug_azure_vm"></a> Azure VM의 원격 디버그 ASP.NET Core

Windows 서버에 대 한 Azure VM 만들기 지정 하 고 설치 및 IIS 및 기타 필수 소프트웨어 구성 요소를 구성 합니다. 이 Azure App Service에 배포 하는 보다 많은 시간이 걸리는 및이 자습서의 나머지 단계를 따라야 합니다.

이러한 절차 이러한 서버 구성에서 테스트 되었습니다.
* Windows Server 2012 R2 및 IIS 8
* Windows Server 2016 및 IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Azure VM에서 IIS에서 이미 실행 되는 앱?

이 문서에는 Windows 서버에 iis 기본 구성 설정 및 Visual Studio에서 앱을 배포 하는 단계가 포함 됩니다. 이러한 단계는 서버 앱을 제대로 실행할 수 있는지 및 원격 디버깅할 준비가 설치 필수 구성 요소에 포함 되어 있습니다.

* 앱은 IIS에서 실행 되 고 원격 디버거를 다운로드 하 고 디버깅을 시작으로 이동 하세요만 하려는 경우 [다운로드 하 여 Windows Server에서 원격 도구 설치](#BKMK_msvsmon)합니다.

* 앱 설정 되어 있는지를 배포 해야 하는 데 도움이 필요 하 고이 항목의 모든 단계에 따라 디버그할 수 있도록 IIS에서 올바르게 실행 했습니다.

  * 시작 하기 전에에 설명 된 모든 단계를 따릅니다 [설치 및 실행된 IIS](/azure/virtual-machines/windows/quick-create-portal)합니다.

  * 네트워크 보안 그룹에 포트 80을 여는 경우 열 수도 합니다 [포트를 수정](#bkmk_openports) 원격 디버거 (4024 또는 4022)에 대 한 합니다. 이런 방식으로 나중에 열 필요가 없습니다.

### <a name="update-browser-security-settings-on-windows-server"></a>Windows Server에서 브라우저 보안 설정 업데이트

보안 강화 구성 (기본적으로 사용 됩니다) Internet Explorer에서 사용 하는 경우 일부 웹 서버 구성 요소를 다운로드할 수 있도록 신뢰할 수 있는 사이트로 일부 도메인을 추가 해야 있습니다. 으로 이동 하 여 신뢰할 수 있는 사이트 추가 **인터넷 옵션 > 보안 > 신뢰할 수 있는 사이트 > 사이트**합니다. 다음 도메인을 추가 합니다.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

소프트웨어를 다운로드 하면 다양 한 웹 사이트 스크립트 및 리소스를 로드 하는 권한 부여에 대 한 요청 표시 될 수 있습니다. 이러한 리소스 중 일부는 필요 하지 않지만 프로세스를 간소화 하기 위해 클릭 **추가** 메시지가 표시 되 면 합니다.

### <a name="install-aspnet-core-on-windows-server"></a>Windows Server에서 ASP.NET Core를 설치 합니다.

1. 호스팅 시스템에 [.NET Core Windows Server 호스팅 번들](https://aka.ms/dotnetcore-2-windowshosting)을 설치합니다. 번들은 .NET Core 런타임, .NET Core 라이브러리 및 ASP.NET Core 모듈을 설치합니다. 더 자세한 지침은 [IIS에 게시](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)합니다.

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

가져오는 경우 게시 설정에이 섹션을 건너뛸 수 있습니다.

1. **IIS(인터넷 정보 서비스) 관리자** 를 열고 **사이트**로 이동합니다.

2. **기본 웹 사이트** 노드를 마우스 오른쪽 단추로 클릭하고 **응용 프로그램 추가**를 선택합니다.

3. 설정 된 **별칭** 필드를 **MyASPApp** 및 응용 프로그램 풀 필드 **관리 코드 없음**합니다. 설정 된 **실제 경로** 하 **C:\Publish** (나중에 배포할 ASP.NET 프로젝트).

4. IIS 관리자에서 선택한 사이트를 선택할 **사용 권한 편집**, 해당 IUSR, IIS_IUSRS, 또는 사용자 응용 프로그램 풀은 읽기 및 실행 권한이 있는 권한 있는 사용자에 대해 구성 되었는지 확인 합니다.

    액세스를 사용 하 여 이러한 사용자 중 하나로 표시 되지 않으면, IUSR 읽기 및 실행 권한이 있는 사용자로 추가 하는 단계를 통해 이동 합니다.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(선택 사항) 게시 하 고 Visual Studio에서 로컬 폴더에 게시 하 여 앱 배포

웹 배포를 사용 하지 않는 경우에 게시 하 고 파일 시스템 또는 다른 도구를 사용 하 여 앱을 배포 해야 합니다. 파일 시스템을 사용 하 여 패키지를 만들어 시작 하 고 패키지를 수동으로 배포 하거나 PowerShell, RoboCopy 또는 XCopy 같은 다른 도구를 사용 합니다. 이 섹션에서는 웹 배포를 사용 하지 않는 경우 패키지를 수동으로 복사는 가정 합니다.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> 다운로드 하 여 Windows Server에서 원격 도구 설치

Visual Studio의 버전과 일치 하는 원격 도구의 버전을 다운로드 합니다.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a> Windows Server에서 원격 디버거 설정

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 추가 사용자에 대 한 사용 권한을 추가 하는 인증 모드를 변경 하거나 원격 디버거의 포트 번호에 필요한 경우 참조 [원격 디버거 구성](../debugger/remote-debugging.md#configure_msvsmon)합니다.

### <a name="BKMK_attach"></a> Visual Studio 컴퓨터에서 ASP.NET 애플리케이션에 연결

1. Visual Studio 컴퓨터에서 디버그 하려는 된 솔루션을 엽니다 (**MyASPApp** 이 문서의 단계를 수행 하는 경우).
2. Visual Studio에서 클릭 **디버그 > 프로세스에 연결** (Ctrl + Alt + P).

    > [!TIP]
    > Visual Studio 2017 이상 버전에서 다시 연결할 수는 동일한 프로세스 이전에 사용 하 여 연결할 **디버그 > 프로세스에 다시 연결 하는 중...** (Shift+Alt+P).

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

    * 선택 **dotnet.exe** (예:.NET Core)

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

### <a name="bkmk_openports"></a> 문제 해결: Windows Server에서 필요한 포트를 열려면

대부분의 설치 프로그램에서 ASP.NET와 원격 디버거 설치를 통해 필요한 포트가 열려 있습니다. 그러나 배포 문제를 해결 하는 응용 프로그램 방화벽 뒤에서 호스팅되는 경우에 올바른 포트가 열려 있는지 확인 해야 합니다.

Azure VM에서 포트를 통해 열어야 합니다 [네트워크 보안 그룹](/azure/virtual-machines/windows/nsg-quickstart-portal)합니다.

필요한 포트:

* 80-IIS에 대 한 필요합니다.
::: moniker range=">=vs-2019"
* 4024-Visual Studio 2019 원격 디버깅을 위해 필요 합니다. (참조 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) 자세한).
::: moniker-end
::: moniker range="vs-2017"
* 4022-Visual Studio 2017에서 원격 디버깅을 위해 필요 합니다. (참조 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) 자세한).
::: moniker-end
* UDP 3702-(선택 사항) 검색 포트 사용 하도록 설정 하는 **찾을** 단추 Visual Studio에서 원격 디버거를 연결 하는 경우.

또한 이러한 포트가 이미 열어야 ASP.NET 설치:
- 8172-(Visual Studio에서 앱을 배포 하려면 웹 배포 하는 데 필요한 선택 사항)
