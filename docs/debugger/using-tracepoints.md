---
title: 디버거에서 추적점 사용 | Microsoft Docs
ms.date: 9/4/2019
ms.topic: conceptual
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: fe9d96290474283164ed9761a0cb9aa7734f1a9d
ms.sourcegitcommit: 2db01751deeee7b2bdb1db25419ea6706e6fcdf8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71069033"
---
# <a name="use-tracepoints-in-the-visual-studio-debugger"></a>Visual Studio 디버거에서 추적점 사용

추적점을 사용 하면 코드를 수정 하거나 중지 하지 않고 구성 가능한 조건에서 출력 창에 정보를 기록할 수 있습니다. 이 기능은 관리 되는 코드와 네이티브 코드 뿐 아니라 JavaScript 및 C#와 같은 여러 언어에 대해서도 지원 됩니다.

## <a name="let39s-take-an-example"></a>&#39;예제를 사용 합니다.

다음 예제 프로그램은 루프에서 다른 `for` 반복을 실행할 때마다 1 씩 늘리는 카운터 변수를 사용 하는 간단한 루프입니다.

![카운터 예제](../debugger/media/counterexample.png "카운터 예제")

## <a name="set-tracepoints-in-source-code"></a>소스 코드에서 추적점 설정

**중단점 설정** 창의 **작업** 확인란 아래에 출력 문자열을 지정 하 여 추적점을 설정할 수 있습니다.

1. 추적점을 초기화 하려면 먼저 추적점을 설정 하려는 줄 번호의 왼쪽 여백을 클릭 합니다.

   ![중단점 초기화](../debugger/media/breakpointinitialization.png "중단점 초기화")

2. 빨간색 원을 마우스로 가리킨 다음 기어 아이콘을 클릭 합니다.
3. 그러면 **중단점 설정** 창이 열립니다.

   ![중단점 창](../debugger/media/breakpointwindow.png "중단점 창")

4. **작업** 확인란을 선택 합니다.

   ![선택 된 작업 상자](../debugger/media/checkedactionsbox.png "선택 된 작업 상자")

   빨간색 원이 다이아몬드로 변경 되어 중단점에서 추적점로 전환 되었음을 알 수 있습니다.

5. 출력 창 텍스트 상자 **에** 로그인 할 메시지를 입력 합니다. 자세한 내용은이 문서의 뒷부분에 나오는 섹션을 참조 하십시오.

   이제 추적점이 설정 됩니다. 모든 정보를&quot; 출력 창에 기록 하려면 닫기단추를누릅니다.&quot;

6. 메시지가 표시 되는지 여부를 결정 하는 조건을 추가 하려면 **조건** 확인란을 선택 합니다.

   ![선택 된 조건 상자](../debugger/media/checkedconditionsbox.png "선택 된 조건 상자")

   조건에 대 한 세 가지 선택 사항이 있습니다. **조건식**, **필터**및 **적중 횟수를 계산**합니다.

## <a name="actions-menu"></a>작업 메뉴

이 메뉴를 사용 하 여 출력 창에 메시지를 기록할 수 있습니다. 메시지 상자에 출력 하려는 문자열을 입력 합니다 (따옴표 필요 없음). 변수의 값을 표시 하려면 중괄호 안에 포함 해야 합니다.

예를 들어 출력 콘솔에 `counter` 변수 값을 표시 하려면 메시지 텍스트 상자에 {counter}를 입력 합니다.

![카운터 출력 메시지](../debugger/media/counteroutputmessage.png "카운터 출력 메시지")

**닫기** 를 클릭 한 다음 프로그램 디버그 (**F5**)를 클릭 하면 출력 창에 다음 출력이 표시 됩니다.

![출력 창의 동작 메시지](../debugger/media/actionsmessageinoutputwindow.png "출력 창의 동작 메시지")

특수 키워드를 사용 하 여 보다 구체적인 정보를 표시할 수도 있습니다. 아래 표시 된 대로 키워드를 정확 하 게 입력 합니다. 각 키워드 앞에 "$"를 사용 하 고 키워드 자체에 대해 모든 대문자를 사용 합니다.

| 키워드 | 표시 되는 내용 |
| --- | --- |
| $ADDRESS | 현재 명령 |
| $CALLER | 호출 함수 이름 |
| $CALLSTACK | 호출 스택 |
| $FUNCTION | 현재 함수 이름 |
| $PID | 프로세스 ID |
| $PNAME | 프로세스 이름 |
| $TID | 스레드 ID |
| $TNAME   | 스레드 이름 |
| $TICK | 틱 수 (Windows GetTickCount) |

