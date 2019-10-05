---
title: 여러 프로세스 디버깅 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a2679825d41a6360dde05e7511d607f8be69dfa
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434103"
---
# <a name="debug-multiple-processes"></a>여러 프로세스 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로세스 디버깅 시작, 프로세스 간 전환, 실행 중단 및 계속 실행, 소스 단계별 실행, 디버깅 중지 및 프로세스 종료 또는 프로세스에서 분리를 수행하는 방법을 설명합니다.  
  
## <a name="BKMK_Contents"></a> 목차  
 [여러 프로세스의 실행 동작 구성](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [소스 및 기호 (.pdb) 파일 찾기](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [VS 솔루션의 여러 프로세스 시작, 프로세스에 연결, 디버거에서 프로세스를 자동으로 시작](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [프로세스 전환, 실행 중단 및 계속 실행, 소스 단계별 실행](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [디버깅 중지, 종료 또는 프로세스에서 분리](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> 여러 프로세스의 실행 동작 구성  
 여러 프로세스가 디버거에서 실행되는 경우 기본적으로 디버거 명령을 중단하고 단계별로 실행하고 중지하면 대개 모든 프로세스가 영향을 받습니다. 예를 들어 한 프로세스가 중단점에서 일시 중단되면 다른 모든 프로세스의 실행도 일시 중단됩니다. 이 기본 동작을 변경하여 실행 명령의 대상을 더욱 세부적으로 제어할 수 있습니다.  
  
1. **디버그** 메뉴에서 **옵션 및 설정**을 선택합니다.  
  
2. 에 **디버깅**, **일반** 페이지의 선택을 취소 합니다 **한 프로세스가 중단 될 때 모든 프로세스 중단** 확인란 합니다.  
  
   ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> 소스 및 기호(.pdb) 파일 찾기  
 프로세스의 소스 코드를 탐색하려면 디버거가 프로세스의 소스 파일과 기호 파일에 액세스할 수 있어야 합니다. [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.  
  
 프로세스의 파일에 액세스할 수 없는 경우 디스어셈블리 창을 사용하여 탐색할 수 있습니다. [방법: 디스어셈블리 창 사용](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> VS 솔루션의 여러 프로세스 시작, 프로세스에 연결, 디버거에서 프로세스를 자동으로 시작  
  
- [Visual Studio 솔루션의 여러 프로세스 디버깅 시작](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [시작 프로젝트 변경](#BKMK_Change_the_startup_project) • [솔루션의 특정 프로젝트 시작](#BKMK_Start_a_specific_project_in_a_solution) • [의 여러 프로젝트 시작을 솔루션](#BKMK_Start_multiple_projects_in_a_solution) • [프로세스에 연결](#BKMK_Attach_to_a_process) • [디버거에서 프로세스를 자동으로 시작](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> 자식 프로젝트가 동일한 솔루션에 있는 경우에도 디버거는 디버깅된 프로세스에서 시작되는 자식 프로세스에 자동으로 연결되지 않습니다. 자식 프로세스를 디버깅하려면:  
> 
> - 자식 프로세스가 시작된 후 자식 프로세스에 연결합니다.  
> 
>   또는  
>   - 디버거의 새 인스턴스에서 자식 프로세스를 자동으로 시작하도록 Windows를 구성합니다.  
  
### <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Visual Studio 솔루션의 여러 프로세스 디버깅 시작  
 독립적으로 실행될 수 있는 Visual Studio 솔루션에 프로젝트가 두 개 이상 있는 경우(각기 다른 프로세스에서 실행되는 프로젝트) 디버거가 시작하는 프로젝트를 선택할 수 있습니다.  
  
 ![프로젝트에 대 한 시작 유형 변경](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="BKMK_Change_the_startup_project"></a> 시작 프로젝트 변경  
 솔루션에 대 한 시작 프로젝트를 변경 하려면 솔루션 탐색기에서 프로젝트를 선택 하 고 선택한 **시작 프로젝트로 설정** 상황에 맞는 메뉴입니다.  
  
#### <a name="BKMK_Start_a_specific_project_in_a_solution"></a> 솔루션의 특정 프로젝트 시작  
 프로젝트를 솔루션에 대 한 기본 시작 프로젝트를 변경 하지 않고를 시작 하려면 솔루션 탐색기에서 프로젝트를 선택 하 고 선택한 **디버그** 상황에 맞는 메뉴입니다. 선택할 수 있습니다 **새 인스턴스 시작** 하거나 **새 인스턴스 한 단계씩 코드 실행**합니다.  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [VS 솔루션의 여러 프로세스 시작, 프로세스에 연결, 디버거에서 프로세스를 자동으로 시작](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
#### <a name="BKMK_Start_multiple_projects_in_a_solution"></a> 솔루션의 여러 프로젝트 시작  
  
1. 솔루션 탐색기에서 솔루션을 선택 하 고 선택한 **속성** 상황에 맞는 메뉴입니다.  
  
2. 선택 **공용 속성**를 **시작 프로젝트** 에 **속성** 대화 상자.  
  
3. 선택 변경 하려는 각 프로젝트에 대해 **시작**를 **디버깅 하지 않고 시작**, 또는 **None**합니다.  
  
   ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [VS 솔루션의 여러 프로세스 시작, 프로세스에 연결, 디버거에서 프로세스를 자동으로 시작](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
### <a name="BKMK_Attach_to_a_process"></a> 프로세스에 연결  
 디버거 될 수도 있습니다 *연결* Visual Studio 외부의 프로세스에서 실행 되는 프로그램을 원격 장치에서 실행 중인 프로그램을 포함 합니다. 일단 프로그램에 연결되면 디버거 실행 명령을 사용하고 프로그램 상태를 검사하는 등의 작업을 수행할 수 있습니다. 디버그 정보를 사용하여 프로그램을 빌드했는지 여부, 프로그램의 소스 코드에 액세스할 수 있는지 여부 및 공용 언어 런타임 JIT 컴파일러가 디버그 정보를 추적하고 있는지 여부에 따라 프로그램 검사 기능이 제한될 수 있습니다.  
  
 참조 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) 자세한 내용은 합니다.  
  
 **로컬 컴퓨터에서 실행 중인 프로세스에 연결**  
  
 선택 **디버그**하십시오 **프로세스에 연결**합니다. 에 **프로세스에 연결** 대화 상자에서 프로세스를 선택 합니다는 **사용 가능한 프로세스** 목록에서 선택한 다음 **연결**합니다.  
  
 ![처리 대화 상자에 연결](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
### <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> 디버거에서 프로세스를 자동으로 시작  
 경우에 따라 다른 프로세스에서 시작된 프로그램의 시작 코드를 디버깅해야 할 수도 있습니다. 서비스 및 사용자 지정 설치 작업을 예로 들 수 있습니다. 이러한 시나리오에서는 애플리케이션을 시작할 때 디버거를 시작하고 자동으로 연결할 수 있습니다.  
  
1. 레지스트리 편집기를 엽니다 (**regedit.exe**).  
  
2. 로 이동 합니다 **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options** 폴더입니다.  
  
3. 디버거에서 시작할 응용 프로그램의 폴더를 선택합니다.  
  
    앱의 이름을 하위 폴더로 없으면 선택 **Image File Execution Options** 를 선택한 후 **새로 만들기**, **키** 상황에 맞는 메뉴입니다. 새 키를 선택, 선택 **이름 바꾸기** 바로 가기 메뉴에서 앱의 이름을 입력 합니다.  
  
4. 앱 폴더의 상황에 맞는 메뉴에서 선택 **새로 만들기**하십시오 **문자열 값**.  
  
5. 새 값의 이름을 변경할 **새 값** 에 `debugger`입니다.  
  
6. Debugger 항목의 상황에 맞는 메뉴에서 선택 **수정**합니다.  
  
7. 문자열 편집 대화 상자에서 입력 `vsjitdebugger.exe` 에 **데이터 값** 상자입니다.  
  
    ![문자열 편집 대화 상자](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Regedit.exe의 자동 디버거 시작 항목](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> 프로세스 전환, 실행 중단 및 계속 실행, 소스 단계별 실행  
  
- [프로세스 간 전환](#BKMK_Switch_between_processes) • [중단, 단계별 실행, 및 계속 명령을](#BKMK_Break__step__and_continue_commands)  
  
### <a name="BKMK_Switch_between_processes"></a> 프로세스 간 전환  
 디버깅하는 동안 여러 프로세스에 연결할 수 있지만 한 번에 프로세스 하나만 디버거에서 활성화됩니다. 활성을 설정할 수 있습니다 또는 *현재* 디버그 위치 도구 모음 또는 프로세스를 **프로세스** 창입니다. 프로세스 간에 전환하려면 두 프로세스가 모두 중단 모드여야 합니다.  
  
 **현재 프로세스를 설정 하려면**  
  
- 디버그 위치 도구 모음에서 선택 **프로세스** 보려는 합니다 **프로세스** 목록 상자입니다. 현재 프로세스로 지정할 프로세스를 선택합니다.  
  
   ![프로세스 간 전환](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   경우는 **디버그 위치** 도구 모음이 표시 되지 않으면, 선택 **도구**합니다 **사용자 지정**합니다. 에 **도구 모음** 탭에서 **디버그 위치**합니다.  
  
- 엽니다는 **프로세스** 창 (바로 가기 **Ctrl + Alt + Z**) 현재 프로세스로 설정할 프로세스 찾아 두 번 클릭 합니다.  
  
   ![프로세스 창](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   현재 프로세스는 노란색 화살표로 표시됩니다.  
  
  프로젝트로 전환하면 해당 프로젝트가 디버깅 목적의 현재 프로세스로 설정됩니다. 사용자에게 표시되는 모든 디버거 창은 현재 프로세스의 상태를 보여 주며, 모든 단계별 실행 명령은 현재 프로세스에만 영향을 미칩니다.  
  
  ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [프로세스 전환, 실행 중단 및 계속 실행, 소스 단계별 실행](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
### <a name="BKMK_Break__step__and_continue_commands"></a> 명령 중단, 단계별 실행 및 계속 실행  
  
> [!NOTE]
> 기본적으로 디버거 명령을 중단하고 계속 실행하고 단계별로 실행하면 디버그 중인 모든 프로세스가 영향을 받습니다. 이 동작을 변경 하려면 참조 [여러 프로세스의 실행 동작 구성](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**명령**|**한 프로세스가 중단 될 때 모든 프로세스 중단**<br /><br /> 선택됨(기본값)|**한 프로세스가 중단 될 때 모든 프로세스 중단**<br /><br /> 선택 취소됨|  
|**디버그** 메뉴:<br /><br /> -   **모두 중단**|모든 프로세스가 중단됩니다.|모든 프로세스가 중단됩니다.|  
|**디버그** 메뉴:<br /><br /> -   **계속**|모든 프로세스가 다시 시작됩니다.|일시 중단된 모든 프로세스가 다시 시작됩니다.|  
|**디버그** 메뉴:<br /><br /> -   **한 단계씩 코드 실행**<br />-   **프로시저 단위 실행**<br />-   **프로시저 나가기**|현재 프로세스가 단계별로 실행되는 동안 모든 프로세스가 실행됩니다.<br /><br /> 그런 다음 모든 프로세스가 중단됩니다.|현재 프로세스가 단계별로 실행됩니다.<br /><br /> 일시 중단된 프로세스가 다시 시작됩니다.<br /><br /> 실행 중인 프로세스가 계속 실행됩니다.|  
|**디버그** 메뉴:<br /><br /> -   **현재 프로세스 한 단계씩 실행**<br />-   **현재 프로세스 단계**<br />-   **현재 프로세스 프로시저 나가기**|N/A|현재 프로세스가 단계별로 실행됩니다.<br /><br /> 다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|  
|소스 창<br /><br /> -   **Breakpoint**|모든 프로세스가 중단됩니다.|소스 창 프로세스만 중단됩니다.|  
|소스 창 상황에 맞는 메뉴:<br /><br /> -   **커서까지 실행**<br /><br /> 소스 창이 현재 프로세스에 있어야 합니다.|모든 프로세스가 소스 창 프로세스가 커서까지 실행되는 동안 실행되었다가 중단됩니다.<br /><br /> 그런 다음 다른 모든 프로세스가 중단됩니다.|소스 창 프로세스가 커서까지 실행됩니다.<br /><br /> 다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|  
|**프로세스** 창 상황에 맞는 메뉴:<br /><br /> -   **프로세스 중단**|N/A|선택한 프로세스가 중단됩니다.<br /><br /> 다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|  
|**프로세스** 창 상황에 맞는 메뉴:<br /><br /> -   **프로세스를 계속 합니다.**|N/A|선택한 프로세스가 다시 시작됩니다.<br /><br /> 다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [프로세스 전환, 실행 중단 및 계속 실행, 소스 단계별 실행](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> 디버깅 중지, 종료 또는 프로세스에서 분리  
  
- [중지, 종료 및 분리 명령](#BKMK_Stop__terminate__and_detach_commands)  
  
  기본적으로 선택 하면 **디버깅할**, **디버깅 중지** 디버거가 종료 또는 프로세스에서 열린 하는 방법에 따라 모든 프로세스에서 분리 여러 프로세스가 디버거에서 열려 있는 경우는 디버거:  
  
- 현재 프로세스가 디버거에서 시작된 경우 프로세스가 종료됩니다.  
  
- 디버거를 현재 프로세스에 연결한 경우 디버거는 프로세스에서 분리되며 프로세스는 계속 실행됩니다.  
  
  Visual Studio 솔루션의 프로세스 디버깅을 시작 하는 경우 이미 실행 중인 다른 프로세스에 연결 하 고 선택한 예를 들어 **디버깅 중지**, 디버깅 세션이 끝나면 Visual Studio에서 시작 된 프로세스 종료, 연결 하는 프로세스는 계속 실행 하는 동안. 다음 절차를 사용하여 디버깅을 중지하는 방법을 제어할 수 있습니다.  
  
> [!NOTE]
> 합니다 **한 프로세스가 중단 될 때 모든 프로세스 중단** 옵션 디버깅 또는 종료 및 프로세스에서 분리를 중지 하는 중에 영향을 주지 않습니다.  
  
 **디버깅 중지는 개별 프로세스에 미치는 영향을 변경 하려면**  
  
- 엽니다는 **프로세스** 창 (바로 가기 **Ctrl + Alt + Z**). 프로세스 선택 및 선택 하거나 선택을 취소 합니다 **디버깅 중지 시 분리** 확인란 합니다.  
  
### <a name="BKMK_Stop__terminate__and_detach_commands"></a> 중지, 종료 및 분리 명령  
  
|||  
|-|-|  
|**명령**|**설명**|  
|**디버그** 메뉴:<br /><br /> -   **디버깅을 중지합니다**|동작에서 변경 하지 않으면 **프로세스** 창이 **디버깅 중지 시 분리** 옵션:<br /><br /> 1.  디버거에서 시작된 프로세스가 종료됩니다.<br />2.  연결된 프로세스가 디버거에서 분리됩니다.|  
|**디버그** 메뉴:<br /><br /> -   **모두 종료**|모든 프로세스가 종료됩니다.|  
|**디버그** 메뉴:<br /><br /> -   **모두 분리**|디버거가 모든 프로세스에서 분리됩니다.|  
|**프로세스** 창 상황에 맞는 메뉴:<br /><br /> -   **프로세스 분리**|디버거가 선택된 프로세스에서 분리됩니다.<br /><br /> 다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|  
|**프로세스** 창 상황에 맞는 메뉴:<br /><br /> -   **프로세스 종료**|선택한 프로세스가 종료됩니다.<br /><br /> 다른 프로세스가 기존 상태(일시 중단됨 또는 실행 중)를 유지합니다.|  
|**프로세스** 창 상황에 맞는 메뉴:<br /><br /> -   **디버깅 중지 시 분리**|동작을 설정/해제 **디버그**하십시오 **디버깅 중지** 선택한 프로세스:<br /><br /> -확인합니다. 디버거는 프로세스에서 분리 됩니다.<br />-선택을 취소 합니다. 프로세스가 종료됩니다.|  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [디버깅 중지, 종료 또는 프로세스에서 분리](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="see-also"></a>참고 항목  
 [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Navigating through Code with the Debugger](../debugger/navigating-through-code-with-the-debugger.md) (디버거로 코드 탐색)  
 [Just-in-time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
