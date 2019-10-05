---
title: 디버거로 코드 탐색 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f79ece781db19f2483ef1dd6cb0a81ff7cf78e06
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430979"
---
# <a name="navigating-through-code-with-the-debugger"></a>디버거로 코드 탐색
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

명령 및 바로 가기를 디버거에서 코드를 탐색 하는 데 익숙한을 가져와 빠르고 쉽게 찾고 앱 관련 문제를 해결 하 게 합니다. 하면 디버거에서 코드를 탐색 하는 동안 [앱의 상태를 검사](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) 또는 해당 실행 흐름에 자세히 알아봅니다.  
  
## <a name="start-debugging"></a>디버깅 시작  
 자주 사용 하 여 디버깅 세션을 시작 하기 **F5** (**디버그** / **디버깅 시작**). 이 명령은 디버거가 연결 된 앱을 시작 합니다.  
  
 녹색 화살표 또한 디버거를 시작 합니다 (동일 **F5**).  
  
 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 디버거가 연결 된 앱을 시작할 수는 몇 가지 다른 방법 포함 **F11** ([코드로 단계](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([코드 건너뛰기](#BKMK_Step_over_Step_out)), 또는 사용 하 여 **커서까지 실행**합니다.  이러한 옵션에 수행할 작업에 정보에 대 한이 항목의 다른 섹션을 참조 하세요.  
  
 디버깅할를 노란색 줄 다음에 실행 될 코드를 표시 됩니다.  
  
 ![DBG&#95;Basics&#95;Break&#95;Mode](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 디버깅 하는 동안 같은 명령을 간에 전환할 수 있습니다 **F5**를 **F11** 확인 하려는 코드에 신속 하 게 (예: 중단점)이이 항목에서 설명 하는 다른 기능을 사용 합니다.  
  
 디버거가 일시 중지 된 동안에 지역 창에서 변수 값 보기 또는 조사식 창에서 식을 계산 하는 등 대부분의 디버거 기능을 사용할 수 (라고도 *중단 모드*). 디버거가 일시 중지 하는 경우에 앱 상태 함수, 변수, 하는 동안 일시 중단 되 고 개체가 메모리에 남아 있습니다. 중단 모드에서 요소의 위치와 상태 위반이 나 버그를 확인할 수 있습니다. 일부 프로젝트 유형의 경우에 중단 모드에서 응용 프로그램을 조정할을 만들 수 있습니다.  
  
## <a name="BKMK_Step_into__over__or_out_of_the_code"></a> 한 줄씩 코드를 한 단계씩  
 디버깅 하는 동안 코드 (각 문)의 각 줄에서 중지 하려면 사용 합니다 **F11** 바로 가기 키 (또는 **디버그** / **단계에** 메뉴에서).  
  
> [!TIP]
> 변수를 해당 값을 확인 하거나 마우스로 가리키면 각 코드 줄을 실행 하는 [지역](../debugger/autos-and-locals-windows.md) 및 [조사식](../debugger/autos-and-locals-windows.md) 변경 하는 값을 조사 하려면 windows.  
  
 동작에 대 한 일부 내용은 다음과 같습니다 **단계씩**:  
  
- 중첩된 함수 호출인 경우 **한 단계씩 코드 실행** 명령은 가장 안쪽에 중첩된 함수를 한 단계씩 실행합니다. **와 같은 호출에** 한 단계씩 코드 실행 `Func1(Func2())`을 사용하면 디버거에서 함수 `Func2`를 한 단계씩 실행합니다.  
  
- 실제로 디버거는 실제 줄이 아닌 코드 문을 단계별로 실행합니다. 예를 들어 한 줄에 `if` 절을 작성할 수 있습니다.  
  
  ```csharp  
  int x = 42;  
  string s = "Not answered";  
  if( int x == 42) s = "Answered!";  
  ```  
  
  ```vb  
  Dim x As Integer = 42  
  Dim s As String = "Not answered"  
  If x = 42 Then s = "Answered!"  
  ```  
  
   이 줄을 한 단계씩 실행하면 디버거는 조건을 한 단계로 처리하고 결과를 다른 단계로 처리합니다(이 예에서는 조건이 참임).  
  
  함수를 한 단계씩 실행 하는 동안 호출 스택을 시각적으로 추적을 참조 하세요 [디버깅 하는 동안 호출 스택의 메서드 매핑](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)합니다.  
  
## <a name="BKMK_Step_over_Step_out"></a> 함수를 건너뛰는 중 코드를 단계별로 실행  
 디버거에서 코드를 실행 하는 경우 종종 얻게 될 특정 함수에 어떻게 필요가 없습니다 (신경쓰지 않아도 또는 알고 작동 같은 검증된 라이브러리 코드). 이러한 명령을 사용 하 여 코드를 통해 건너뜁니다 (함수는 계속 실행 되기는 물론 있지만 디버거는 해당 건너뜁니다).  
  
|키보드 명령|메뉴 명령|설명|  
|----------------------|------------------|-----------------|  
|**F10**|**프로시저 단위 실행**|현재 줄에 함수 호출이 포함 되어 있으면 **프로시저 단위 실행** 코드를 실행 한 다음 호출된 된 함수가 반환 후 코드의 첫 번째 줄에서 실행을 일시 중단 합니다.|  
|**Shift+F11**|**프로시저 나가기**|**프로시저 나가기** 계속 코드를 실행 하 고 현재 함수의 경우 (현재 함수를 통해 디버거 건너뜁니다)는 반환 될 때 실행을 일시 중단 합니다.|  
  
> [!TIP]
> 앱의 진입점을 찾을 해야 할 경우 시작 **F10** 하거나 **F11**합니다. 이러한 명령을 앱 상태를 검사 하거나 해당 실행 흐름에 대 한 자세한 내용을 알아보려면 시도 하는 경우에 주로 유용 합니다.  
  
## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> 특정 위치 또는 함수까지 실행  
 종종 코드를 디버깅 하는 기본 방법, 이러한 메서드는 유용 정확 하 게 검사 하 고 원하는 코드를 알고 있는 경우 또는 적어도 디버깅을 시작 하려는 알 수 있습니다.  
  
- **코드에 중단점 설정**  
  
     코드에 간단한 중단점을 설정하려면 Visual Studio 편집기에서 소스 파일을 엽니다. 상황에 맞는 메뉴를 참조 하세요. 선택한 코드 창에서 마우스 오른쪽 단추로 클릭 하 고 실행을 일시 중단 하려는 코드 줄에 커서를 설정한 **중단점 / 중단점 삽입** (누르거나 **F9**). 줄이 실행 되기 전에 디버거가 실행 오른쪽을 일시 중단 합니다.  
  
     ![중단점을 설정](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Visual Studio에서 중단점은 조건부 중단점 및 추적점과 같은 다양한 추가 기능을 제공합니다. 참조 [중단점을 사용 하 여](../debugger/using-breakpoints.md)입니다.  
  
- **커서 위치까지 실행**  
  
     커서 위치까지 실행하려면 소스 창에서 실행 가능한 코드 줄에 커서를 놓습니다. 편집기의 상황에 맞는 메뉴 (편집기에서 마우스 오른쪽 단추로 클릭)에서 선택 **커서까지 실행**합니다. 이 임시 중단점 설정과 유사 합니다.  
  
- **수동으로 코드 중단**  
  
     를 실행 중인 앱에서 코드의 사용 가능한 다음 줄에서 중단 하려면 선택 **디버그**하십시오 **모두 중단** (키보드: **Ctrl + Alt + Break**).  
  
     해당 소스 또는 기호(.pdb) 파일 없이 코드를 실행하는 동안 중단하는 경우 디버거에서 적절한 파일을 찾는 데 도움이 될 수 있는 **소스 파일을 찾을 수 없음** 또는 **기호를 찾을 수 없음** 페이지가 표시됩니다. [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요. 지원 파일에 액세스할 수 없는 경우에도 디스어셈블리 창에서 어셈블리 명령을 디버깅할 수 있습니다.  
  
- **호출 스택에 있는 함수까지 실행**  
  
     에 **호출 스택** 함수를 선택, 마우스 오른쪽 단추로 클릭 및 선택 창 (디버깅 하는 동안 사용 가능), **커서까지 실행**합니다. 호출 스택을 시각적으로 추적을 참조 하세요 [디버깅 하는 동안 호출 스택의 메서드 매핑](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)합니다.  
  
- **이름으로 지정된 함수까지 실행**  
  
     지정된 된 함수에 도달할 때까지 응용 프로그램을 실행 하도록 디버거에 알 수 있습니다. 함수 이름을 지정하거나 호출 스택에서 함수를 선택할 수 있습니다.  
  
     함수 이름을 지정하려면 **디버그**, **새 중단점**, **함수에서 중단**을 선택한 다음 함수의 이름과 기타 식별 정보를 입력합니다.  
  
     ![새 중단점 대화 상자](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     함수가 오버로드되거나 여러 네임스페이스에 있는 경우 **중단점 선택** 대화 상자에서 원하는 함수를 선택할 수 있습니다.  
  
     ![중단점 선택 대화 상자](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
## <a name="BKMK_Set_the_next_statement_to_execute"></a> 실행 흐름 변경에 대 한 포인터를 이동 합니다.  
 디버거가 일시 중지 하는 동안 실행할 코드의 다음 문을 설정 하려면 명령 포인터를 이동할 수 있습니다. 소스 또는 디스어셈블리 창의 여백에 있는 노란색 화살표는 다음에 실행할 문의 위치를 나타냅니다. 코드의 일부를 건너뛰거나 이전에 실행한 줄로 돌아가려면 이 화살표를 이동합니다. 알려진 버그를 포함하는 코드 섹션을 건너뛰려는 경우 등에 이 방법을 사용할 수 있습니다.  
  
 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 다음에 실행할 문을 설정하려면 다음 절차 중 하나를 사용합니다.  
  
- 소스 창에서 노랑 화살표를 같은 소스 파일에서 다음 문을 설정할 위치로 끌어 놓습니다.  
  
- 소스 창에서 다음 실행, 마우스 오른쪽 단추로 클릭 하 고 선택 하려는 줄에 커서를 설정 **다음 문 설정**합니다.  
  
- 디스어셈블리 창에서 다음에 실행할 마우스 오른쪽 단추로 클릭 하려는 어셈블리 명령에 커서를 설정는 선택한 **다음 문 설정**합니다.  
  
> [!CAUTION]
> 다음 문을 설정하면 프로그램 카운터가 새 위치로 바로 이동하게 됩니다. 이 명령은 주의해서 사용해야 합니다.  
> 
> - 기존 실행 위치와 새 실행 위치 사이에서는 명령이 실행되지 않습니다.  
>   - 실행 위치를 뒤로 이동하면 그 사이에서 실행된 명령이 실행 취소되지 않습니다.  
>   - 다음 문을 다른 함수나 범위로 이동하면 호출 스택이 손상되어 런타임 오류나 예외가 발생할 수 있습니다. 다음 문을 다른 범위로 이동하려고 하면 디버거에서 대화 상자가 열리고 여기서 작업을 취소할 수 있습니다. Visual Basic의 경우 다음 문을 다른 범위나 함수로 이동할 수 없습니다.  
>   - 네이티브 C++에서 런타임 검사를 활성화한 경우 다음 문을 설정하면 실행이 메서드의 끝에 도달할 때 예외가 throw될 수 있습니다.  
>   - 편집하며 계속하기를 활성화한 경우 편집하며 계속하기에서 즉시 다시 매핑할 수 없는 종류의 편집을 수행하면 **다음 문 설정** 이 실패합니다. 예를 들어 catch 블록 내의 코드를 편집하면 이 문제가 발생합니다. 이 경우 작업이 지원되지 않음을 알리는 오류 메시지가 나타납니다.  
> 
> [!NOTE]
> 관리 코드의 경우 다음과 같은 조건에서는 다음 문을 이동할 수 없습니다.  
> 
> - 다음 문이 현재 문과 다른 메서드에 있는 경우  
>   - Just-In-Time 디버깅을 사용하여 디버깅을 시작한 경우  
>   - 호출 스택 해제를 진행 중인 경우  
>   - System.StackOverflowException 또는 System.Threading.ThreadAbortException 예외가 throw된 경우  
  
 애플리케이션을 실행하는 동안에는 다음 문을 설정할 수 없습니다. 다음에 실행할 문을 설정하려면 디버거가 중단 모드에 있어야 합니다.  
  
## <a name="step-into-non-user-code"></a>한 단계씩 사용자 코드가 아닌 코드 실행  
 기본적으로 디버거만 앱 코드를 디버깅 하는 동안 이라는 디버거에 의해 결정 되는 수를 표시 하려고 *Just My Code*합니다. (참조 [Just My Code](../debugger/just-my-code.md) 를 다른 프로젝트 형식 및 언어에 대 한 작동 방식 및 동작을 사용자 지정 하는 방법을 참조 하세요.) 그러나를 디버깅 하는 동안에 따라 수 확인 하려는 프레임 워크 코드, 타사 라이브러리 코드 또는 호출의 운영 체제 (시스템 호출).  
  
 내 코드만으로 이동 하 여 해제할 수 있습니다 **도구** / **옵션** / **디버깅** 선택을 취소 하 고는 **내 코드만** 확인란을 선택 합니다.  
  
 내 코드만 해제 하면 디버거는 사용자 코드가 아닌 한 단계씩 실행할 수 및 사용자 코드가 아닌 디버거 창에 나타납니다.  
  
> [!NOTE]
> 디바이스 프로젝트에 대해서는 내 코드만 옵션이 지원되지 않습니다.  
  
 **한 단계씩 시스템 호출 실행**  
  
 시스템 코드에 대 한 디버깅 기호를 로드 한 경우 내 코드만 사용 가능 하지 할 수 있습니다 다른 모든 호출과 마찬가지로 시스템 호출 한 단계씩 실행할 수 있습니다.  
  
 Microsoft 기호 파일에 액세스 하려면 참조 [기호 서버를 사용 하 여 로컬 컴퓨터에 없는 기호 파일을 찾습니다](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) 에 [지정 기호 (.pdb) 및 소스 파일](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) 항목입니다.  
  
 디버깅하는 동안 특정 시스템 구성 요소에 대한 기호를 로드하려면  
  
1. 모듈 창을 엽니다 (키보드: **Ctrl+Alt+U**).  
  
2. 기호를 로드하려는 모듈을 선택합니다.  
  
     **기호 상태** 열을 보면 기호가 로드된 모듈을 확인할 수 있습니다.  
  
3. 상황에 맞는 메뉴에서 **기호 로드** 를 선택합니다.  
  
## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 한 단계씩 관리 코드의 속성 및 연산자 실행  
 기본적으로 디버거는 관리 코드의 속성과 연산자를 건너뜁니다. 대부분의 경우 이렇게 하면 더 나은 디버깅 환경이 제공됩니다. 속성 또는 연산자를 한 단계씩 실행을 사용 하도록 설정 하려면 **디버깅할** / **옵션**합니다. **디버깅** / **일반** 페이지에서 **속성 및 연산자 건너뛰기(관리 전용)** 확인란의 선택을 취소합니다.
