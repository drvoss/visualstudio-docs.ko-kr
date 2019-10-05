---
title: 디버거에서 스레드를 보는 | Microsoft Docs
ms.date: 10/29/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f65bd7a904f30f132f654b6dd718532d9d0e66e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821585"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window-c-visual-basic-c"></a>스레드 창을 사용 하 여 Visual Studio 디버거에서 스레드 보기 (C#, Visual Basic의 경우 C++)
에 **스레드** 창을 검토 하 고 수 디버그 중인 응용 프로그램에서 스레드를 사용 하 여 작동 합니다. 사용 하는 방법에 대 한 단계별 지침에 대 한 합니다 **스레드** 창 참조 [연습: 스레드 창을 사용 하 여 디버그](../debugger/how-to-use-the-threads-window.md)합니다.

## <a name="use-the-threads-window"></a>스레드 창 사용
 합니다 **스레드** 창에 있는 각 행에 응용 프로그램에서 별도 스레드에서 테이블이 있습니다. 기본적으로 이 테이블에는 애플리케이션의 모든 스레드가 나열되지만 목록을 필터링하여 관심 있는 스레드만 표시할 수 있습니다. 각 열에는 다양 한 유형의 정보를 설명합니다. 일부 열을 숨길 수도 있습니다. 모든 열을 표시 하면 왼쪽에서 오른쪽으로 다음과 같은 열 표시:

- **플래그**: 이 레이블이 지정 되지 않은 열에서 특별히 주의 하려는 스레드를 표시할 수 있습니다. 스레드에 플래그를 설정 하는 방법에 대 한 정보를 참조 하세요. [방법: 플래그 지정 및 스레드의](../debugger/how-to-flag-and-unflag-threads.md)합니다.

- **현재 스레드의**: 이 레이블이 지정 되지 않은 열 노란색 화살표는 현재 스레드를 나타냅니다. 화살표 개요-현재 스레드에 대 한 현재 디버거 컨텍스트를 나타냅니다.

- **ID**: 각 스레드에 대 한 id 번호를 표시합니다.

- **관리 되는 ID**: 관리 되는 스레드의 관리 식별 번호가 표시 됩니다.

- **범주**: 사용자 인터페이스 스레드, 원격 프로시저 호출 처리기 또는 작업자 스레드로 스레드가의 범주를 표시합니다. 특정 범주는 애플리케이션의 주 스레드를 식별합니다.

- **이름**: 있는 경우 또는 이름으로 각 스레드를 식별 \<이름 없음 >.

- **위치**: 스레드가 실행 되 고 있는 보여 줍니다. 이 위치를 확장하여 스레드의 전체 호출 스택을 표시할 수 있습니다.

- **우선 순위**: (기본적으로 숨김) 고급 열을 표시 하는 시스템에서 각 스레드에 할당 하는 우선 순위가 있습니다.

- **선호도 마스크**: 각 스레드에 대 한 프로세서 선호도 마스크를 보여 주는 고급 열 (기본적으로 숨김). 다중 프로세서 시스템에서는 선호도 마스크에 따라 스레드가 실행될 수 있는 프로세서가 결정됩니다.

- **일시 중단 횟수**: 고급 열 (기본적으로 숨김) 일시 중단된 횟수를 표시 하는 합니다. 이 횟수에 따라 스레드를 실행할 수 있는지 여부가 결정됩니다. 일시 중단 된 횟수에 대 한 자세한 내용은 참조 하세요. [동결 및 재개 스레드](#freeze-and-thaw-threads)합니다.

- **프로세스 이름**: 각 스레드가 속하는 프로세스가 표시 됩니다 (기본적으로 숨김) 고급 열입니다. 이 열의 데이터를에서 여러 프로세스를 디버깅할 때 유용할 수 있습니다.

- **프로세스 ID**: 각 스레드가 속하는 프로세스 ID를 표시 하는 고급 열 (기본적으로 숨김).

- **전송 한정자**: 고급 열 (기본적으로 숨김) 고유 하 게 디버거를 연결할 컴퓨터를 식별 합니다.

### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>중단 모드나 실행 모드에서 스레드 창을 표시하려면

- Visual Studio 디버그 모드일 때 선택 된 **디버그** 메뉴에서 **Windows**를 선택한 후 **스레드**합니다.

### <a name="to-display-or-hide-a-column"></a>열을 표시하거나 숨기려면

- 맨 위에 있는 도구 모음에는 **스레드** 창에서 **열**합니다. 그런 다음 선택 하거나 열을 표시 하거나 숨기려면 이름의 선택을 취소 합니다.

## <a name="display-flagged-threads"></a>플래그가 지정 된 스레드 표시
 **스레드** 창에서 아이콘으로 스레드를 표시하여 특별한 주의가 필요한 스레드에 플래그를 설정할 수 있습니다. 자세한 내용은 [방법: 스레드에 플래그 지정 및 스레드의 플래그 해제](../debugger/how-to-flag-and-unflag-threads.md)를 참조하세요. **스레드** 창에서 모든 스레드를 표시하거나 플래그가 지정된 스레드만 표시하도록 선택할 수 있습니다.

### <a name="to-display-only-flagged-threads"></a>플래그가 지정된 스레드만 표시하려면

- 선택 **스레드 스레드만 표시** 맨 위에 있는 도구 모음에는 **스레드** 창입니다. (흐리게 표시 되 면 해야 먼저 일부 스레드에 플래그를 설정 합니다.)

## <a name="freeze-and-thaw-threads"></a>중지 하 고 스레드 재개
 스레드를 중지 하는 경우에 시스템 리소스가 사용 가능한 경우에 스레드 실행에 시작 되지 않습니다.

 네이티브 코드에서 일시 중단 하거나 Windows 함수를 호출 하 여 스레드를 다시 시작할 수 있습니다 `SuspendThread` 고 `ResumeThread`입니다. MFC 함수를 호출 하거나 [CWinThread::SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) 하 고 [cwinthread:: Resumethread](/cpp/mfc/reference/CWinThread-class#resumethread)합니다. 호출 하는 경우 `SuspendThread` 또는 `ResumeThread`의 *일시 중단 횟수* 나오는 합니다 **스레드** 창이 변경 됩니다. 중지 하거나 재개 네이티브 스레드 일시 중단 된 횟수가 변경 되지 않습니다. 스레드 재개 되 고 일시 중단 된 횟수가 0 경우가 아니면 네이티브 코드에서 실행할 수 없습니다.

 관리 코드에서 일시 중단된 횟수 변경 하거나 스레드 재개 합니다. 관리 코드에서 스레드를 중지 하면 일시 중단 된 개수는 1입니다. 네이티브 코드에서 스레드를 중지 하면 해당 일시 중단 된 횟수가 0을 사용 하지 않은 경우는 `SuspendThread` 호출 합니다.

> [!NOTE]
> 네이티브 코드에서 관리 코드로의 호출을 디버깅할 때 관리 코드는 이를 호출한 네이티브 코드와 동일한 실제 스레드에서 실행됩니다. 네이티브 스레드를 일시 중단하거나 중지하면 관리 코드도 중지됩니다.

### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>스레드 실행을 중지하거나 재개하려면

- 맨 위에 있는 도구 모음에는 **스레드** 창에서 **스레드 중지** 또는 **스레드 재개**합니다.

     이 동작은 **스레드** 창에서 선택되는 스레드에만 적용됩니다.

### <a name="switch-to-another-thread"></a>다른 스레드로 전환

노란색 화살표는 현재 스레드 (및 실행 포인터의 위치)를 나타냅니다. 끝이 굽은 녹색 화살표가 현재 디버거 컨텍스트가 아닌 현재 스레드를 나타냅니다.

#### <a name="to-switch-to-another-thread"></a>다른 스레드로 전환

- 다음 단계 중 하나를 수행 합니다.

  - 스레드를 두 번 클릭합니다.

  - 스레드를 마우스 오른쪽 단추로 클릭 **스위치를 스레드**합니다.

## <a name="group-and-sort-threads"></a>그룹 및 정렬 스레드
 스레드를 그룹화하면 테이블에 각 그룹의 제목이 나타납니다. 제목에는 **작업자 스레드** 또는 **플래그가 해제된 스레드** 등의 그룹 설명과 트리 컨트롤이 포함됩니다. 각 그룹의 멤버 스레드가 그룹 제목 아래에 나타납니다. 그룹에 대 한 멤버 스레드를 숨기려는 경우 트리 컨트롤을 사용 하 여 그룹을 축소 합니다.

 그룹화가 정렬보다 우선하기 때문에 예를 들어 스레드를 범주별로 그룹화한 다음 각 범주 내의 ID로 정렬할 수 있습니다.

### <a name="to-sort-threads"></a>스레드를 정렬하려면

1. 맨 위에 있는 도구 모음에는 **스레드** 창 열의 맨 위에 있는 단추를 선택 합니다.

     이제 해당 열의 값으로 스레드가 정렬됩니다.

2. 정렬 순서를 반대로 하려면 같은 단추를 다시 선택 합니다.

     목록 맨 위에 나타난 스레드가 이제 맨 아래에 나타납니다.

### <a name="to-group-threads"></a>스레드를 그룹화하려면

- 에 **스레드** 창 도구 모음을 선택 합니다 **그룹화** 목록 다음 스레드를 그룹화 하려는 조건을 선택 합니다.

### <a name="to-sort-threads-within-groups"></a>그룹 내에서 스레드를 정렬하려면

1. 맨 위에 있는 도구 모음에서의 **스레드** 창에서를 **그룹화** 목록 다음 스레드를 그룹화 하려는 조건을 선택 합니다.

2. 에 **스레드** 창 열의 맨 위에 있는 단추를 선택 합니다.

     이제 해당 열의 값으로 스레드가 정렬됩니다.

### <a name="to-expand-or-collapse-all-groups"></a>모든 그룹을 확장하거나 축소하려면

- 맨 위에 있는 도구 모음에는 **스레드** 창에서 **그룹을 확장** 또는 **그룹 축소**합니다.

## <a name="search-for-specific-threads"></a>특정 스레드 검색
 지정된 된 문자열과 일치 하는 스레드를 검색할 수 있습니다 합니다 **스레드** 창입니다. 스레드를 검색 하는 경우 모든 열에 검색 문자열과 일치 하는 모든 스레드는 창에 표시 됩니다. 이 정보에는 **위치** 열의 호출 스택 맨 위에 나타나는 스레드 위치가 포함됩니다. 기본적으로 전체 호출 스택을 검색 되지 않습니다.

### <a name="to-search-for-specific-threads"></a>특정 스레드를 검색하려면

1. **스레드** 창의 맨 위에 있는 도구 모음에서 **검색** 상자로 이동하고 다음을 수행합니다.

     - 검색 문자열을 입력 하 고 다음 키를 누릅니다 **Enter**합니다.

     \- 또는 -

     - 드롭다운 목록 옆에 선택 합니다 **검색** 상자 하 고 이전 검색에서 검색 문자열을 선택 합니다.

2. (선택 사항) 검색에 전체 호출 스택을 포함하려면 **호출 스택 검색**을 선택합니다.

## <a name="display-thread-call-stacks-and-switch-between-frames"></a>스레드 호출 스택 표시 및 프레임 간 전환
다중 스레드 프로그램에서 각 스레드에는 자신의 고유한 호출 스택이 있습니다. **스레드** 창을 사용하여 편리하게 이러한 스택을 볼 수 있습니다.

> [!TIP]
> 각 스레드에 대해 호출 스택의 시각적 표현을 사용 합니다 [병렬 스택](../debugger/get-started-debugging-multithreaded-apps.md) 창입니다.

### <a name="to-view-the-call-stack-of-a-thread"></a>스레드의 호출 스택을 보려면

- 에 **위치** 열에서 스레드 위치 옆에 있는 역된 삼각형을 선택 합니다.

     위치가 확장되어 스레드의 전체 호출 스택이 표시됩니다.

### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>모든 스레드의 호출 스택을 보거나 축소하려면

- 맨 위에 있는 도구 모음에는 **스레드** 창에서 **호출 스택 확장명** 또는 **호출 스택 축소**합니다.

## <a name="see-also"></a>참고자료
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [다중 스레드 애플리케이션 디버깅 시작](../debugger/get-started-debugging-multithreaded-apps.md)
