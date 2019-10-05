---
title: 호출 스택의 시각적 맵 만들기 | Microsoft Docs
ms.date: 11/26/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62fb77590a20b0e31648cab10f310851fd65820e
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180000"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>디버깅 하는 동안 호출 스택의 시각적 맵 만들기 (C#, Visual Basic, C++, JavaScript)

디버깅하는 동안 호출 스택을 시각적으로 추적할 코드 맵을 만듭니다. 맵을 기록해 두면 코드에서 어떤 작업을 하고 있는지 추적하여 버그를 찾는 데 집중할 수 있습니다.

연습을 보려면 다음 비디오를 시청 하세요. [비디오: 코드 맵 디버거 통합으로 시각적으로 디버그 (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

코드 맵과 함께 사용할 수 있는 명령 및 작업에 대 한 자세한 내용은 [코드 맵 찾아보기 및 다시 정렬](../modeling/browse-and-rearrange-code-maps.md)을 참조 하세요.

>[!IMPORTANT]
>[Visual Studio Enterprise edition](https://visualstudio.microsoft.com/downloads)에서만 코드 맵을 만들 수 있습니다.

다음은 코드 맵을 간략히 살펴보는 것입니다.

 ![코드 맵의 호출 스택을 사용 하 여 디버깅](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

## <a name="MapStack"></a> 호출 스택 매핑

1. C#Visual Basic C++Visual Studio Enterprise, 또는 JavaScript 프로젝트에서 **디버그** > **디버깅 시작** 을 선택 하거나 **F5**키를 눌러 디버깅을 시작 합니다.

1. 앱이 중단 모드에 들어가거나 함수를 한 단계씩 실행 하면 **디버그** > **코드 맵**을 선택 하거나 **ctrl**+**Shift**+ **`** 를 누릅니다.

   현재 호출 스택은 새 코드 맵에 주황색으로 표시됩니다.

   ![코드 맵의 호출 스택 참조](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

디버깅을 계속할 때 코드 맵이 자동으로 업데이트 됩니다. 지도 항목 또는 레이아웃을 변경 해도 코드에는 영향을 주지 않습니다. 맵에서 이름 바꾸기, 이동 또는 제거 기능을 자유롭게 사용할 수 있습니다.

항목에 대 한 자세한 정보를 보려면 해당 항목 위로 마우스를 이동 하 여 항목의 도구 설명을 확인 합니다. 도구 모음에서 **범례** 를 선택 하 여 각 아이콘의 의미를 확인할 수도 있습니다.

![코드 맵 범례](../debugger/media/debuggermap_showlegend.png "코드 맵 범례")

>[!NOTE]
>다이어그램은 코드 맵의 맨 위에 있는 **코드의 이전 버전을 기반으로** 할 수 있습니다. 지도를 마지막으로 업데이트 한 후 코드가 변경 되었을 수 있음을 의미 합니다. 예를 들어 맵에 대한 호출이 더 이상 코드에 없는 경우가 있습니다. 메시지를 닫은 다음 맵을 다시 업데이트하기 전에 솔루션 다시 빌드를 시도합니다.

## <a name="map-external-code"></a>외부 코드 매핑

기본적으로 맵에는 고유한 코드만 나타납니다. 지도에서 외부 코드를 보려면 다음을 수행 합니다.

- **호출 스택** 창에서 마우스 오른쪽 단추를 클릭 하 고 **외부 코드 표시**를 선택 합니다.

  ![호출 스택 창을 사용 하 여 외부 코드 표시](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- 또는 Visual Studio **Tools** (또는 **디버그**) > **옵션** > **디버깅**에서 **내 코드만 사용** 을 선택 취소 합니다.

  ![옵션 대화 상자를 사용 하 여 외부 코드 표시](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>지도의 레이아웃 제어

맵의 레이아웃을 변경 해도 코드에는 영향을 주지 않습니다.

지도의 레이아웃을 제어 하려면 맵 도구 모음에서 **레이아웃** 메뉴를 선택 합니다.

**레이아웃** 메뉴에서 다음을 수행할 수 있습니다.

- 기본 레이아웃을 변경합니다.
- **디버그할 때 자동으로 레이아웃**을 선택 취소 하 여 지도를 자동으로 다시 정렬 하지 않습니다.
- **증분 레이아웃**의 선택을 취소 하 여 항목을 추가할 때 맵을 최대한 적게 다시 정렬 합니다.

## <a name="MakeNotes"></a> 코드에 대해 메모하기

주석을 추가 하 여 코드에서 발생 하는 상황을 추적할 수 있습니다.

주석을 추가 하려면 코드 맵을 마우스 오른쪽 단추로 클릭 하 고**새 주석** **편집** > 을 선택한 다음 주석을 입력 합니다.

주석에 새 줄을 추가 하려면 **Shift**+**enter**를 누릅니다.

 ![코드 맵의 호출 스택에 주석 추가](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> 다음 호출 스택과 함께 맵 업데이트

응용 프로그램을 다음 중단점까지 실행 하거나 함수를 한 단계씩 실행 하면 새 호출 스택이 자동으로 추가 됩니다.

![다음 호출 스택으로 코드 맵 업데이트](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

새 호출 스택이 자동으로 추가 되지 않도록 하려면 코드 맵 도구 ![]모음에서 자동으로 코드 맵에(../debugger/media/debuggermap_automaticupdateicon.gif "호출 스택") 표시를 코드 맵에 자동으로 표시를 선택 합니다. 맵은 기존 호출 스택을 계속 강조 표시 합니다. 현재 호출 스택을 맵에 수동으로 추가 하려면 다음을 누릅니다 **Ctrl**+**Shift**+ **`** 합니다.

## <a name="AddRelatedCode"></a> 맵에 관련 코드 추가

이제 또는 Visual Basic에서 C# 맵을 가져왔습니다. 필드, 속성 및 기타 메서드 등의 항목을 추가 하 여 코드에서 발생 하는 일을 추적할 수 있습니다.

코드의 메서드 정의로 이동 하려면 맵에서 메서드를 두 번 클릭 하거나, 해당 메서드를 선택 하 고 **F12**키를 누르거나 마우스 오른쪽 단추를 클릭 하 고 **정의로 이동**을 선택 합니다.

![코드 맵에서 메서드에 대 한 코드 정의로 이동](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

추적 하려는 항목을 지도에 추가 하려면 메서드를 마우스 오른쪽 단추로 클릭 하 고 추적 하려는 항목을 선택 합니다. 가장 최근 추가된 항목은 녹색으로 표시됩니다.

![호출 스택 코드 맵의 메서드와 관련 된 필드](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>기본적으로 맵에 항목을 추가하면 클래스, 네임스페이스 및 어셈블리와 같은 부모 그룹 노드도 추가됩니다. 코드 맵 도구 모음에서 **부모 포함** 단추를 선택 하거나 항목을 추가 하는 동안 **Ctrl** 키를 눌러이 기능을 사용 하지 않도록 설정할 수 있습니다.

![호출 스택 코드 맵에 메서드에 필드 표시](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

더 많은 코드를 보려면 맵 빌드를 계속합니다.

 ![필드를 사용 하는 메서드: 호출 스택 코드 맵을 참조 하세요.](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![호출 스택 코드 맵에 있는 필드를 사용 하는 메서드](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> 맵을 사용하여 버그 찾기
 코드를 시각화하면 버그를 더 빠르게 찾을 수 있습니다. 예를 들어 그리기 앱에서 버그를 조사 하는 경우를 가정해 보겠습니다. 선을 그렸다가 취소하려는 경우 다른 선을 그릴 때까지 아무 것도 발생하지 않습니다.

 따라서 `clear`, `undo` 및 `Repaint` 메서드에서 중단점을 설정하고, 디버깅을 시작하고, 다음과 같은 맵을 빌드합니다.

 ![코드 맵에 다른 호출 스택 추가](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 `Repaint`를 제외하고 맵 호출 `undo`에 대한 모든 사용자 제스처를 확인할 수 있습니다. `undo`가 즉시 작동하지 않는 이유를 이해할 수 있을 것입니다.

 버그를 수정 하 고 응용 프로그램을 계속 실행 한 후 맵은의 새 호출 `undo` 을에 `Repaint`추가 합니다.

 ![코드 맵의 호출 스택에 새 메서드 호출 추가](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>다른 사용자와 맵 공유

맵을 내보내고 Microsoft Outlook을 사용 하 여 다른 사람에 게 보내고, 솔루션에 저장 하 고, 버전 제어에 체크 인할 수 있습니다.

맵을 공유 하거나 저장 하려면 코드 맵 도구 모음에서 **공유** 를 사용 합니다.

![다른 사람과 호출 스택 코드 맵 공유](../debugger/media/debuggermap_sharewithothers.png "다른 사람과 호출 스택 코드 맵 공유")

## <a name="see-also"></a>참고자료
[솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)

[코드 맵을 사용하여 응용 프로그램 디버그](../modeling/use-code-maps-to-debug-your-applications.md)

[코드 맵 분석기를 사용하여 잠재적 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)

[코드 맵 찾아보기 및 다시 정렬](../modeling/browse-and-rearrange-code-maps.md)
