---
title: UWP 앱에 대 한 디버깅 세션을 시작 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 7c65662d054b8c3dd9e650fe088f7048cc3b4071
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62930068"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>UWP 앱에 대한 디버깅 세션 시작

이 문서에는 유니버설 Windows 플랫폼 (UWP) 앱에 대 한 Visual Studio 디버깅 세션을 시작 하는 방법을 설명 합니다. XAML에서 UWP 앱을 작성할 수 있습니다 하 고 C++, XAML 및 C#/Visual Basic 합니다. UWP 앱을 디버깅을 시작 하려면 디버깅 세션을 구성 하 고 앱을 시작 하는 방법은 선택 합니다.

::: moniker range=">=vs-2019"
> [!NOTE]
> Visual Studio 2019 년부터 HTML 및 JavaScript 용 UWP 앱 더 이상 지원 됩니다.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017에서 대부분의 명령 및이 문서에 나와 있는 옵션에도 적용 UWP 앱 HTML 및 JavaScript에 대 한 합니다. 관리 되는 명령이 서로 있는 및 C++ 앱을 JavaScript 앱 일반적으로 동일 명령에 대 한 C++ UWP 앱.
::: moniker-end

## <a name="BKMK_The_easy_way_to_start_debugging"></a>Visual Studio 도구 모음에서 디버깅 시작

구성 및 디버깅을 시작 하는 가장 쉬운 방법은 표준 Visual Studio 도구 모음에서 됩니다.

![도구 모음에서 디버그](../debugger/media/vsrun_select_target_device.png)

1. **구성** 드롭다운을 합니다 **표준** 도구 모음 선택 **디버그**합니다.

1. **플랫폼** 드롭다운에서 빌드할 대상 플랫폼을 선택 합니다.

1. 녹색 화살표 옆에 있는 드롭다운 목록에서 디버그 대상을 선택 합니다. 로컬 컴퓨터, 직접 연결 된 장치, 로컬 Visual Studio 시뮬레이터, 원격 장치 또는 에뮬레이터를 선택할 수 있습니다.

1. 디버깅을 시작 하려면 녹색 선택 **시작** 선택 또는 도구 모음에서 화살표 **디버그** > **디버깅 시작**를 누르거나 **F5**.

   Visual Studio가 디버거가 연결된 응용 프로그램을 빌드하고 시작합니다.

디버깅 중단점에 도달 하면, 있습니다 수동으로 실행을 일시 중단 되지 않은 예외가 발생 하거나 앱이 끝날 때까지 계속 됩니다.

### <a name="BKMK_Choose_the_deployment_target"></a> 배포 대상 옵션

Visual Studio 도구 모음에서 디버깅 대상을 설정할 수 있습니다 하거나 프로젝트의 속성 페이지를 디버깅 합니다. 다음 옵션 중 하나를 선택합니다.

|||
|-|-|
|**로컬 컴퓨터**|로컬 컴퓨터의 현재 세션에서 응용 프로그램을 디버깅합니다.|
|**시뮬레이터**|UWP 앱 용 Visual Studio 시뮬레이터에서 앱을 디버그 합니다. 시뮬레이터는 터치 제스처 및는 로컬 컴퓨터에 없는 장치 회전과 같은 장치 기능을 시뮬레이션 하는 데스크톱 창입니다. 시뮬레이터 옵션은 사용할 수 있는 경우에만 앱의 **대상 플랫폼 최소입니다. 버전** 로컬 컴퓨터의 운영 체제 보다 작거나 같음. 자세한 내용은 [시뮬레이터에서 UWP 앱 실행](../debugger/run-windows-store-apps-in-the-simulator.md)합니다.|
|**원격 컴퓨터**|네트워크나 이더넷 케이블을 통해 로컬 컴퓨터에 연결 하는 장치에서 앱을 디버그 합니다. Visual Studio 용 원격 도구가 원격 장치에서 실행 되 고 설치 해야 합니다. 자세한 내용은 [원격 컴퓨터에서 UWP 앱 실행](../debugger/run-windows-store-apps-on-a-remote-machine.md)합니다.|
|**디바이스**|USB로 연결 된 장치에서 앱을 디버그 합니다. 장치가는 개발자 잠금 해제 되어야 하 고 화면을 잠금 해제 해야 합니다.|
|**모바일 에뮬레이터**|에뮬레이터 이름에 지정 된 에뮬레이터 부팅, 앱을 배포 및 디버깅을 시작 합니다. 에뮬레이터는 Hyper-v 사용 하도록 컴퓨터에만 사용할 수 있습니다.|

