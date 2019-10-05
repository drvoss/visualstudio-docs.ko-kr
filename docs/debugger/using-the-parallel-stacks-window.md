---
title: 병렬 스택 창의 스레드를 보는 | Microsoft Docs
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9728346bc4c6d805bb0febd3a0d5bef0ed809a5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902423"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>병렬 스택 창의 스레드 및 작업 보기 (C#, Visual Basic의 경우 C++)

합니다 **병렬 스택** 창은 다중 스레드 응용 프로그램 디버깅에 유용 합니다. 여러 보기가 있습니다.

- [스레드 뷰](#threads-view) 앱의 모든 스레드에 대 한 호출 스택 정보를 표시 합니다. 스레드 및 스레드와 스레드 스택 프레임 간을 탐색할 수 있습니다.

- [작업 보기](#tasks-view) 작업 중심 호출 스택 정보를 표시 합니다.
  - 관리 코드에서는 **태스크** 보기의 호출 스택이 표시 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 개체입니다.
  - 네이티브 코드로 **태스크** 보기의 호출 스택이 표시 [작업 그룹](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [병렬 알고리즘](/cpp/parallel/concrt/parallel-algorithms), [비동기 에이전트](/cpp/parallel/concrt/asynchronous-agents), 및 [간단한 작업](/cpp/parallel/concrt/task-scheduler-concurrency-runtime)합니다.

- [메서드 뷰](#method-view) 선택한 메서드에 대 한 호출 스택을 피벗 합니다.

## <a name="use-the-parallel-stacks-window"></a>병렬 스택 창 사용

열려는 합니다 **병렬 스택** 창 디버깅 세션에서 여야 합니다. 선택 **디버깅할** > **Windows** > **병렬 스택**합니다.

### <a name="toolbar-controls"></a>도구 모음 컨트롤

합니다 **병렬 스택** 창에는 다음 도구 모음 컨트롤이:

![병렬 스택 창의 도구 모음](../debugger/media/parallel_stackstoolbar.png "병렬 스택 도구 모음")

|아이콘|컨트롤|설명|
|-|-|-|
|![스레드/작업 콤보 상자](media/parallel_toolbar1.png "스레드/작업 콤보 상자")|**스레드**/**작업** 콤보 상자|스레드의 호출 스택과 작업의 호출 스택 간에 뷰를 전환합니다. 자세한 내용은 [작업 뷰](#tasks-view)와 [스레드 뷰](#threads-view)를 참조하세요.|
|![플래그가 지정 된 아이콘을 보여 줍니다](media/parallel_toolbar2.png "지정 된 스레드만 표시 아이콘")|플래그가 지정된 항목만 표시|와 같은 다른 디버거 창에서 플래그가 지정 된 스레드에 대해서만 호출 스택이 표시 합니다 **GPU 스레드** 창 및 **병렬 조사식** 창입니다.|
|![메서드 뷰 설정/해제 아이콘](media/parallel_toolbar3.png "메서드 뷰 설정/해제 아이콘")|**메서드 뷰** 설정/해제|호출 스택 뷰 사이 전환 하 고 **메서드 뷰**합니다. 자세한 내용은 [메서드 뷰](#method-view)를 참조하세요.|
|![현재 아이콘으로 자동 스크롤](media/parallel_toolbar4.png "현재 아이콘으로 자동 스크롤")|현재 스택 프레임으로 자동 스크롤|그래프 표시는 현재 스택 프레임이 뷰에 표시 됩니다. 이 기능은 다른 창에서 현재 스택 프레임을 변경할 때 또는 대형 그래프의 새 중단점을 적중 하는 경우에 유용 합니다.|
|![확대/축소 아이콘을 설정/해제](media/parallel_toolbar5.png "확대/축소 토글 아이콘")|확대/축소 컨트롤 설정/해제|표시 하거나 왼쪽 창에 있는 확대/축소 컨트롤을 숨깁니다. <br /><br />확대/축소 컨트롤의 표시 여부에 관계 없이 키를 눌러 확대 수도 수 있습니다 **Ctrl** 및에서 마우스 휠을 돌려서 또는 키를 눌러 **Ctrl**+**Shift** + **+** 확대 하 고 **Ctrl**+**Shift** + **-** 축소 합니다. |

### <a name="stack-frame-icons"></a>스택 프레임 아이콘
다음 아이콘 모든 보기에서 활성 상태이 고 현재 스택 프레임에 대 한 정보를 제공합니다.

|아이콘|설명|
|-|-|
|![노란색 화살표](media/icon_parallelyellowarrow.gif)|현재 스레드의 현재 위치 (활성 스택 프레임)를 나타냅니다.|
|![스레드 아이콘](media/icon_parallelthreads.gif)|-현재 스레드의 현재 위치 (활성 스택 프레임)를 나타냅니다.|
|![녹색 화살표](media/icon_parallelgreenarrow.gif)|현재 스택 프레임 (현재 디버거 컨텍스트)를 나타냅니다. 메서드 이름이 표시 될 때마다 굵게 표시 됩니다.|

### <a name="context-menu-items"></a>컨텍스트 메뉴 항목
다음 바로 가기 메뉴 항목의 메서드를 마우스 오른쪽 단추로 클릭할 때 사용할 **스레드** 보기 또는 **작업** 보기. 마지막 6 개 항목에서와 동일 합니다 [호출 스택 창](how-to-use-the-call-stack-window.md)합니다.

![병렬 스택 창의 바로 가기 메뉴](../debugger/media/parallel_contmenu.png "병렬 스택 창의 바로 가기 메뉴")

|Menu item|설명|
|-|-|
|**플래그**|선택한 항목에 플래그를 지정합니다.|
|**플래그 해제**|선택한 항목의 플래그를 해제합니다.|
|**중지**|선택한 항목을 중지합니다.|
|**재개**|선택한 항목을 재개합니다.|
|**프레임으로 전환**|해당 메뉴로 동일한 명령에 **호출 스택** 창입니다. 그러나 합니다 **병렬 스택** 창에서 한 가지 방법은 여러 프레임에 있을 수 있습니다. 이 항목의 하위 메뉴에서 원하는 프레임을 선택할 수 있습니다. 현재 스레드의 스택 프레임 중 하나 이면 해당 프레임의 하위 메뉴에는 기본적으로 선택 됩니다.|
|**태스크로 이동** 또는 **스레드로 이동**|전환 합니다 **태스크** 또는 **스레드** 뷰와 동일한 스택 프레임이 강조 표시 된 유지 합니다.|
|**소스 코드로 이동**|소스 코드 창에서 해당 위치로 이동합니다. |
|**디스어셈블리로 이동**|해당 위치를 이동 합니다 **디스어셈블리** 창입니다.|
|**외부 코드 표시**|외부 코드를 표시하거나 숨깁니다.|
|**16진수 표시**|10진수 표시와 16진수 표시 간을 전환합니다.|
|**소스의 스레드 표시**|소스 코드 창에서 스레드 위치를 플래그합니다. |
|**기호 로드 정보**|열립니다는 **기호 로드 정보** 대화 상자.|
|**기호 설정**|열립니다는 **기호 설정** 대화 상자. |

## <a name="threads-view"></a>스레드 뷰

**스레드** 보기 스택 프레임 및 현재 스레드의 호출 경로 파란색으로 강조 표시 합니다. 스레드의 현재 위치는 노란색 화살표로 표시 됩니다.

현재 스택 프레임을 변경 하려면 다른 메서드를 두 번 클릭 합니다. 이 선택한 방법은 현재 스레드 또는 다른 스레드의 일부 인지에 따라 현재 스레드가 전환할 수도 있습니다.

경우는 **스레드** 그래프 보기 창에 맞게 너무 큽니다를 **Bird's Eye View** 제어 창에 나타납니다. 그래프의 다른 부분으로 이동할 컨트롤의 프레임을 이동할 수 있습니다.

다음 그림에서는 Main에서 이동 하 여 네이티브 코드로 전환 관리 하는 하나의 스레드를 보여 줍니다. 현재 메서드가 있는 스레드 수는 6입니다. Thread.Sleep을 계속 하나 및 Console.WriteLine 및 SyncTextWriter.WriteLine 계속 다른 합니다.

 ![병렬 스택 창의 뷰를 스레드](../debugger/media/parallel_stack1.png "스레드 병렬 스택 창의 뷰")

다음 표에서 주요 기능을 설명 합니다 **스레드** 보기:

|설명선|요소 이름|설명|
|-|-|-|
|1|호출 스택 세그먼트 또는 노드|일련의 하나 이상의 스레드에 대 한 메서드를 포함합니다. 프레임에 연결 된 화살표 선이 없으면, 프레임 스레드에 대 한 전체 호출 경로 표시 합니다.|
|2|파란색 강조 표시|현재 스레드의 호출 경로를 나타냅니다.|
|3|화살표 선|노드를 연결하여 스레드에 대한 전체 호출 경로를 구성합니다.|
|4|노드 머리글|프로세스 및 노드에 대 한 스레드 수를 보여 줍니다.|
|5|메서드|동일한 메서드에 있는 하나 이상의 스택 프레임을 나타냅니다.|
|6|메서드에 대 한 도구 설명|메서드를 마우스로 가리킬 때 표시 됩니다. **스레드** 보기 도구 설명 없이 모든 스레드의 비슷합니다 표에 표시 된 **스레드** 창입니다. |

## <a name="tasks-view"></a>작업 보기
앱에서 사용 하는 경우 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 개체 (관리 코드용) 또는 `task_handle` 사용할 수 있습니다 (네이티브 코드용) 병렬화를 표현 하 개체를 **작업** 보기. **작업** 보기에는 스레드 대신 작업의 호출 스택이 표시됩니다.

**작업** 보기:

- 작업을 실행 하지 않는 스레드의 호출 스택이 표시 되지 않습니다.
- 맨 위 및 맨 아래 작업에 대 한 가장 관련성이 높은 프레임에 표시할 작업을 실행 하는 스레드의 호출 스택은 시각적으로 잘립니다.
- 여러 작업이 하나의 스레드에서 되 면 별도 노드에서 이러한 작업의 호출 스택이 표시 됩니다.

전체 호출 스택을 보려면,으로 전환 **스레드** 스택 프레임을 마우스 오른쪽 단추로 클릭 하 고 선택 하 여 뷰 **스레드로 이동**합니다.

다음 그림에 표시 합니다 **스레드** 맨 위에 있고 해당 뷰 **작업** 맨 아래에 보기.

![스레드 및 작업 보기](../debugger/media/parallel_threads-tasks.png "스레드 및 작업 보기")

추가 정보와 함께 도구 설명을 표시 하는 메서드를 가리키면 됩니다. **작업** 보기 도구 설명 작업을 보여 줍니다 모든 테이블에서 유사 합니다 **작업** 창입니다.

다음 이미지에서 메서드에 대 한 도구 설명 표시는 **스레드** 맨 위에 있는 및 해당 보기 **작업** 맨 아래에 보기.

![스레드 및 태스크 도구 설명](../debugger/media/parallel_threads-tasks-tooltips.png "스레드 및 태스크 도구 설명")

## <a name="method-view"></a>메서드 뷰
**스레드** 보기 또는 **작업** 뷰를 선택 하 여 현재 메서드가의 그래프를 피벗할 수 있습니다 합니다 **메서드 뷰 설정/해제** 도구 모음에서 아이콘입니다. **메서드** 뷰에서는 현재 메서드를 호출하거나 현재 메서드에 의해 호출되는 모든 스레드에 대한 메서드를 모두 한눈에 볼 수 있습니다. 다음 그림에서 동일한 정보를 표시 되는 모양을 보여 주는 **스레드** 왼쪽에서 볼 **메서드 뷰** 오른쪽에 있습니다.

![스레드 뷰와 메서드 뷰](../debugger/media/parallel_methodview.png "스레드 뷰와 메서드 뷰")

새 스택 프레임으로 전환 하면 수행한 메서드는 현재 메서드 및 **메서드 뷰** 모든 호출자 및 호출 수신자에 대 한 새 메서드를 보여 줍니다. 이렇게 하면 메서드가 호출 스택에 표시되는지 여부에 따라 일부 스레드가 뷰에 나타나거나 사라집니다. 호출 스택 뷰로 돌아가려면 선택 합니다 **메서드 뷰** 도구 모음 아이콘을 다시 합니다.

## <a name="see-also"></a>참고자료
- [다중 스레드 응용 프로그램 디버깅 시작](../debugger/get-started-debugging-multithreaded-apps.md)
- [연습: 병렬 애플리케이션 디버그](../debugger/walkthrough-debugging-a-parallel-application.md)
- [디버거 소개](../debugger/debugger-feature-tour.md)
- [관리 코드 디버깅](../debugger/debugging-managed-code.md)
- [병렬 프로그래밍](/dotnet/standard/parallel-programming/index)
- [작업 창 사용](../debugger/using-the-tasks-window.md)
- [Task 클래스](../extensibility/debugger/task-class-internal-members.md)
