---
title: Attach to Running Processes with the Debugger | Microsoft Docs
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
ms.openlocfilehash: 03cd890802e5563ce2daeb78438c56f4452d74f0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299520"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio 디버거에서 실행 중인 프로세스에 연결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

로컬 또는 원격 컴퓨터에서 실행 중인 프로세스에 Visual Studio 디버거를 연결할 수 있습니다. After the process is running, click **Debug / Attach to Process** (or press **CTRL+ALT+P**) to open the **Attach to Process** dialog box.

You can use this capability to debug apps that are running on a local or remote computer, debug multiple processes simultaneously, or debug an application that was not created in Visual Studio. It is often useful when you want to debug an app, but (for whatever reason) you did not start the app from Visual Studio with the debugger attached. For example, if you are running the app without the debugger and hit an exception, you might then attach to the process running the app to begin debugging.

> [!TIP]
> Not sure whether you need to use **Attach to Process** for your debugging scenario? See [Common debugging scenarios](#BKMK_Scenarios). If you want to debug ASP.NET applications that have been deployed to IIS, see [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

## <a name="BKMK_Attach_to_a_running_process"></a> Attach to a running process on the local machine
 In order to attach to a process, you must know the name of the process (see [Common debugging scenarios](#BKMK_Scenarios) for a few common process names).

1. In Visual Studio, select **Debug / Attach to Process** (or press **CTRL+ALT+P**).

2. **프로세스에 연결** 대화 상자의 **사용 가능한 프로세스** 목록에서 연결할 프로그램을 찾습니다.

     To quickly select the process you want, type the first letter of the process name. If you don't know the process name, see [Common debugging scenarios](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     프로세스가 다른 사용자 계정으로 실행되고 있으면 **모든 사용자의 프로세스 표시** 확인란을 선택합니다.

3. **연결 대상** 상자에서 디버깅할 코드 형식이 표시되어 있는지 확인합니다. 기본 **자동** 설정은 디버깅할 코드 형식을 결정합니다. 코드 형식을 수동으로 설정하려면, 다음을 수행합니다.

    1. **연결 대상** 상자에서 **선택**을 클릭합니다.

    2. **코드 형식 선택** 대화 상자에서 **다음 코드 형식 디버깅** 을 클릭하고 디버깅할 형식을 선택합니다.

    3. **확인**을 클릭합니다.

4. **연결**을 클릭합니다.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> 원격 컴퓨터의 프로세스에 연결
 In order to attach to a process, you must know the name of the process (see [Common debugging scenarios](#BKMK_Scenarios) for a few common process names). For more complete guidance for ASP.NET apps that have been deployed to IIS, see [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). 다른 앱은 작업 관리자에서 프로세스 이름을 찾을 수 있습니다.

 **프로세스에 연결** 대화 상자를 사용할 때 원격 디버깅용으로 설정된 다른 컴퓨터를 선택할 수 있습니다. For more information, see [Remote Debugging](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). 원격 컴퓨터를 선택하면 해당 컴퓨터에서 실행되는 사용 가능한 프로세스의 목록을 볼 수 있고 디버깅을 위해 하나 이상의 프로세스에 연결할 수 있습니다.

 **To select a remote computer:**

1. In Visual Studio, select **Debug / Attach to Process** (or press **CTRL+ALT+P**).

2. **프로세스에 연결** 대화 상자의 **전송** 목록에서 적합한 연결 형식을 선택합니다. 대부분의 경우에는**기본값** 이 올바른 설정입니다.

   **전송** 설정은 디버깅 세션에 상관없이 유지됩니다.

3. **한정자** 목록 상자를 사용하여 다음 방법 중 하나로 원격 컴퓨터 이름을 선택합니다.

   1. **한정자** 목록 상자에 이름을 입력합니다.

      > [!NOTE]
      > If, in later steps, you can't connect using the remote computer name, use the IP address. (The port number may appear automatically after selecting the process. You can also enter it manually. In the illustration below, 4020 is the default port for the remote debugger.)

   2. **한정자** 목록 상자 옆에 있는 드롭다운 화살표를 클릭하고 드롭다운 목록에서 컴퓨터 이름을 선택합니다.

   3. Click the **Find** button next to the **Qualifier** list to open the **Select Remote Debugger Connection** dialog box. **원격 디버거 연결 선택** 대화 상자에는 로컬 서브넷에 있는 모든 디바이스와 이더넷 케이블을 통해 컴퓨터에 직접 연결된 모든 디바이스가 나열됩니다. 원하는 컴퓨터 또는 디바이스를 클릭한 다음 **선택**을 클릭합니다.

      **한정자** 설정은 해당 한정자를 사용하여 디버깅 연결에 성공한 경우에만 디버깅 세션 간에 유지됩니다.

4. **새로 고침**을 클릭합니다.

     **사용 가능한 프로세스** 목록은 **프로세스** 대화 상자를 열 때 자동으로 표시됩니다. 대화 상자가 열려 있는 동안 백그라운드에서 프로세스를 시작하고 중지할 수 있습니다. 그러나 내용이 현재 상태가 아닐 수 있습니다. 언제든지 **새로 고침**을 클릭하여 목록을 새로 고치고 현재 프로세스 목록을 확인할 수 있습니다.

5. **프로세스에 연결** 대화 상자의 **사용 가능한 프로세스** 목록에서 연결할 프로그램을 찾습니다.

    프로세스가 다른 사용자 계정으로 실행되고 있으면 **모든 사용자의 프로세스 표시** 확인란을 선택합니다.

6. **연결**을 클릭합니다.

## <a name="additional-info"></a>Additional info

디버깅하는 동안 여러 프로그램에 연결할 수 있지만 언제든지 디버거에서 활성화되는 프로그램은 한 개뿐입니다. **디버그 위치** 도구 모음이나 **프로세스** 창에서 활성 프로그램을 설정할 수 있습니다. 자세한 내용은 [방법: 현재 프로세스 설정](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e)을 참조하세요.

신뢰할 수 없는 사용자 계정에서 소유한 프로세스에 연결하면 보안 경고 확인 대화 상자가 나타납니다. 자세한 내용은 참조 하세요. [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결 하면 위험할 수 있습니다. 다음 정보가 의심 스 럽 또는 확실 하지 않은 경우이 프로세스에 연결 하지 않는](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)합니다.

원격 데스크톱(터미널 서비스) 세션에서 디버그할 때 **사용 가능한 프로세스** 목록에 사용 가능한 프로세스 중 일부가 표시되지 않는 경우가 있습니다. 제한된 사용자 계정의 사용자로 Visual Studio를 실행하는 경우 서비스 및 w3wp.exe를 비롯한 다른 서버 프로세스에 사용되는 세션 0에서 실행되는 프로세스는 **사용 가능한 프로세스** 목록에 표시되지 않습니다. 관리자 계정으로 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 를 실행하거나 터미널 서비스 세션 대신 서버 콘솔에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 를 실행하여 이 문제를 해결할 수 있습니다. 이러한 해결 방법을 둘 다 사용할 수 없는 경우 세 번째 방법으로 Windows 명령줄에서 `vsjitdebugger.exe -p` *ProcessId* 를 실행하여 프로세스에 연결합니다. 프로세스 ID는 tlist.exe를 사용하여 확인할 수 있습니다. tlist.exe를 얻으려면  [WDK 및 WinDbg 다운로드](https://go.microsoft.com/fwlink/?LinkId=168279)에서 Debugging Tools for Windows를 다운로드하여 설치합니다.

## <a name="BKMK_Scenarios"></a> Common debugging scenarios

To help you identify whether you need to use **Attach to process** and what process to attach to, a few common debugging scenarios are shown here (the list is not exhaustive). Where more instructions are available, we provide links.

For some app types (like Windows Store apps), you don't attach directly to a process name, but use the **Debug Installed App Package** menu option instead (see table).

> [!NOTE]
> For information about basic debugging in Visual Studio, see [Getting started with the debugger](../debugger/getting-started-with-the-debugger.md).

|시나리오|Debug Method|프로세스 이름|Notes and Links|
|-|-|-|-|
|Debug a managed or native app on the local machine|Use attach to process or [standard debugging](../debugger/getting-started-with-the-debugger.md)|*appname*.exe|To quickly access the dialog box, use **CTRL+ALT+P** and then type the first letter of the process name.|
|Debug ASP.NET apps on the local machine after starting the app without the debugger|Use attach to process|iiexpress.exe|This may be helpful to make your app load faster, such as (for example) when profiling. |
|Remote debug ASP.NET 4 or 4.5 on an IIS server|Use remote tools and attach to process|w3wp.exe|See [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Remote debug ASP.NET Core on an IIS server|Use remote tools and attach to process|dnx.exe|For app deployment, see [Publish to IIS](https://docs.asp.net/en/latest/publishing/iis.html). For debugging, see [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Debug other supported app types on a server process|Use remote tools (if server is remote) and attach to process|iexplore.exe or other processes|If necessary, use Task Manager to help identify the process. See [Remote Debugging](../debugger/remote-debugging.md) and later sections in this topic|
|Remote debug a Windows desktop app|Remote Tools and F5|해당 사항 없음| See [Remote Debugging](../debugger/remote-debugging.md)|
|Remote debug a Windows Universal (UWP), OneCore, HoloLens, or IoT app|설치된 앱 패키지 디버그|해당 사항 없음|Use **Debug / Other Debug Targets / Debug Installed App Package** instead of **Attach to process**|
|Debug a Windows Universal (UWP), OneCore, HoloLens, or IoT app that you didn't start from Visual Studio|설치된 앱 패키지 디버그|해당 사항 없음|Use **Debug / Other Debug Targets / Debug Installed App Package** instead of **Attach to process**|

> [!WARNING]
> JavaScript로 작성된 Windows 유니버설 앱에 연결하려면 먼저 앱에 디버깅을 사용하도록 설정해야 합니다. Windows 개발자 센터에서 [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) 을 참조하세요.

> [!NOTE]
> 디버거에서 C++로 작성된 코드에 연결하려면 코드에 `DebuggableAttribute`가 있어야 합니다. 이 특성은 [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) 링커 옵션으로 링크하여 자동으로 코드에 추가할 수 있습니다.

## <a name="what-debugger-features-can-i-use"></a>What debugger features can I use?

To use the full features of the Visual Studio debugger (like hitting breakpoints) when attaching to a process, the executable must exactly match your local source and symbols (that is, the debugger must be able to load the correct [symbol (.pbd) files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). By default, this requires a debug build.

For remote debugging scenarios, you must have the source code (or a copy of the source code) already open in Visual Studio. The compiled app binaries on the remote machine must come from the same build as on the local machine.

In some local debugging scenarios, you can debug in Visual Studio with no access to the source if the correct symbol files are present with the app (by default, this requires a debug build). For more info, see [Specify Symbol and Source Files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a> 연결 오류 문제 해결
 실행 중인 프로세스에 디버거를 연결할 때 이 프로세스에는 한 가지 이상의 코드 형식이 포함될 수 있습니다. 디버거가 연결될 수 있는 코드 형식이 **코드 형식 선택** 대화 상자에서 표시되고 선택됩니다.

 때로는 디버거가 한 코드 형식에는 연결되고 다른 코드 형식에는 연결되지 않을 수도 있습니다. 이러한 문제는 원격 컴퓨터에서 실행 중인 프로세스에 연결하려 할 때 발생할 수 있습니다. 원격 컴퓨터에 설치된 원격 디버깅 구성 요소가 일부 코드 형식만 지원하고 다른 코드 형식은 지원하지 않을 수도 있습니다. 데이터베이스를 직접 디버깅하기 위해 두 개 이상의 프로세스에 연결하려는 경우에도 이 문제가 발생할 수 있습니다. SQL 디버깅은 단일 프로세스에 대한 연결만 지원합니다.

 디버거를 일부 코드 형식에 연결할 수 있지만 모든 코드 형식에 연결할 수는 없는 경우 연결할 수 없는 형식을 알려 주는 메시지가 나타납니다.

 적어도 하나의 코드 형식에 디버거가 성공적으로 연결되면 프로세스 디버깅을 진행할 수 있습니다. 이 경우 성공적으로 연결된 코드 형식만 디버깅할 수 있습니다. 위 예제 메시지에서는 스크립트 코드 형식에 연결하지 못했음을 보여 줍니다. 따라서 이 프로세스 내의 스크립트 코드는 디버깅할 수 없습니다. 스크립트 코드는 프로세스 내에서 계속 실행되지만 스크립트에서 중단점을 설정하거나 데이터를 보거나 기타 디버깅 작업을 수행할 수는 없습니다.

 디버거가 연결되지 않는 특정 코드 형식에만 다시 연결을 시도하면 해당 코드 형식에 디버거가 연결되지 않는 이유를 더 구체적으로 확인할 수 있습니다.

 **To obtain specific information about why a code type failed to attach**

1. 프로세스에서 분리합니다. **디버그** 메뉴에서 **모두 분리**를 클릭합니다.

2. 프로세스에 다시 연결하여 한 코드 형식만 선택합니다.

   1. **프로세스에 연결** 대화 상자의 **사용 가능한 프로세스** 목록에서 프로세스를 선택합니다.

   2. **선택**을 클릭합니다.

   3. **코드 형식 선택** 대화 상자에서 **다음 코드 형식 디버깅** 을 선택하고 연결에 실패한 코드 형식을 선택합니다. 다른 코드는 모두 선택 해제합니다.

   4. **확인**을 클릭합니다. **코드 형식 선택** 대화 상자가 닫힙니다.

   5. **프로세스에 연결** 대화 상자에서 **연결**을 클릭합니다.

      이렇게 하면 연결이 완전히 실패하고 자세한 오류 메시지가 나타납니다.

## <a name="see-also"></a>관련 항목:
 [Debug Multiple Processes](../debugger/debug-multiple-processes.md) [Just-In-Time Debugging](../debugger/just-in-time-debugging-in-visual-studio.md) [Remote Debugging](../debugger/remote-debugging.md)