## <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> 프로젝트 속성 페이지에 디버깅 구성

추가 디버깅 옵션을 구성 하려면 프로젝트의 디버깅 속성 페이지를 사용 합니다.

**디버깅 속성을 열려면:**

1. **솔루션 탐색기**프로젝트를 선택한 다음 선택 합니다 **속성** 아이콘을 또는 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택 **속성**합니다.

1. 왼쪽에는 **속성** 창:

   - 에 대 한 C# 및 Visual Basic 앱을 선택 **디버그**합니다.

     ![C#및 Visual Basic 프로젝트 디버그 속성 페이지](../debugger/media/dbg_csvb_debugpropertypage.png)

   - 에 대 한 C++ 앱 선택 **구성 속성** > **디버깅**.

     ![C++UWP 앱 디버깅 속성 페이지](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="BKMK_Choose_the_debugger_to_use"></a> 사용할 디버거 선택

에 대 한 C# 및 Visual Basic 앱을 Visual Studio 이러한 기본적으로 코드를 관리 합니다. 다른 또는 추가적인 코드 형식 디버깅을 선택할 수 있습니다. 설정할 수도 있습니다 **디버거 형식** 프로젝트의 일부인 모든 백그라운드 작업에 대 한 값입니다.

C++ 앱을 Visual Studio는 기본적으로 네이티브 코드를 디버깅 합니다. 특정 형식의 코드 대신, 또는 외에, 네이티브 코드를 디버깅 하도록 선택할 수 있습니다.

**코드 형식 디버깅 하려면 다음을 지정 하려면**

- 에 대 한 C# Visual Basic 앱에서 다음 디버거 중 하나를 선택 하 고는 **응용 프로그램 종류** 및 **백그라운드 프로세스 유형** 아래에 있는 드롭다운 **디버거 형식** 에서 합니다 **디버그** 속성 페이지.

- 에 대 한 C++ 앱에서 다음 디버거 중 하나를 선택 합니다 **디버거 형식** 드롭다운에서 **디버깅** 속성 페이지.

|||
|-|-|
|**관리 전용**|응용 프로그램에서 관리 코드를 디버깅합니다. JavaScript 코드와 네이티브 C/C++ 코드는 무시됩니다.|
|**네이티브 전용**|응용 프로그램에서 네이티브 C/C++ 코드를 디버깅합니다. 관리 코드와 JavaScript 코드는 무시됩니다.|
|**혼합(관리/네이티브)**|응용 프로그램에서 네이티브 C/C++ 코드 및 관리 코드를 디버깅합니다. JavaScript 코드는 무시됩니다. C++ 프로젝트의 경우이 옵션 이라고 **관리 / 네이티브**합니다.|
|**스크립트**|응용 프로그램에서 JavaScript 코드를 디버깅합니다. 관리 코드와 네이티브 코드는 무시됩니다.|
|**스크립트가 포함된 네이티브**|네이티브 C 디버그 /C++ 코드와 앱에서 JavaScript 코드입니다. 관리 되는 코드는 무시 됩니다. 사용할 수 있는 C++ 프로젝트 또는 백그라운드 태스크만 합니다.|
|**GPU 전용(C++ AMP)**|GPU(그래픽 처리 장치)에서 실행되는 네이티브 C++ 코드를 디버깅합니다. 사용할 수 있는 C++ 프로젝트에 해당 합니다.|

### <a name="BKMK__Optional__Disable_network_loopbacks"></a> (선택 사항) 네트워크 루프백을 사용 하지 않도록 설정

 보안을 위해 표준 방식으로 설치 하는 UWP 앱에 설치 된 장치에 대 한 네트워크 호출을 만들 수 없습니다. Visual Studio 예외적으로 단일 컴퓨터에서 통신 프로시저를 테스트할 수 있도록 기본적으로이 규칙에서 앱을 배포 합니다. 앱을 릴리스하기 전에 예외 없이 앱을 테스트 해야 합니다.

**네트워크 루프백 예외를 제거하려면:**

- 에 대 한 C# Visual Basic 앱을 선택 취소 합니다 **로컬 네트워크 루프백 허용** 아래의 확인란 **시작 옵션** 에 **디버그** 속성 페이지.

- 시각적 개체에 대해 C++ 앱을 선택 **No** 에서 합니다 **로컬 네트워크 루프백 허용** 드롭다운을는 **디버깅** 속성 페이지.

### <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> 디버깅을 시작할 때 (선택 사항) 앱을 다시 설치
 설치 문제를 진단 하는 C# 또는 Visual Basic 앱을 선택 **제거 후 패키지를 다시 설치** 에 **디버그** 속성 페이지. 이 옵션 디버깅을 시작할 때 원래 설치를 다시 만듭니다. 이 옵션을 사용할 수 없는 C++ 프로젝트입니다.

### <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> 원격 디버깅에 대 한 인증 옵션 설정

기본적으로 선택 하면 원격 디버거를 실행 하려면 Windows 자격 증명을 제공 해야 합니다 **원격 컴퓨터** 배포 대상으로 합니다. 인증 요구 사항을 변경할 수 있습니다.

합니다 **유니버설 (암호화 되지 않은 프로토콜)** IoT, Xbox 및 HoloLens 장치 및 크리에이터 업데이트 또는 이후 Windows 10 Pc에 대 한 인증 모드는 합니다.

**인증 방법을 변경 하려면:**

- 에 대 한 C# 및 Visual Basic 앱에는 **디버그** 속성 페이지에서 선택 **원격 컴퓨터** 으로 **대상 장치**. 그런 다음 선택 **None** 또는 **유니버설 (암호화 되지 않은 프로토콜)** 에 대 한 **Mode**합니다.

- 에 대 한 C++ 앱 선택 **원격 컴퓨터** 아래에서 **실행할 디버거** 에 **디버깅** 속성 페이지. 그런 다음 선택 **인증 없음** 또는 **유니버설 (암호화 되지 않은 프로토콜)** 에 대 한 **인증 유형**합니다.

> [!CAUTION]
> 원격 디버거를 실행할 때는 네트워크 보안이 없습니다 있기 **None** 하거나 **유니버설 (암호화 되지 않은 프로토콜)** 모드입니다. 이러한 모드에 있는 신뢰할 수 있는 네트워크 에서만 악성 코드 또는 유해 트래픽 위험이 없습니다 있는지를 선택 하세요.

## <a name="BKMK_Start_the_debugging_session"></a> 디버깅 시작 옵션

선택 하면 **디버깅할** > **디버깅 시작** 누르거나 **F5**, Visual Studio가 디버거가 연결 된 앱을 시작 합니다. 중단점에 도달하거나 수동으로 실행을 일시 중단하거나 처리되지 않은 예외가 발생하거나 응용 프로그램이 끝날 때까지 계속해서 실행됩니다.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> 앱 시작 지연 되지만 디버깅을 시작합니다

기본적으로 Visual Studio 디버깅을 시작할 때 바로 앱을 시작 합니다. 또한 디버그 모드에서 실행 되지만 디버거 외부에서 앱을 시작 하려면 앱을 설정할 수 있습니다. Windows에서 앱 시작을 디버깅 하려는 하는 예를 들어 **시작** 메뉴 또는 앱에서 백그라운드 프로세스를 디버그 합니다. 이 옵션을 선택 하면 앱 시작 시 디버거에서 시작 됩니다.

**자동 앱 시작을 사용 하지 않도록 설정 합니다.**

- 에 대 한 C# 및 Visual Basic 앱을 선택 **시작 하지 않음 시작 시 코드를 디버그** 아래에서 **시작 옵션** 에 **디버그** 속성 페이지.

- 에 대 한 C++ 앱을 선택 **No** 에서 **응용 프로그램 시작** 드롭다운에서 합니다 **디버깅** 속성 페이지.

백그라운드 작업 디버깅 하는 방법에 대 한 자세한 내용은 참조 하세요. [트리거 일시 중단, 다시 시작 및 백그라운드 이벤트 UWP 앱 용](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)합니다.

### <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> 설치 또는 실행 중인 UWP 앱 디버그

사용할 수 있습니다 **디버그 Installed App Package** 에 이미 설치 되어 있거나 로컬 또는 원격 장치에서 실행 중인 UWP 앱을 디버그 합니다. Microsoft Store 앱을 설치 하거나 Visual Studio 프로젝트를 되지 않을 수 있습니다. 예를 들어, 앱 Visual Studio를 사용 하지 않는 사용자 지정 빌드 시스템이 있을 수 있습니다.

설치 된 앱을 즉시 시작할 수 있습니다 또는 다른 메서드를 사용 하 여 시작 될 때 디버거에서 실행 되도록 설정할 수 있습니다. 자세한 내용은 [트리거 일시 중단, 다시 시작 및 백그라운드 이벤트 UWP 앱 용)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)합니다.

설치 또는 실행 중인 UWP 앱에 디버거를 시작 하려면 선택 **디버깅할** > **기타 디버그 대상** > **디버그 Installed App Package**합니다. 자세한 지침은 [설치 된 앱 패키지 디버그](../debugger/debug-installed-app-package.md)합니다.

### <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> 실행 중인 Windows 8.x 앱에 디버거 연결

[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 응용 프로그램에 디버거를 연결하려면 디버깅 가능 패키지 관리자를 사용하여 응용 프로그램이 디버그 모드에서 실행되도록 설정합니다. 디버깅 가능한 패키지 관리자 Visual Studio 용 원격 도구를 사용 하 여 설치 됩니다.

1. 앱이 설치 되어 있는 장치에 Visual Studio 용 원격 도구를 설치 합니다. 자세한 내용은 [원격 도구 설치](../debugger/remote-debugging.md)합니다.

1. 에 Windows **시작** 화면에서 검색 하 고 시작 **디버깅 가능한 패키지 관리자**합니다.

   AppxDebug cmdlet에 맞게 올바르게 구성된 PowerShell 창이 나타납니다.

1. 앱의 PackageFullName 식별자를 지정 합니다.

   1. 모든 앱의 PackageFullName이 포함 되어 있는 목록을 보려면, 입력 `Get-AppxPackage` PowerShell 프롬프트에서.

   1. PowerShell 프롬프트에서 입력 `Enable-AppxDebug <PackageFullName>`여기서 \<PackageFullName > 앱의 PackageFullName 식별자입니다.

1. **디버그** > **프로세스에 연결**을 선택합니다.

1. 에 **프로세스에 연결** 대화 상자에서 원격 장치 지정 합니다 **연결 대상** 상자.

   장치 이름을 입력을의 드롭다운 목록에서 선택 합니다 **연결 대상** 누르거나 상자의 **찾을** 에서 장치를 찾을 수는 **원격 연결** 대화 상자.

1. 옆에 디버그 하려는 코드의 형식을 지정 하는 **연결할** 상자에서 **선택**합니다.

1. 에 **코드 형식 선택** 대화 상자를 선택 합니다.
   - **디버깅할 코드 형식을 자동으로 결정**, 또는
   - **다음 코드 형식 디버깅**, 하나 이상의 코드 형식 목록에서 선택 합니다.

1. 에 **사용 가능한 프로세스** 목록에서 디버그 하는 앱 프로세스를 선택 합니다.

1. 선택 **연결**합니다.

 프로세스에 디버거가 연결됩니다. 중단점에 도달하거나 수동으로 실행을 일시 중단하거나 처리되지 않은 예외가 발생하거나 응용 프로그램이 끝날 때까지 계속해서 실행됩니다.

::: moniker range="vs-2017"
> [!NOTE]
> JavaScript 앱은 *wwahost.exe* 프로세스의 인스턴스에서 실행됩니다. 둘 이상의 JavaScript 앱을 실행 중인 경우의 숫자 프로세스 id (PID)를 확인 해야 합니다 *wwahost.exe* 프로세스에 연결 합니다.
>
> JavaScript 앱에 연결 하는 가장 쉬운 방법은 다른 JavaScript 앱을 닫는 것입니다. 또는 실행의 Pid를 기록할 수 있습니다 *wwahost.exe* Windows 작업 관리자에서 앱을 시작 하기 전에 프로세스입니다. 앱을 시작 하면 해당 *wwahost.exe* PID는 이전에 언급 된 다른 것이 됩니다.
::: moniker-end

## <a name="see-also"></a>참고자료
- [Visual Studio에서 앱 디버그](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)