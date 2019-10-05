---
title: '오류: 대상 프로세스 종료 코드를 사용 하 여 &#39;코드&#39; 함수를 계산 하는 동안 &#39;함수&#39; | Microsoft Docs'
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75d82b6011a0dfa7f2c388e7d5f39a9ebabcd663
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850814"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>오류: 대상 프로세스 종료 코드를 사용 하 여 &#39;코드&#39; 함수를 계산 하는 동안 &#39;함수&#39;

전체 메시지 텍스트: 'Function' 함수를 평가 하는 동안 ' code '코드를 사용 하 여 대상 프로세스가 종료 되었습니다.

디버거에서.NET 개체의 상태를 검사 좀 더 쉽게 추가 코드를 실행 하는 디버깅된 프로세스를 강제로 자동으로 됩니다 (일반적으로 속성 getter 메서드 및 `ToString` 함수). 대부분의 시나리오에서 이러한 함수는 성공적으로 완료 또는 디버거에 의해 발생 될 수 있는 예외를 throw 합니다. 그러나는 예외가 없습니다 포착 커널 경계를 넘나들, 사용자 메시지 펌프를 요구 하거나는 복구할 수 있으므로 몇 가지 경우가 있습니다. 결과, 속성 getter 또는 코드를 실행 하는 ToString 메서드 중 하나는 명시적으로 프로세스를 종료 합니다 (예를 들어, 호출 `ExitProcess()`) 수 없습니다는 처리 되지 않은 예외를 throw 하거나 (예를 들어 `StackOverflowException`) 종료 됩니다는 디버깅된 프로세스를 디버그 세션을 종료 합니다. 이 오류 메시지에서 발견 되 면이 발생 했습니다.

이 문제에 대 한 일반적인 이유는 디버거가 자신을 호출 하는 속성으로 계산 되는 경우 스택 오버플로 예외가 발생할 수 있습니다이입니다. 스택 오버플로 예외를 복구할 수 없습니다 하 고 대상 프로세스가 종료 됩니다.

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

이 문제에 대 한 두 가지 방법이 있습니다.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>해결 방법 #1: ToString 메서드나 속성 getter 호출에서 디버거를 방지 

오류 메시지에는 디버거를 호출 하려고 하는 함수의 이름을 알려줍니다. 함수 이름을 사용 하 여 연습할 수에서 해당 함수를 다시 평가 합니다 **직접 실행** 창을 평가 디버그 합니다. 디버깅은에서 평가할 때 가능한를 **직접 실행** 창 이므로 암시적 평가를 달리를 **자동/지역/조사식** windows 디버거 처리 되지 않은 예외에서 중단 합니다.

이 함수를 수정할 수 있는 경우 속성 getter 호출에서 디버거를 방지할 수 있습니다 또는 `ToString` 메서드. 다음 중 하나를 시도 합니다.

* 메서드는 속성 getter 외에도 코드의 다른 유형으로 변경 하거나 ToString 메서드 및 문제가 사라집니다.
    또는
* (에 대 한 `ToString`) 정의 된 `DebuggerDisplay` 형식에 속성에 있는 것 이외의 평가 디버거 `ToString`합니다.
    또는
* (예: 속성 getter) 배치는 `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` 속성에는 특성입니다. 이 API 호환성을 위해 속성을 유지 해야 하는 메서드가 있는 경우에 유용할 수 있습니다 하지만 실제로 메서드 여야 합니다.

이 메서드를 수정할 수 없는 경우 대체 명령에 대상 프로세스를 중단 및 평가 다시 시도 수 있습니다.

### <a name="solution-2-disable-all-implicit-evaluation"></a>해결 방법 2: 모든 암시적 평가 사용 하지 않도록 설정

이전 해결 방법이 문제를 해결 하지 하는 경우 이동할 **도구** > **옵션**, 설정의 선택을 취소 **디버깅**  >   **일반적인** > **속성 확인 및 기타 암시적 함수 호출**합니다. 대부분의 암시적 함수 실행이 비활성화 됩니다 하 고 문제를 해결 해야 합니다.
