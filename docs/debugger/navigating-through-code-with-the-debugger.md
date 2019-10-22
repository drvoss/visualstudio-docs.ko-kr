---
title: 디버거를 사용 하 여 코드 탐색 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/12/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e07e2612e01453115cf4cd6120d92bfd5b0168bd
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "70222646"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Visual Studio 디버거를 사용 하 여 코드 탐색

Visual Studio 디버거는 코드를 탐색 하 여 앱의 상태를 검사 하 고 실행 흐름을 표시 하는 데 도움이 될 수 있습니다. 바로 가기 키, 디버그 명령, 중단점 및 기타 기능을 사용 하 여 검사 하려는 코드를 신속 하 게 가져올 수 있습니다. 디버거 탐색 명령 및 바로 가기를 사용 하면 앱 문제를 보다 쉽고 빠르게 찾고 해결할 수 있습니다.  처음으로 코드를 디버깅 하는 경우이 문서를 진행 하기 전에 절대 초보자와 [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md) [에 대 한 디버깅](../debugger/debugging-absolute-beginners.md) 을 읽어야 할 수 있습니다.

## <a name="basic-debugging"></a>기본적인 디버깅

디버거를 연결 하 여 응용 프로그램을 시작 하려면 **f5**키를 누르거나 **디버그**  > **디버깅 시작**을 선택 하거나 Visual Studio 도구 모음에서 녹색 화살표를 선택 합니다.

 ![DBG&#95;기본&#95;사항&#95;디버깅 시작](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")

디버깅 하는 동안 노란색 강조 표시는 다음에 실행 되는 코드 줄을 보여 줍니다.

 ![DBG&#95;기본&#95;중단&#95;모드](../debugger/media/dbg_basics_break_mode.png "중단 모드")

**모듈** 및 **조사식** 창과 같은 대부분의 디버거 창은 디버거가 실행 되는 동안에만 사용할 수 있습니다. **지역** 창에서 변수 값 보기 또는 **조사식** 창에서 식 계산과 같은 일부 디버거 기능은 디버거가 중단점에서 일시 중지 된 경우에만 사용할 수 있습니다 ( *중단 모드*라고도 함).

중단 모드에서 함수, 변수 및 개체가 메모리에 유지 되는 동안에는 앱 실행이 일시 중단 됩니다. 요소의 위치 및 상태를 검사 하 여 위반 또는 버그를 찾을 수 있습니다. 일부 프로젝트 형식의 경우 중단 모드에서 응용 프로그램을 조정할 수도 있습니다. 이러한 기능을 보여 주는 비디오는 [디버거 시작](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6)을 참조 하세요.

소스 또는 기호 ( *.pdb*) 파일이 로드 되지 않은 코드를 중단 하는 경우 디버거는 파일을 찾아 로드 하는 데 도움이 될 수 있는 **소스 파일을 찾을** 수 없음 또는 **기호를 찾을** 수 없음 페이지를 표시 합니다. [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요. 기호 또는 소스 파일을 로드할 수 없는 경우에도 **디스어셈블리** 창에서 어셈블리 명령을 디버그할 수 있습니다.

응용 프로그램을 처음부터 시작 하 여 항상 디버깅을 시작할 필요는 없습니다. **F11** 키를 눌러 코드를 한 단계씩 코드 실행 하거나 **, F10** 키를 눌러 [코드를 프로시저](#BKMK_Step_over_Step_out) [단위로](#BKMK_Step_into__over__or_out_of_the_code)실행 하거나, [특정 위치나 함수까지 실행할](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)수도 있습니다.

## <a name="step-through-code"></a>단계별 코드 실행

디버거 단계 명령은 앱 상태를 검사 하거나 실행 흐름에 대 한 자세한 정보를 확인 하는 데 도움이 됩니다.

앱에서 진입점을 찾아야 하는 경우 **F10** 또는 **F11**키를 사용 하 여 시작 합니다.

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a>한 줄씩 코드 한 단계씩 코드 실행

디버깅 하는 동안 코드 또는 문의 각 줄에서 중지 하려면 **디버그**  >  한**단계씩 코드 실행**을 사용 하거나 **F11**키를 누릅니다.

디버거는 실제 줄이 아닌 코드 문을 단계별로 진행 합니다. 예를 들어 한 줄에 `if` 절을 작성할 수 있습니다.

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

그러나이 줄을 한 단계씩 실행 하면 디버거는 조건을 한 단계로 처리 하 고 그 결과를 다른 단계로 처리 합니다. 위의 예제에서 조건은 true입니다.

중첩된 함수 호출인 경우 **한 단계씩 코드 실행** 명령은 가장 안쪽에 중첩된 함수를 한 단계씩 실행합니다. 예를 들어 `Func1(Func2())`와 같은 호출에 한 **단계씩 코드 실행** 을 사용 하는 경우 디버거는 `Func2` 함수를 단계별로 실행 합니다.

>[!TIP]
>각 코드 줄을 실행 하면 변수 위로 마우스를 이동 하 여 값을 확인 하거나 [지역](autos-and-locals-windows.md) 및 [조사식](watch-and-quickwatch-windows.md) 창을 사용 하 여 값 변경 내용을 볼 수 있습니다. 함수를 한 단계씩 실행 하는 동안 호출 스택을 시각적으로 추적할 수도 있습니다. [디버깅 하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)를 참조 하세요.

### <a name="BKMK_Step_over_Step_out"></a>코드를 단계별로 실행 하 고 일부 함수 건너뛰기

디버깅 하는 동안 함수를 고려 하지 않거나 잘 테스트 된 라이브러리 코드와 같이 작동 하는 것을 알 수 있습니다. 다음 명령을 사용 하 여 코드를 건너뛸 수 있습니다. 함수는 계속 실행 되지만 디버거는 해당 함수를 건너뜁니다.

|키보드 명령|디버그 메뉴 명령|설명|
|----------------------|------------------|-----------------|
|**F10**|**프로시저 단위 실행**|현재 줄에 함수 호출이 포함 된 경우 **프로시저 단위** 실행은 코드를 실행 한 다음 호출 된 함수가 반환 된 후 코드의 첫 번째 줄에서 실행을 일시 중단 합니다.|
|**Shift**+**F11**|**프로시저 나가기**|**프로시저** 실행 코드를 계속 실행 하 고 현재 함수가 반환 될 때 실행을 일시 중단 합니다. 디버거가 현재 함수를 건너뜁니다.|

## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>특정 위치 또는 함수까지 실행

검사 하려는 코드를 정확 하 게 알고 있거나 디버깅을 시작할 위치를 알고 있는 경우 특정 위치 또는 함수에 직접 실행 하는 것이 좋습니다.

### <a name="run-to-a-breakpoint-in-code"></a>코드의 중단점까지 실행

코드에 간단한 중단점을 설정 하려면 실행을 일시 중단 하려는 코드 줄 옆에 있는 맨 왼쪽 여백을 클릭 합니다. 줄을 선택 하 고 **F9**키를 누르거나, **디버그**  > **중단점 설정/해제**를 선택 하거나, 마우스 오른쪽 단추를 클릭 하 고 중단점  >  중단점을 선택 하 여 선택할 수도 있습니다. 중단점은 코드 줄 옆의 왼쪽 여백에 빨간색 점으로 표시 됩니다. 디버거는 줄이 실행 되기 직전에 실행을 일시 중단 합니다.

![중단점 설정](../debugger/media/dbg_basics_setbreakpoint.png "중단점 설정")

Visual Studio에서 중단점은 조건부 중단점 및 추적점과 같은 다양한 추가 기능을 제공합니다. 자세한 내용은 [중단점 사용](../debugger/using-breakpoints.md)을 참조 하세요.

### <a name="run-to-a-function-breakpoint"></a>함수 중단점까지 실행

지정 된 함수에 도달할 때까지 실행 되도록 디버거에 지시할 수 있습니다. 함수 이름을 지정하거나 호출 스택에서 함수를 선택할 수 있습니다.

**이름으로 함수 중단점을 지정 하려면**

1. **디버그**  > **새 중단점**  > **함수 중단점** 을 선택 합니다.

1. **새 함수 중단점** 대화 상자에서 함수 이름을 입력 하 고 언어를 선택 합니다.

   ![새 함수 중단점 대화 상자](../debugger/media/dbg_execution_newbreakpoint.png "새 함수 중단점")

1. **확인**을 선택합니다.

함수가 오버 로드 되거나 둘 이상의 네임 스페이스에 있는 경우 **중단점** 창에서 원하는 항목을 선택할 수 있습니다.

![오버 로드 된 함수 중단점](../debugger/media/dbg_execution_overloadedbreakpoints.png "오버 로드 된 함수 중단점")

**호출 스택에서 함수 중단점을 선택 하려면**

1. 디버깅 하는 동안 **디버그**  > **Windows**  > **호출 스택**을 선택 하 여 **호출 스택** 창을 엽니다.

1. **호출 스택** 창에서 함수를 마우스 오른쪽 단추로 클릭 하 고 **커서까지 실행**을 선택 하거나 **ctrl** +**F10**키를 누릅니다.

호출 스택을 시각적으로 추적 하려면 [디버그 하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)를 참조 하세요.

### <a name="run-to-a-cursor-location"></a>커서 위치까지 실행

커서 위치까지 실행 하려면 소스 코드 또는 **호출 스택** 창에서 중단 하려는 줄을 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **커서까지 실행**을 선택 하거나 **ctrl** +**F10**키를 누릅니다. **커서까지 실행** 을 선택 하는 것은 임시 중단점 설정과 유사 합니다.

### <a name="run-to-click"></a>실행하려면 클릭

디버거에서 일시 중지 된 상태에서 소스 코드 또는 **디스어셈블리** 창에서 문을 마우스로 가리키고 **여기로 실행 실행** 녹색 화살표 아이콘을 선택할 수 있습니다. **실행을 클릭** 하 여 클릭 하면 임시 중단점을 설정 하지 않아도 됩니다.

![실행 하려면 클릭](../debugger/media/dbg-run-to-click.png "실행하려면 클릭")

> [!NOTE]
> **실행 하려면 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]을 시작 하 여 클릭** 합니다.

### <a name="manually-break-into-code"></a>수동으로 코드 중단

실행 중인 앱에서 사용 가능한 다음 코드 줄에서 중단 하려면 **디버그**  > **모두 중단**을 선택 하거나 **ctrl** +**alt** +**break**를 누릅니다.

## <a name="BKMK_Set_the_next_statement_to_execute"></a>포인터를 이동 하 여 실행 흐름 변경

디버거가 일시 중지 된 동안 소스 코드 또는 **디스어셈블리** 창의 여백에 있는 노란색 화살표는 실행할 다음 문의 위치를 표시 합니다. 이 화살표를 이동 하 여 다음 문을 실행 하도록 변경할 수 있습니다. 코드의 일부를 건너뛰거나 이전 줄로 돌아갈 수 있습니다. 포인터를 이동 하는 것은 알려진 버그를 포함 하는 코드 섹션을 건너뛰는 경우 등에 유용 합니다.

 ![포인터를 이동 합니다.](../debugger/media/dbg_basics_example3.gif "포인터를 이동 합니다.")

다음 문을 실행 하도록 변경 하려면 디버거가 중단 모드에 있어야 합니다. 소스 코드 또는 **디스어셈블리** 창에서 노란색 화살표를 다른 줄로 끌거나 다음에 실행할 줄을 마우스 오른쪽 단추로 클릭 하 고 **다음 문 설정**을 선택 합니다.

프로그램 카운터가 새 위치로 바로 이동 하 고 이전 실행 지점과 새 실행 위치 간의 명령이 실행 되지 않습니다. 그러나 실행 지점을 뒤로 이동 하는 경우에는 중간의 명령이 실행 취소 되지 않습니다.

>[!CAUTION]
>- 다음 문을 다른 함수나 범위로 이동하면 호출 스택이 손상되어 런타임 오류나 예외가 발생할 수 있습니다. 다음 문을 다른 범위로 이동하려고 하면 디버거에서 대화 상자가 열리고 여기서 작업을 취소할 수 있습니다.
>- Visual Basic의 경우 다음 문을 다른 범위나 함수로 이동할 수 없습니다.
>- 네이티브 C++에서 런타임 검사를 활성화한 경우 다음 문을 설정하면 실행이 메서드의 끝에 도달할 때 예외가 throw될 수 있습니다.
>- 편집하며 계속하기를 활성화한 경우 편집하며 계속하기에서 즉시 다시 매핑할 수 없는 종류의 편집을 수행하면 **다음 문 설정** 이 실패합니다. 예를 들어 catch 블록 내의 코드를 편집하면 이 문제가 발생합니다. 이 경우 작업이 지원 되지 않음을 알리는 오류 메시지가 표시 됩니다.
>- 관리 코드에서는 다음을 수행 하는 경우 다음 문을 이동할 수 없습니다.
>   - 다음 문이 현재 문과 다른 메서드에 있는 경우
>   - Just-in-time 디버깅을 통해 디버깅이 시작 되었습니다.
>   - 호출 스택 해제가 진행 중입니다.
>   - System.StackOverflowException 또는 System.Threading.ThreadAbortException 예외가 throw된 경우

## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>사용자가 아닌 코드 디버그

기본적으로 디버거는 *내 코드만*이라는 설정을 사용 하도록 설정 하 여 앱 코드만 디버깅 하려고 합니다. 이 기능이 다양 한 프로젝트 형식 및 언어에 대해 작동 하는 방법 및 사용자 지정할 수 있는 방법에 대 한 자세한 내용은 [내 코드만](../debugger/just-my-code.md)을 참조 하세요.

디버깅 하는 동안 프레임 워크 코드, 타사 라이브러리 코드 또는 시스템 호출을 보려면 내 코드만를 사용 하지 않도록 설정할 수 있습니다. **도구** (또는 **디버그**) > **옵션**  > **디버깅**에서 **내 코드만 사용** 확인란의 선택을 취소 합니다. 내 코드만 사용 하지 않도록 설정 된 경우 디버거 창에 사용자 코드가 아닌 코드가 표시 되 고 디버거가 사용자가 아닌 코드를 한 단계씩 코드 실행 할 수 있습니다.

> [!NOTE]
> 디바이스 프로젝트에 대해서는 내 코드만 옵션이 지원되지 않습니다.

### <a name="debug-system-code"></a>시스템 코드 디버그

Microsoft 시스템 코드에 대 한 디버깅 기호를 로드 하 고 내 코드만를 비활성화 한 경우 다른 호출과 마찬가지로 시스템 호출을 한 단계씩 실행 할 수 있습니다.

Microsoft 기호를 로드 하려면 [기호 위치 구성 및 옵션 로드](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options)를 참조 하세요.

**특정 시스템 구성 요소에 대 한 기호를 로드 하려면:**

1. 디버깅 하는 동안**Windows**  > **모듈** **디버그**  >  선택 하거나 **Ctrl** +**Alt** +**U**를 눌러 **모듈** 창을 엽니다.

1. **모듈** 창에서 기호 **상태** 열에 기호가 로드 된 모듈을 확인할 수 있습니다. 기호를 로드 하려는 모듈을 마우스 오른쪽 단추로 클릭 하 고 **기호 로드**를 선택 합니다.

## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 한 단계씩 관리 코드의 속성 및 연산자 실행
 기본적으로 디버거는 관리 코드의 속성과 연산자를 건너뜁니다. 대부분의 경우 이렇게 하면 더 나은 디버깅 환경이 제공됩니다. 속성 또는 연산자를 한 단계씩 실행 하려면 **디버그**  > **옵션**을 선택 합니다. **디버깅** > **일반** 페이지에서 **속성 및 연산자 건너뛰기(관리 전용)** 확인란의 선택을 취소합니다.

## <a name="see-also"></a>참조
- [디버깅이란?](../debugger/what-is-debugging.md)
- [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
- [먼저 디버깅 살펴보기](../debugger/debugger-feature-tour.md)
