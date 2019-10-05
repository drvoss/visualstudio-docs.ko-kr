---
title: 워크플로 디자이너-상태 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4d07cfeeb713767bc4f711c99b6b482759af2232
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62434080"
---
# <a name="state-activity-designer"></a>상태 활동 디자이너

<xref:System.Activities.Statements.State>는 상태 시스템이 가질 수 있는 상태를 나타냅니다.

## <a name="using-the-state-activity-designer"></a>상태 활동 디자이너 사용

추가할를 <xref:System.Activities.Statements.State> 워크플로 끌어 옵니다.를 **상태** 활동 디자이너의를 **상태 시스템** 섹션을 **도구 상자** 에 놓습니다를 <xref:System.Activities.Statements.StateMachine> 워크플로 디자이너 화면에서 작업입니다. <xref:System.Activities.Statements.State> 활동은 <xref:System.Activities.Statements.StateMachine>에 끌어 놓고 나중에 전환을 추가하거나 <xref:System.Activities.Statements.State> 활동을 끌어 놓을 때 전환을 만들 수 있습니다. 추가할를 <xref:System.Activities.Statements.State> 활동 고 한 단계로 끌어서 전환을 만들려면를 **상태** 활동에서를 **상태 시스템** 섹션을 **도구 상자** 다른 위로 가져갑니다 워크플로 디자이너의 상태입니다. 끌어 온 <xref:System.Activities.Statements.State>를 다른 <xref:System.Activities.Statements.State> 위로 가져가면 <xref:System.Activities.Statements.State> 주위에 삼각형 4개가 표시됩니다. <xref:System.Activities.Statements.State>를 삼각형 4개 중 하나에 놓으면 상태 시스템에 추가되고, 소스 <xref:System.Activities.Statements.State>에서 놓은 대상 <xref:System.Activities.Statements.State>로의 전환이 만들어집니다. 자세한 내용은 [전환](../workflow-designer/transition-activity-designer.md)합니다.

### <a name="state-activity-properties-in-the-workflow-designer"></a>Workflow Designer의 State 활동 속성

다음 표에서는 워크플로 디자이너를 사용하여 설정할 수 있는 <xref:System.Activities.Statements.State> 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다. 이러한 일부 속성은 속성 표에서 편집할 수 있으며 일부 속성은 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|머리글에 <xref:System.Activities.Statements.State> 활동 디자이너의 이름을 지정합니다. 기본값은 **상태**합니다. 속성 표에서 또는 활동 디자이너의 머리글에서 직접 값을 편집할 수 있습니다. <xref:System.Activities.Statements.State.DisplayName%2A>은 워크플로 디자이너 상단에 표시되는 이동 경로 탐색에 사용됩니다.<br /><br /> <xref:System.Activities.Statements.State.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|이 상태가 전환될 때 발생하는 동작을 지정합니다. 경우는 <xref:System.Activities.Statements.State> 활동을 확장에서 활동을 끌어이 값을 설정할 수 있습니다 합니다 **도구 상자** 놓으면를 **항목** 상태 섹션.|
|<xref:System.Activities.Statements.State.Exit%2A>|False|이 상태가 다른 상태로 전환될 때 발생하는 동작을 지정합니다. 경우는 <xref:System.Activities.Statements.State> 활동을 확장에서 활동을 끌어이 값을 설정할 수 있습니다 합니다 **도구 상자** 놓으면를 **종료** 상태 섹션.|
|<xref:System.Activities.Statements.State.Transitions%2A>|False|<xref:System.Activities.Statements.State>에서 가능한 전환을 나열합니다. 목록의 각 항목에는 관련 <xref:System.Activities.Statements.Transition> 및 대상 <xref:System.Activities.Statements.State>에 대한 링크가 있습니다. 링크를 클릭하면 디자이너가 <xref:System.Activities.Statements.Transition> 또는 <xref:System.Activities.Statements.State>의 확장된 보기로 전환됩니다.|

## <a name="see-also"></a>참고자료

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)