## <a name="conditions-menu"></a>조건 메뉴

조건을 사용 하 여 출력 메시지를 필터링 할 수 있으므로 특정 시나리오에만 표시 됩니다. 사용할 수 있는 세 가지 종류의 조건이 있습니다.

### <a name="conditional-expression"></a>조건식
조건 식의 경우 출력 메시지는 특정 조건이 충족 될 때만 표시 됩니다.

조건 식의 경우 특정 조건이 true 이거나 변경 된 경우에 메시지를 출력 하도록 추적점을 설정할 수 있습니다. 예를 들어 `for` 루프를 계속 반복 하는 동안 counter 값만 표시 하려면 **true** 옵션을 선택한 다음 메시지 텍스트 상자에을 입력 `i%2 == 0` 합니다.

![조건식이 True 임](../debugger/media/conditionalexpressionistrue.png "조건식이 True 임")

`for` 루프 반복이 변경 될 때 counter 값을 인쇄 하려면 **변경 된 경우** 옵션을 선택 하 고 메시지 텍스트 상자에을 `i` 입력 합니다.

![변경 된 조건 식](../debugger/media/conditionalexpressionwhenchanged.png "변경 된 조건 식")


**변경 시** 옵션의 동작은 프로그래밍 언어 마다 다릅니다.

- 네이티브 코드의 경우 디버거는 조건의 첫 번째 계산을 변경으로 간주 하지 않으므로 첫 번째 계산에서 추적점을 적중 하지 않습니다.
- 관리 코드의 경우 **변경 된 경우** 디버거는 첫 번째 평가에서 추적점을 적중 합니다.

조건을 설정 하는 동안 사용할 수 있는 유효한 식에 대 한 자세한 내용은 [디버거의 식](expressions-in-the-debugger.md) 을 참조 하세요.

### <a name="hit-count"></a>적중 횟수
적중 횟수 조건을 통해 추적점이 설정 된 코드 줄이 지정 된 횟수 만큼 실행 된 후에만 출력을 보낼 수 있습니다.

적중 횟수에 대해 추적점이 설정 된 코드 줄이와 같거나,의 배수 이거나, 지정 된 적중 횟수 값 보다 크거나 같은 경우 메시지를 출력 하도록 선택할 수 있습니다. 요구 사항에 가장 적합 한 옵션을 선택 하 고 해당 반복을 나타내는 정수 값을 필드에 입력 합니다 (예: 5).

![조건식 적중 횟수](../debugger/media/conditionalexpressionhitcount.png "조건식 적중 횟수")

### <a name="filter"></a>Filter
필터 조건의 경우 표시 되는 장치, 프로세스 또는 스레드 출력을 지정 합니다.

![조건식 필터](../debugger/media/conditionalexpressionfilter.png "조건식 필터")

필터 식 목록:

- MachineName = "이름"
- ProcessId = 값
- ProcessName = "이름"
- ThreadId = 값
- ThreadName = "이름"

문자열 (예: 이름)을 큰따옴표로 묶습니다. 따옴표 없이 값을 입력할 수 있습니다. `&` (),`OR`()`NOT`, ()및괄호를사용하여절을조합할수있습니다.`!` `||` `AND`

## <a name="considerations"></a>고려 사항

추적점은 더 깔끔하고 부드러운 환경을 디버깅 하기 위한 것 이지만, 사용할 때 알아야 할 몇 가지 고려 사항이 있습니다.

경우에 따라 개체의 속성이 나 특성을 검사 하면 해당 값이 변경 될 수 있습니다. 이는 추적점 기능 자체에 의해 발생 하는 버그가 아니지만 추적점을 사용 하 여 개체를 검사 해도 이러한 실수로 인 한 수정이 발생 하지 않도록 하는 것이 좋습니다.

**작업** 메시지 상자에서 식이 계산 되는 방식은 현재 개발에 사용 하 고 있는 언어와 다를 수 있습니다. 예를 들어 문자열을 출력 하기 위해 일반적으로 또는 `Debug.WriteLine()` `console.log()`를 사용 하는 경우에도 메시지를 따옴표로 둘러쌀 필요가 없습니다. 또한 식 출력에 대 한 중괄호`{ }`구문 ()은 개발 언어에서 값을 출력 하는 규칙과 다를 수 있습니다. 그러나 중괄호 (`{ }`) 안에 있는 콘텐츠는 여전히 개발 언어의 구문을 사용 하 여 작성 해야 합니다.
