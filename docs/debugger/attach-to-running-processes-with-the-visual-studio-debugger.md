---
title: 디버거를 사용 하 여 실행 중인 프로세스에 연결 | Microsoft Docs
ms.custom: seodec18
ms.date: 04/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f810761d088eaf6ec94524a7d76ec255c931686b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565788"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio 디버거에서 실행 중인 프로세스에 연결
로컬 또는 원격 컴퓨터에서 실행 중인 프로세스에 Visual Studio 디버거를 연결할 수 있습니다. 프로세스를 실행 한 후 선택 **디버깅할** > **프로세스에 연결** 누르거나 **Ctrl**+**Alt** + **P** 사용 하 여 Visual Studio에는 **프로세스에 연결** 프로세스에 디버거를 연결 하는 대화 상자.

사용할 수 있습니다 **프로세스에 연결** 로컬 또는 원격 컴퓨터에서 실행 중인 앱을 디버깅 하려면 동시에 여러 프로세스 디버깅, Visual Studio에서 작성 하지 않은 앱을 디버그 또는 사용 하 여 Visual Studio에서 시작 하지 않은 모든 앱을 디버그 합니다 디버거를 연결 합니다. 예를 들어, 디버거 없이 앱을 실행 하 고 예외가 발생 하는 경우 다음 앱을 실행 하는 프로세스에 디버거를 연결 하 디버깅을 시작 합니다.

