---
title: 디버거를 사용 하 여 실행 중인 프로세스에 연결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
- C++
- CSharp
- FSharp
- VB
- c++
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 62
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 15b9921514f76d788430c1eda66603e9fc446361
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67891022"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio 디버거에서 실행 중인 프로세스에 연결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

로컬 또는 원격 컴퓨터에서 실행 중인 프로세스에 Visual Studio 디버거를 연결할 수 있습니다. 프로세스를 실행 한 후 클릭 **디버그 / 프로세스에 연결** (누르거나 **CTRL + ALT + P**)를 열려면 합니다 **프로세스에 연결** 대화 상자.

로컬 또는 원격 컴퓨터에서 실행 되는 앱을 디버그, 동시에 여러 프로세스 디버깅 또는 Visual Studio에서 생성 되지 않은 응용 프로그램 디버그에이 기능을 사용할 수 있습니다. 유용는 앱을 디버그 하려는 경우 되었지만 (어떤 이유로 든) 하면 시작 되지 않았으므로 앱 Visual Studio에서 디버거가 연결 된입니다. 예를 들어, 디버거 없이 앱을 실행 하는 경우 예외가 발생 수에 연결할 디버깅을 시작 하려면 앱을 실행 하는 프로세스입니다.

> [!TIP]
> 있는지 여부를 사용 해야 **프로세스에 연결** 디버깅 시나리오에 대 한? 참조 [일반적인 디버깅 시나리오](#BKMK_Scenarios)합니다. IIS에 배포 된, 참조 하는 ASP.NET 응용 프로그램을 디버그 하려는 경우 [원격 IIS 컴퓨터에서 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)합니다.

## <a name="BKMK_Attach_to_a_running_process"></a> 로컬 컴퓨터에서 실행 중인 프로세스에 연결
 프로세스에 연결 하려면 프로세스 이름을 알고 있어야 합니다 (참조 [일반적인 디버깅 시나리오](#BKMK_Scenarios) 몇 가지 일반적인 프로세스 이름에 대 한).

1. Visual Studio에서 선택 **디버그 / 프로세스에 연결** (누르거나 **CTRL + ALT + P**).

2. **프로세스에 연결** 대화 상자의 **사용 가능한 프로세스** 목록에서 연결할 프로그램을 찾습니다.

     원하는 프로세스를 신속 하 게 선택 하려면 프로세스 이름의 첫 글자를 입력 합니다. 프로세스 이름을 모르는 경우 [일반적인 디버깅 시나리오](#BKMK_Scenarios)합니다.

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     프로세스가 다른 사용자 계정으로 실행되고 있으면 **모든 사용자의 프로세스 표시** 확인란을 선택합니다.

3. **연결 대상** 상자에서 디버깅할 코드 형식이 표시되어 있는지 확인합니다. 기본 **자동** 설정은 디버깅할 코드 형식을 결정합니다. 코드 형식을 수동으로 설정하려면, 다음을 수행합니다.

    1. **연결 대상** 상자에서 **선택**을 클릭합니다.

    2. **코드 형식 선택** 대화 상자에서 **다음 코드 형식 디버깅** 을 클릭하고 디버깅할 형식을 선택합니다.

    3. **확인**을 클릭합니다.

4. **연결**을 클릭합니다.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> 원격 컴퓨터의 프로세스에 연결
 프로세스에 연결 하려면 프로세스 이름을 알고 있어야 합니다 (참조 [일반적인 디버깅 시나리오](#BKMK_Scenarios) 몇 가지 일반적인 프로세스 이름에 대 한). IIS에 배포 된 ASP.NET 앱에 대 한 자세한 지침은 [원격 IIS 컴퓨터에서 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)합니다. 다른 앱은 작업 관리자에서 프로세스 이름을 찾을 수 있습니다.

 **프로세스에 연결** 대화 상자를 사용할 때 원격 디버깅용으로 설정된 다른 컴퓨터를 선택할 수 있습니다. 자세한 내용은 [원격 디버깅](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)합니다. 원격 컴퓨터를 선택하면 해당 컴퓨터에서 실행되는 사용 가능한 프로세스의 목록을 볼 수 있고 디버깅을 위해 하나 이상의 프로세스에 연결할 수 있습니다.

 **원격 컴퓨터를 선택 합니다.**

1. Visual Studio에서 선택 **디버그 / 프로세스에 연결** (누르거나 **CTRL + ALT + P**).

2. **프로세스에 연결** 대화 상자의 **전송** 목록에서 적합한 연결 형식을 선택합니다. 대부분의 경우에는**기본값** 이 올바른 설정입니다.

   **전송** 설정은 디버깅 세션에 상관없이 유지됩니다.

3. **한정자** 목록 상자를 사용하여 다음 방법 중 하나로 원격 컴퓨터 이름을 선택합니다.

   1. **한정자** 목록 상자에 이름을 입력합니다.

      > [!NOTE]
      > 이후 단계에서는 원격 컴퓨터 이름을 사용 하 여 연결할 수 없습니다, 경우에 IP 주소를 사용 합니다. (포트 번호는 프로세스를 선택한 후 자동으로 나타날 수 있습니다. 또한이 직접 입력 합니다. 아래 그림에서 4020 경우 원격 디버거에 대 한 기본 포트)

   2. **한정자** 목록 상자 옆에 있는 드롭다운 화살표를 클릭하고 드롭다운 목록에서 컴퓨터 이름을 선택합니다.

   3. 클릭 합니다 **찾을** 단추 옆에 **한정자** 열려면 목록을 **원격 디버거 연결 선택** 대화 상자. **원격 디버거 연결 선택** 대화 상자에는 로컬 서브넷에 있는 모든 장치와 이더넷 케이블을 통해 컴퓨터에 직접 연결된 모든 장치가 나열됩니다. 원하는 컴퓨터 또는 디바이스를 클릭한 다음 **선택**을 클릭합니다.

      **한정자** 설정은 해당 한정자를 사용하여 디버깅 연결에 성공한 경우에만 디버깅 세션 간에 유지됩니다.

4. **새로 고침**을 클릭합니다.

     **사용 가능한 프로세스** 목록은 **프로세스** 대화 상자를 열 때 자동으로 표시됩니다. 대화 상자가 열려 있는 동안 백그라운드에서 프로세스를 시작하고 중지할 수 있습니다. 그러나 내용이 현재 상태가 아닐 수 있습니다. 언제든지 **새로 고침**을 클릭하여 목록을 새로 고치고 현재 프로세스 목록을 확인할 수 있습니다.

5. **프로세스에 연결** 대화 상자의 **사용 가능한 프로세스** 목록에서 연결할 프로그램을 찾습니다.

    프로세스가 다른 사용자 계정으로 실행되고 있으면 **모든 사용자의 프로세스 표시** 확인란을 선택합니다.

6. **연결**을 클릭합니다.

## <a name="additional-info"></a>추가 정보

디버깅하는 동안 여러 프로그램에 연결할 수 있지만 언제든지 디버거에서 활성화되는 프로그램은 한 개뿐입니다. **디버그 위치** 도구 모음이나 **프로세스** 창에서 활성 프로그램을 설정할 수 있습니다. 자세한 내용은 [방법: 현재 프로세스 설정](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e)합니다.

신뢰할 수 없는 사용자 계정에서 소유한 프로세스에 연결하면 보안 경고 확인 대화 상자가 나타납니다. 자세한 내용은 참조 하세요. [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결하면 위험할 수 있습니다. 다음 정보가 의심 스 럽 또는 확실 하지 않은 경우이 프로세스에 연결 하지 않는](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)합니다.

원격 데스크톱(터미널 서비스) 세션에서 디버그할 때 **사용 가능한 프로세스** 목록에 사용 가능한 프로세스 중 일부가 표시되지 않는 경우가 있습니다. 제한된 사용자 계정의 사용자로 Visual Studio를 실행하는 경우 서비스 및 w3wp.exe를 비롯한 다른 서버 프로세스에 사용되는 세션 0에서 실행되는 프로세스는 **사용 가능한 프로세스** 목록에 표시되지 않습니다. 관리자 계정으로 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 를 실행하거나 터미널 서비스 세션 대신 서버 콘솔에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 를 실행하여 이 문제를 해결할 수 있습니다. 이러한 해결 방법을 둘 다 사용할 수 없는 경우 세 번째 방법으로 Windows 명령줄에서 `vsjitdebugger.exe -p` *ProcessId* 를 실행하여 프로세스에 연결합니다. 프로세스 ID는 tlist.exe를 사용하여 확인할 수 있습니다. tlist.exe를 얻으려면  [WDK 및 WinDbg 다운로드](http://go.microsoft.com/fwlink/?LinkId=168279)에서 Debugging Tools for Windows를 다운로드하여 설치합니다.

## <a name="BKMK_Scenarios"></a> 일반적인 디버깅 시나리오

사용 해야 하는지 여부를 식별할 수 있도록 **프로세스에 연결** 및 프로세스에 연결 하는 몇 가지 일반적인 디버깅 시나리오는 다음과 같습니다 (목록 목록은 전체 목록이 아닙니다). 자세한 지침을 사용할 수 있는 링크를 제공 합니다.

일부 앱 형식 (예: Windows 스토어 앱)에 대 한 프로세스 이름에 직접 연결 하지 않은 수 있지만를 사용 합니다 **디버그 Installed App Package** 메뉴 옵션을 대신 (표 참조).

> [!NOTE]
> Visual Studio에서 기본 디버깅에 대 한 자세한 내용은 [디버거를 사용 하 여 시작](../debugger/getting-started-with-the-debugger.md)합니다.

|시나리오|메서드를 디버그 합니다.|프로세스 이름|정보 및 링크|
|-|-|-|-|
|로컬 컴퓨터의 관리 되는 또는 네이티브 앱 디버그|사용 하 여 프로세스에 연결 또는 [표준 디버깅](../debugger/getting-started-with-the-debugger.md)|*appname*.exe|대화 상자에 빠르게 액세스 하려면 사용 하 여 **CTRL + ALT + P** 프로세스 이름의 첫 글자를 입력 합니다.|
|디버거 없이 앱을 시작한 후 로컬 컴퓨터에 ASP.NET 앱 디버그|사용 하 여 프로세스에 연결|iiexpress.exe|로드 앱을 확인 하면 도움이 될이 빠르고 같은 (예) 프로 파일링 하는 경우. |
|원격 디버그 ASP.NET 4 또는 4.5에서 IIS 서버|원격 도구를 사용 하 고 프로세스에 연결|w3wp.exe|참조 [원격 IIS 컴퓨터에서 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS 서버에서 원격 디버그 ASP.NET Core|원격 도구를 사용 하 고 프로세스에 연결|dnx.exe|앱 배포에 대해서 [Publish to IIS](https://docs.asp.net/en/latest/publishing/iis.html)합니다. 디버깅을 참조 하세요. [원격 IIS 컴퓨터에서 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|서버 프로세스에서 다른 유형의 지원 되는 앱 디버그|(원격 서버 경우) 원격 도구를 사용 하 고 프로세스에 연결|iexplore.exe 또는 기타 프로세스|필요한 경우 작업 관리자 프로세스를 식별 하는 데 사용 합니다. 참조 [원격 디버깅](../debugger/remote-debugging.md) 및이 항목의 뒷부분에 나오는 섹션|
|Windows 데스크톱 앱을 원격 디버그|원격 도구와 F5|N/A| 참조 [원격 디버깅](../debugger/remote-debugging.md)|
|원격은 Windows (UWP (유니버설), OneCore, HoloLens, IoT 앱 디버깅|설치된 앱 패키지 디버그|N/A|사용 하 여 **디버그 / 기타 디버그 대상 / 설치 된 앱 패키지 디버그** 대신 **프로세스에 연결**|
|Visual Studio에서 시작 하지 않은 Windows (UWP (유니버설), OneCore, HoloLens, IoT 앱을 디버그|설치된 앱 패키지 디버그|N/A|사용 하 여 **디버그 / 기타 디버그 대상 / 설치 된 앱 패키지 디버그** 대신 **프로세스에 연결**|

> [!WARNING]
> JavaScript로 작성된 Windows 유니버설 앱에 연결하려면 먼저 앱에 디버깅을 사용하도록 설정해야 합니다. Windows 개발자 센터에서 [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) 을 참조하세요.

> [!NOTE]
> 디버거에서 C++로 작성된 코드에 연결하려면 코드에 `DebuggableAttribute`가 있어야 합니다. 이 특성은 [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) 링커 옵션으로 링크하여 자동으로 코드에 추가할 수 있습니다.

## <a name="what-debugger-features-can-i-use"></a>디버거 기능을 사용할 수 있나요?

(예: 중단점을 적중) Visual Studio 디버거의 전체 기능을 사용 하려면 로컬 소스 및 기호 파일을 실행 해야 정확히 일치를 프로세스에 연결할 때 (즉, 디버거를 올바른 로드 수 있어야 [기호 (.pbd) 파일 ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). 기본적으로 디버그 빌드에서 필요합니다.

원격 디버깅 시나리오에 대 한 Visual Studio에서 열려 있는 소스 코드 (또는 소스 코드의 복사본) 해야 합니다. 원격 컴퓨터에서 컴파일된 응용 프로그램 이진 파일은 로컬 컴퓨터에서와 동일한 빌드에서 가져와야 합니다.

일부 로컬 디버깅 시나리오에서 디버깅할 수 Visual Studio에서 원본에 액세스할 수 없는 앱을 사용 하 여 올바른 기호 파일이 있는 경우 (기본적으로이 필요 디버그 빌드). 자세한 내용은 참조 하세요. [소스 파일과 기호 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)합니다.

## <a name="BKMK_Troubleshoot_attach_errors"></a> 연결 오류 문제 해결
 실행 중인 프로세스에 디버거를 연결할 때 이 프로세스에는 한 가지 이상의 코드 형식이 포함될 수 있습니다. 디버거가 연결될 수 있는 코드 형식이 **코드 형식 선택** 대화 상자에서 표시되고 선택됩니다.

 때로는 디버거가 한 코드 형식에는 연결되고 다른 코드 형식에는 연결되지 않을 수도 있습니다. 이러한 문제는 원격 컴퓨터에서 실행 중인 프로세스에 연결하려 할 때 발생할 수 있습니다. 원격 컴퓨터에 설치된 원격 디버깅 구성 요소가 일부 코드 형식만 지원하고 다른 코드 형식은 지원하지 않을 수도 있습니다. 데이터베이스를 직접 디버깅하기 위해 두 개 이상의 프로세스에 연결하려는 경우에도 이 문제가 발생할 수 있습니다. SQL 디버깅은 단일 프로세스에 대한 연결만 지원합니다.

 디버거를 일부 코드 형식에 연결할 수 있지만 모든 코드 형식에 연결할 수는 없는 경우 연결할 수 없는 형식을 알려 주는 메시지가 나타납니다.

 적어도 하나의 코드 형식에 디버거가 성공적으로 연결되면 프로세스 디버깅을 진행할 수 있습니다. 이 경우 성공적으로 연결된 코드 형식만 디버깅할 수 있습니다. 위 예제 메시지에서는 스크립트 코드 형식에 연결하지 못했음을 보여 줍니다. 따라서 이 프로세스 내의 스크립트 코드는 디버깅할 수 없습니다. 스크립트 코드는 프로세스 내에서 계속 실행되지만 스크립트에서 중단점을 설정하거나 데이터를 보거나 기타 디버깅 작업을 수행할 수는 없습니다.

 디버거가 연결되지 않는 특정 코드 형식에만 다시 연결을 시도하면 해당 코드 형식에 디버거가 연결되지 않는 이유를 더 구체적으로 확인할 수 있습니다.

 **이유 코드 형식 연결 실패에 대 한 특정 정보를 얻으려면**

1. 프로세스에서 분리합니다. **디버그** 메뉴에서 **모두 분리**를 클릭합니다.

2. 프로세스에 다시 연결하여 한 코드 형식만 선택합니다.

   1. **프로세스에 연결** 대화 상자의 **사용 가능한 프로세스** 목록에서 프로세스를 선택합니다.

   2. **선택**을 클릭합니다.

   3. **코드 형식 선택** 대화 상자에서 **다음 코드 형식 디버깅** 을 선택하고 연결에 실패한 코드 형식을 선택합니다. 다른 코드는 모두 선택 해제합니다.

   4. **확인**을 클릭합니다. **코드 형식 선택** 대화 상자가 닫힙니다.

   5. **프로세스에 연결** 대화 상자에서 **연결**을 클릭합니다.

      이렇게 하면 연결이 완전히 실패하고 자세한 오류 메시지가 나타납니다.

## <a name="see-also"></a>참고 항목
 [여러 프로세스 디버깅](../debugger/debug-multiple-processes.md) [-Just-in-time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md) [원격 디버깅](../debugger/remote-debugging.md)
