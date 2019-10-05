---
title: 원격 디버깅 | Microsoft Docs
ms.custom:
- remotedebugging
- seodec18
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9918a2de67693c0232c94a736f12c7af0a0b959c
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043324"
---
# <a name="remote-debugging"></a>Remote Debugging
다른 컴퓨터에 배포된 Visual Studio 애플리케이션을 디버그할 수 있습니다. 이렇게 하려면 Visual Studio 원격 디버거를 사용합니다.

원격 디버깅에 대 한 자세한 내용은 다음이 항목을 참조 하세요.

|시나리오|링크|
|-|-|-|
|Azure App Service|[스냅숏 디버거](../debugger/debug-live-azure-applications.md) 또는 [원격 Azure에서 ASP.NET 디버그](../debugger/remote-debugging-azure.md)|
|Azure VM|[Azure의 원격 디버그 ASP.NET](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Azure Service Fabric 응용 프로그램 디버그](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[원격 디버그 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) 또는 [원격 디버그 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# 또는 Visual Basic|[C# 또는 Visual Basic 프로젝트](../debugger/remote-debugging-csharp.md) 원격 디버그|
|C++|[C++ 프로젝트 원격 디버그](../debugger/remote-debugging-cpp.md)|
|유니버설 Windows 앱 (UWP)|[원격 컴퓨터에서 UWP 앱 실행](../debugger/run-windows-store-apps-on-a-remote-machine.md) 또는 [설치 된 앱 패키지 디버그](../debugger/debug-installed-app-package.md)|

방금 다운로드 하 고 원격 디버거를 설치 하 고 시나리오에 대 한 추가 지침을 필요 하지 않습니다,이 문서의 단계를 수행 합니다.

## <a name="download-and-install-the-remote-tools"></a>원격 도구 다운로드 및 설치

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements_msvsmon"></a> 요구 사항

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="fileshare_msvsmon"></a> (선택 사항) 파일 공유에서 원격 디버거를 실행 하려면

원격 디버거를 찾을 수 있습니다 (*msvsmon.exe*) Visual Studio Community, Professional 또는 Enterprise를 이미 설치 된 컴퓨터에 있습니다. 일부 시나리오에 대 한 원격 디버깅을 설정 하는 가장 쉬운 방법은 파일 공유에서 원격 디버거 (msvsmon.exe)를 실행 하는 것입니다. 사용 제한 사항에 대 한 원격 디버거의 도움말 페이지를 참조 하세요. (**도움말 > 사용량** 원격 디버거의).

1. 찾을 *msvsmon.exe* Visual Studio 버전과 일치 하는 디렉터리에 있습니다.

   ::: moniker range=">=vs-2019"

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. 공유 합니다 **원격 디버거** Visual Studio 컴퓨터의 폴더입니다.

3. 원격 컴퓨터에서 실행 *msvsmon.exe* 공유 폴더에서. 수행 합니다 [설치 지침](#bkmk_setup)합니다.

> [!TIP]
> 명령줄 설치와 명령줄 참조에 대 한 도움말 페이지를 참조 하세요 *msvsmon.exe* 입력 하 여 ``msvsmon.exe /?`` Visual Studio가 설치 된 컴퓨터의 명령줄에서 (또는 이동 **도움말 > 사용량**원격 디버거의).

## <a name="bkmk_setup"></a> 원격 디버거 설정

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a> 원격 디버거 구성
원격 디버거를 처음으로 시작한 후에 원격 디버거 구성의 일부 측면을 변경할 수 있습니다.

- 선택에 원격 디버거를 연결할 다른 사용자에 대 한 사용 권한을 추가 하는 경우 **도구 > 권한을**합니다. 사용 권한을 부여하거나 거부하려면 관리자 권한이 있어야 합니다.

     > [!IMPORTANT]
     > Visual Studio 컴퓨터에서 사용 하는 사용자 계정에서 다른 사용자 계정으로 원격 디버거를 실행할 수는 있지만 원격 디버거의 사용 권한에 다른 사용자 계정을 추가 해야 합니다.

     또는 사용 하 여 명령줄에서 원격 디버거를 시작할 수 있습니다 합니다 **허용 / \<사용자 이름 >** 매개 변수: **msvsmon /allow \< username@computer>** 합니다.

- 인증 모드 또는 포트 번호를 변경 하거나 원격 도구의 시간 제한 값을 지정 하는 경우: 선택할 **도구 > 옵션**합니다.

     기본적으로 사용 되는 포트 번호의 나열을 참조 하세요 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)합니다.

     > [!WARNING]
     > 원격 도구를 인증 안 함 모드에서 실행할 수도 있지만 이 모드는 사용하지 않는 것이 좋습니다. 이 모드에서 실행할 때는 네트워크 보안이 없습니다. 네트워크에 악의적인 트래픽이나 유해 트래픽 위험이 확실히 없는 경우에만 인증 안 함 모드를 선택하세요.

## <a name="bkmk_configureService"></a> (선택 사항) 원격 디버거를 서비스로 구성
ASP.NET 및 기타 서버 환경에서 디버깅을 위해 관리자 권한으로 원격 디버거를 실행 하거나, 항상 실행 하려는 경우 원격 디버거를 서비스로 실행 됩니다.

 원격 디버거를 서비스로 구성 하려는 경우 다음이 단계를 수행 합니다.

1. **원격 디버거 구성 마법사** (rdbgwiz.exe)를 찾습니다. 이는 원격 디버거와 별도의 응용 프로그램입니다. 원격 도구를 설치한 경우에만 사용할 수 있습니다. Visual Studio와 함께 설치되지 않습니다.

2. 구성 마법사 실행을 시작합니다. 첫 페이지가 표시되면 **다음**을 클릭합니다.

3. **Visual Studio 2015 원격 디버거를 서비스로 실행** 확인란을 선택합니다.

4. 사용자 계정 및 암호의 이름을 추가합니다.

    추가 해야 할 수도 합니다 **서비스로 로그온** 사용자 권한을이 계정 (찾기 **로컬 보안 정책** (secpol.msc)에 **시작** 페이지 또는 창 (또는 형식  **secpol을** 명령 프롬프트에서). 창이 나타나면 **사용자 권한 할당**을 두 번 클릭한 다음 오른쪽 창에서 **서비스로 로그온** 을 찾습니다. 폴더를 두 번 클릭합니다. **속성** 창에 사용자 계정을 추가하고 **확인**을 클릭합니다. **다음**을 클릭합니다.

5. 원격 도구가 통신하는 데 사용할 네트워크 유형을 선택합니다. 하나 이상의 네트워크 형식을 선택해야 합니다. 컴퓨터가 도메인을 통해 연결된 경우 첫 번째 항목을 선택해야 합니다. 컴퓨터가 작업 그룹 또는 홈 그룹을 통해 연결된 경우 두 번째 또는 세 번째 항목을 선택해야 합니다. **다음**을 클릭합니다.

6. 서비스를 시작할 수 있는 경우 **Visual Studio 원격 디버거 구성 마법사를 성공적으로 완료했습니다.** 가 표시됩니다. 서비스를 시작할 수 없는 경우 **Visual Studio 원격 디버거 구성 마법사 완료 실패**가 표시됩니다. 이 페이지에서는 서비스를 시작하기 위해 수행할 몇 가지 팁도 제공합니다.

7. **마침**을 클릭합니다.

   이제 원격 디버거가 서비스로 실행됩니다. **제어판 > 서비스**로 이동하고 **Visual Studio 2015 원격 디버거**를 찾아 이를 확인할 수 있습니다.

   **제어판 > 서비스**에서 원격 디버거 서비스를 중지하고 시작할 수 있습니다.

## <a name="set-up-debugging-with-remote-symbols"></a>원격 기호를 사용한 디버깅 설정

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>참고자료

- [디버거 소개](../debugger/debugger-feature-tour.md)
- [원격 디버깅을 위해 Windows 방화벽 구성](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)
- [원격 디버깅 원격 IIS 컴퓨터에서 ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)