> [!TIP]
> 확실 하지 않은 경우 사용할 것인지 **프로세스에 연결** 디버깅 시나리오에 대 한? 참조 [일반적인 디버깅 시나리오](#BKMK_Scenarios)합니다.

## <a name="BKMK_Attach_to_a_running_process"></a> 로컬 컴퓨터에서 실행 중인 프로세스에 연결

이전에 연결 하는 프로세스를 신속 하 게 연결할 참조 [프로세스에 다시 연결](#BKMK_reattach)합니다.

원격 컴퓨터에서 프로세스를 디버깅 하려면 참조 [원격 컴퓨터에서 프로세스에 연결](#BKMK_Attach_to_a_process_on_a_remote_computer)합니다.

**로컬 컴퓨터의 프로세스에 연결 합니다.**

1. Visual Studio에서 선택 **디버깅할** > **프로세스에 연결** (또는 키를 눌러 **Ctrl**+**Alt** + **P**)를 열려고 합니다 **프로세스에 연결** 대화 상자.

   **연결 형식** 로 설정 해야 **기본**입니다. **연결 대상** 에 로컬 컴퓨터 이름 이어야 합니다.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. 에 **사용 가능한 프로세스** 나열, 찾기 및 하나 이상의 프로세스에 연결 하려면 선택 합니다.

   - 프로세스를 신속 하 게 선택 하려면 해당 이름 또는 첫 번째 문자를 입력 합니다 **프로세스 필터링** 상자입니다.

   - 프로세스 이름을 모르는 경우 목록을 찾아보거나 참조 [일반적인 디버깅 시나리오](#BKMK_Scenarios) 몇 가지 일반적인 프로세스 이름에 대 한 합니다.

   >[!TIP]
   >프로세스를 시작 하는 동안 백그라운드에서 중지 된 **프로세스에 연결** 대화 상자가 열려 실행 중인 프로세스 목록을 항상 않을 현재 합니다. 선택할 수 있습니다 **새로 고침** 언제 든 지 현재 목록을 참조 하세요.

3. 에 **연결할** 필드에 디버그 하려는 코드의 형식이 표시 되어 있는지 확인 합니다. 기본값 **자동** 대부분의 앱 형식에 대 한 작동을 설정 합니다.

   수동으로 코드 형식 선택:
   1. **선택**을 클릭합니다.
   1. 에 **코드 형식 선택** 대화 상자에서 **다음 코드 형식 디버깅**합니다.
   1. 디버깅할 코드 형식을 선택 합니다.
   1. **확인**을 선택합니다.

4. 선택 **연결**합니다.

>[!NOTE]
>디버깅을 위해 여러 앱에 연결할 수 있지만 한 번에 하나의 앱만 디버거에서 활성화 됩니다. Visual Studio에서 활성 앱을 설정할 수 있습니다 **디버그 위치** 도구 모음 또는 **프로세스** 창입니다.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> 원격 컴퓨터의 프로세스에 연결

원격 컴퓨터를 선택할 수도 있습니다는 **프로세스에 연결** 대화 상자에서 해당 컴퓨터에서 실행 되는 사용 가능한 프로세스 목록 보기 및 하나 이상의 디버깅에 대 한 프로세스에 연결 합니다. 원격 디버거 (*msvsmon.exe*) 원격 컴퓨터에서 실행 되어야 합니다. 자세한 내용은 [원격 디버깅](../debugger/remote-debugging.md)합니다.

IIS에 배포 된 ASP.NET 응용 프로그램 디버깅에 대 한 자세한 내용은 참조 하세요. [원격 원격 IIS 컴퓨터에서 ASP.NET 디버깅](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)합니다.

**원격 컴퓨터에서 실행 중인 프로세스에 연결 합니다.**

1. Visual Studio에서 선택 **디버깅할** > **프로세스에 연결** (또는 키를 눌러 **Ctrl**+**Alt** + **P**)를 열려고 합니다 **프로세스에 연결** 대화 상자.

2. **연결 형식** 있어야 **기본** 대부분의 경우에 대 한 합니다. 에 **연결 대상** 상자에서 다음 방법 중 하나를 사용 하 여 원격 컴퓨터를 선택 합니다.

   - 그런 다음 드롭다운 화살표를 선택 **연결 대상**, 드롭 다운 목록에서 컴퓨터 이름을 선택 합니다.
   - 에 컴퓨터 이름을 입력 합니다 **연결 대상** 누릅니다 상자 **Enter**합니다.

     Visual Studio 형식으로 표시 되는 컴퓨터 이름에 필요한 포트를 추가 함을 확인 합니다.  **\<원격 컴퓨터 이름 >: 포트**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > 원격 컴퓨터 이름을 사용 하 여 연결할 수 없는 경우 IP를 사용 하 여 시도 및 포트 주소 (예를 들어 `123.45.678.9:4022`). 4024는 Visual Studio 2019 x64 원격 디버거에 대 한 기본 포트입니다. 다른 원격 디버거 포트 할당을 참조 하세요 [원격 디버거 포트 할당](remote-debugger-port-assignments.md)합니다.

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > 원격 컴퓨터 이름을 사용 하 여 연결할 수 없는 경우 IP를 사용 하 여 시도 및 포트 주소 (예를 들어 `123.45.678.9:4022`). 4022는 Visual Studio 2017 x64 원격 디버거에 대 한 기본 포트입니다. 다른 원격 디버거 포트 할당을 참조 하세요 [원격 디버거 포트 할당](remote-debugger-port-assignments.md)합니다.

     ::: moniker-end

   - 선택 합니다 **찾을** 단추 옆에 **연결 대상** 상자를 엽니다 합니다 **원격 연결** 대화 상자. 합니다 **원격 연결** 대화 상자는 로컬 서브넷에 있거나 컴퓨터에 직접 연결 된 모든 장치를 나열 합니다. 해야 할 수 있습니다 [UDP 포트 3702 엽니다](../debugger/remote-debugger-port-assignments.md) 서버에 원격 장치를 검색 합니다. 컴퓨터 또는 장치를 선택한 다음 선택 **선택**합니다.

   > [!NOTE]
   > 합니다 **연결 형식** 설정은 디버깅 세션 간에 유지 합니다. 합니다 **연결 대상** 설정은 해당 대상을 사용 하 여 디버깅 연결에 성공 하면 발생 하는 경우에 디버깅 세션 간에 유지 합니다.

3. 클릭 **새로 고침** 채우는 합니다 **사용 가능한 프로세스** 목록입니다.

    >[!TIP]
    >프로세스를 시작 하는 동안 백그라운드에서 중지 된 **프로세스에 연결** 대화 상자가 열려 실행 중인 프로세스 목록을 항상 않을 현재 합니다. 선택할 수 있습니다 **새로 고침** 언제 든 지 현재 목록을 참조 하세요.

4. 에 **사용 가능한 프로세스** 나열, 찾기 및 하나 이상의 프로세스에 연결 하려면 선택 합니다.

   - 프로세스를 신속 하 게 선택 하려면 해당 이름 또는 첫 번째 문자를 입력 합니다 **프로세스 필터링** 상자입니다.

   - 프로세스 이름을 모르는 경우 목록을 찾아보거나 참조 [일반적인 디버깅 시나리오](#BKMK_Scenarios) 몇 가지 일반적인 프로세스 이름에 대 한 합니다.

   - 모든 사용자 계정으로 실행 되는 프로세스를 찾으려면 다음을 선택 합니다 **모든 사용자의 프로세스 표시** 확인란 합니다.

     >[!NOTE]
     >신뢰할 수 없는 사용자 계정에서 소유한 프로세스에 연결하면 보안 경고 확인 대화 상자가 나타납니다. 자세한 내용은 참조 하세요. [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결하면 위험할 수 있습니다. 다음 정보가 의심 스 럽 또는 확실 하지 않은 경우이 프로세스에 연결 하지 않는](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)합니다.

5. 에 **연결할** 필드에 디버그 하려는 코드의 형식이 표시 되어 있는지 확인 합니다. 기본값 **자동** 대부분의 앱 형식에 대 한 작동을 설정 합니다.

   수동으로 코드 형식 선택:
   1. **선택**을 클릭합니다.
   1. 에 **코드 형식 선택** 대화 상자에서 **다음 코드 형식 디버깅**합니다.
   1. 디버깅할 코드 형식을 선택 합니다.
   1. **확인**을 선택합니다.

6. 선택 **연결**합니다.

>[!NOTE]
>디버깅을 위해 여러 앱에 연결할 수 있지만 한 번에 하나의 앱만 디버거에서 활성화 됩니다. Visual Studio에서 활성 앱을 설정할 수 있습니다 **디버그 위치** 도구 모음 또는 **프로세스** 창입니다.

일부 경우에는 원격 데스크톱 (터미널 서비스) 세션에서 디버그할 때는 합니다 **사용 가능한 프로세스** 모든 사용 가능한 프로세스 목록에 표시 되지 않습니다. Visual Studio에는 제한 된 사용자 계정이 있는 사용자로 실행 하는 경우는 **사용 가능한 프로세스** 목록에는 세션 0에서에서 실행 중인 프로세스에 표시 되지 않습니다. 서비스 및 포함 하 여 다른 서버 프로세스에 대 한 세션 0 되 *w3wp.exe*합니다. 관리자 계정으로 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 를 실행하거나 터미널 서비스 세션 대신 서버 콘솔에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 를 실행하여 이 문제를 해결할 수 있습니다.

이러한 해결 방법을 둘 다 사용할 수 없는 경우 세 번째 방법으로 Windows 명령줄에서 `vsjitdebugger.exe -p <ProcessId>`를 실행하여 프로세스에 연결합니다. 사용 하 여 프로세스 ID를 확인할 수 있습니다 *tlist.exe*합니다. *tlist.exe*를 얻으려면 [WDK 및 WinDbg 다운로드](/windows-hardware/drivers/download-the-wdk)에서 Debugging Tools for Windows를 다운로드하여 설치합니다.

## <a name="BKMK_reattach"></a> 프로세스에 다시 연결

선택 하 여에 이전에 연결 된 프로세스를 신속 하 게 연결할 수 있습니다 **디버깅할** > **프로세스에 다시 연결** (**Shift** + **Alt**+**P**). 이 명령은 선택 하면 디버거는 이전 프로세스 ID와 일치 하도록 첫 번째 시도 하 여에 연결 된 프로세스가 마지막으로 연결 하려고 즉시 경우 실패 하는 이전에 비교 하 여 프로세스 및 이름. 일치 하는 경우 또는 여러 프로세스 이름이 같은 경우는 **프로세스에 연결** 대화 상자를 열어 올바른 프로세스를 선택할 수 있습니다.

> [!NOTE]
> 합니다 **프로세스에 다시 연결** 명령은 Visual Studio 2017에서 시작 하 고 있습니다.

## <a name="BKMK_Scenarios"></a> 일반적인 디버깅 시나리오

사용 여부를 결정 하는 데 **프로세스에 연결** 및 어떤 연결할 프로세스를 다음 표에서 자세한 지침에 대 한 링크를 사용 하 여 몇 가지 일반적인 디버깅 시나리오를 보여 줍니다. 사용 가능한 경우. (의 목록은 전체 목록이 아닙니다.)

유니버설 Windows 앱 (UWP) 앱과 같은 일부 앱 유형에 대 한 프로세스 이름에 직접 연결 하지 않은 수 있지만를 사용 합니다 **디버그 Installed App Package** 대신 Visual Studio에서 메뉴 옵션 (표 참조).

디버거에서 C++로 작성된 코드에 연결하려면 코드에 `DebuggableAttribute`가 있어야 합니다. 이 특성은 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 링커 옵션으로 링크하여 자동으로 코드에 추가할 수 있습니다.

클라이언트 쪽 스크립트 디버깅에 대 한 스크립트 디버깅 활성화 되어야 합니다는 브라우저에서. Chrome에서 클라이언트 쪽 스크립트 디버깅을 위해 선택할 **키트 웹** 코드 유형으로 및 앱의 유형에 따라 하려면 모든 Chrome 인스턴스를 닫고 디버깅 모드에서 브라우저를 시작 해야 할 수 있습니다 (형식 `chrome.exe --remote-debugging-port=9222` 명령줄에서).

신속 하 게 연결할, Visual Studio에서 실행 중인 프로세스를 선택 하려면 입력 합니다. **Ctrl**+**Alt**+**P**, 한 다음의 첫 글자를 입력 합니다 프로세스 이름입니다.

|시나리오|메서드를 디버그 합니다.|프로세스 이름|정보 및 링크|
|-|-|-|-|
|원격 디버그 ASP.NET 4 또는 4.5에서 IIS 서버|원격 도구를 사용 하 고 **프로세스에 연결**|*w3wp.exe*|참조 [원격 원격 IIS 컴퓨터에서 ASP.NET 디버깅](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS 서버에서 원격 디버그 ASP.NET Core|원격 도구를 사용 하 고 **프로세스에 연결**|*dotnet.exe*|앱 배포에 대해서 [Publish to IIS](https://docs.asp.net/en/latest/publishing/iis.html)합니다. 디버깅을 참조 하세요. [원격 IIS 컴퓨터에서 원격 디버깅 Asp.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|지원 되는 앱 형식에 대 한 로컬 IIS 서버에서 클라이언트 쪽 스크립트 디버깅 |사용 하 여 **프로세스에 연결**|*chrome.exe*하십시오 *MicrosoftEdgeCP.exe*, 또는 *iexplore.exe*|스크립트 디버깅을 사용할 수 있어야 합니다. Chrome에 대 한 실행 해야 Chrome에서 디버그 모드를 선택 **Webkit 코드** 에 **연결할** 필드입니다.|
|디버그는 C#, Visual Basic 또는 C++ 로컬 컴퓨터에서 앱을|표준 디버깅 중 하나를 사용 하 여 (**F5**) 또는 **프로세스에 연결**|*\<appname>.exe*|대부분의 시나리오에서 사용 하 여 표준 디버깅 및 not **프로세스에 연결**합니다.|
|Windows 데스크톱 앱을 원격 디버그|원격 도구|N/A| 참조 [원격 디버그를 C# 또는 Visual Basic 앱](../debugger/remote-debugging-csharp.md) 하거나 [원격 디버그를 C++ 앱](../debugger/remote-debugging-cpp.md)|
|디버거 없이 앱을 시작한 후 로컬 컴퓨터에 ASP.NET 앱 디버그|사용 하 여 **프로세스에 연결**|*iiexpress.exe*|로드 앱을 확인 하면 도움이 될이 빠르고 같은 (예) 프로 파일링 하는 경우. |
|서버 프로세스에서 다른 유형의 지원 되는 앱 디버그|서버가 원격 인 경우 원격 도구를 사용 하 고 **프로세스에 연결**|*chrome.exe*하십시오 *iexplore.exe*, 또는 기타 프로세스|필요한 경우 리소스 모니터 프로세스를 식별 하는 데 사용 합니다. [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.|
|원격은 Windows 앱 (UWP (유니버설), OneCore, HoloLens, IoT 앱 디버깅|설치된 앱 패키지 디버그|N/A|참조 [설치 된 앱 패키지 디버그](debug-installed-app-package.md) 사용 하는 대신 **프로세스에 연결**|
|Visual Studio에서 시작 하지 않은 유니버설 Windows (UWP 앱), OneCore, HoloLens, IoT 앱을 디버그|설치된 앱 패키지 디버그|N/A|참조 [설치 된 앱 패키지 디버그](debug-installed-app-package.md) 사용 하는 대신 **프로세스에 연결**|

## <a name="use-debugger-features"></a>디버거 기능을 사용 하 여

(예: 중단점을 적중) Visual Studio 디버거의 전체 기능을 사용 하려면 로컬 소스 및 기호 앱 정확히 일치 해야 하는 프로세스에 연결 하는 경우. 즉, 디버거를 올바른 로드 수 있어야 [기호 (.pdb) 파일](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)합니다. 기본적으로 디버그 빌드에서 필요합니다.

원격 디버깅 시나리오에 대 한 Visual Studio에서 열려 있는 소스 코드 (또는 소스 코드의 복사본) 해야 합니다. 원격 컴퓨터에서 컴파일된 응용 프로그램 이진 파일은 로컬 컴퓨터에서와 동일한 빌드에서 가져와야 합니다.

일부 로컬 디버깅 시나리오에서 디버깅할 수 있습니다 Visual Studio에서 원본에 액세스할 수 없는 앱을 사용 하 여 올바른 기호 파일이 있는 경우. 기본적으로 디버그 빌드에서 필요합니다. 자세한 내용은 [기호 및 소스 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)합니다.

## <a name="BKMK_Troubleshoot_attach_errors"></a> 연결 오류 문제 해결
 실행 중인 프로세스에 디버거를 연결할 때 이 프로세스에는 한 가지 이상의 코드 형식이 포함될 수 있습니다. 디버거가 연결될 수 있는 코드 형식이 **코드 형식 선택** 대화 상자에서 표시되고 선택됩니다.

 때로는 디버거가 한 코드 형식에는 연결되고 다른 코드 형식에는 연결되지 않을 수도 있습니다. 이러한 문제는 원격 컴퓨터에서 실행 중인 프로세스에 연결하려 할 때 발생할 수 있습니다. 원격 컴퓨터에 설치된 원격 디버깅 구성 요소가 일부 코드 형식만 지원하고 다른 코드 형식은 지원하지 않을 수도 있습니다. 데이터베이스를 직접 디버깅하기 위해 두 개 이상의 프로세스에 연결하려는 경우에도 이 문제가 발생할 수 있습니다. SQL 디버깅은 단일 프로세스에 대한 연결만 지원합니다.

 디버거를 전부는 아니지만 일부 코드 형식에 연결할 수 경우 연결 하지 못했습니다 유형을 식별 하는 메시지가 표시 됩니다.

 적어도 하나의 코드 형식에 디버거가 성공적으로 연결되면 프로세스 디버깅을 진행할 수 있습니다. 이 경우 성공적으로 연결된 코드 형식만 디버깅할 수 있습니다. 프로세스에 연결 되지 않은 코드는 계속 실행 되지만 중단점을 설정, 데이터를 보거나, 해당 코드에 다른 디버깅 작업을 수행할 수 없습니다.

 디버거 코드 형식에 연결 하지 못했습니다 이유에 대 한 자세한 정보를 하려는 경우 해당 코드 형식에만 다시 연결을 시도 합니다.

 **코드 형식에 연결하지 못한 이유에 대한 자세한 정보를 얻으려면:**

1. 프로세스에서 분리합니다. 에 **디버그** 메뉴에서 **모두 분리**합니다.

1. 연결에 실패 한 코드 형식만 선택 프로세스에 다시 연결 합니다.

    1. **프로세스에 연결** 대화 상자의 **사용 가능한 프로세스** 목록에서 프로세스를 선택합니다.

    2. 선택 **선택**합니다.

    3. **코드 형식 선택** 대화 상자에서 **다음 코드 형식 디버깅** 을 선택하고 연결에 실패한 코드 형식을 선택합니다. 다른 코드 형식을 선택 취소 합니다.

    4. **확인**을 선택합니다.

    5. 에 **프로세스에 연결** 대화 상자에서 **연결**합니다.

    이렇게 하면 연결이 완전히 실패하고 자세한 오류 메시지가 나타납니다.

## <a name="see-also"></a>참고자료

- [여러 프로세스 디버그](../debugger/debug-multiple-processes.md)
- [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)
- [원격 디버깅](../debugger/remote-debugging.md)