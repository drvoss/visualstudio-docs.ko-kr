---
title: Using the Legacy State Machine Workflow Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bab07b8ba0b71bd880135518ff9ff5fc697d54c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302815"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>레거시 상태 시스템 워크플로 디자이너 사용
When you are creating a new state machine workflow project in [!INCLUDE[vs2010](../includes/vs2010-md.md)] that targets either the [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] or the [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], you can choose to use either the **State Machine Workflow Console Application** or the **State Machine Workflow Library** legacy project template. 이러한 상태 시스템 프로젝트 템플릿 중 하나를 선택하면 상태 시스템 디자이너가 레거시 Workflow Designer 사용자 인터페이스로 나타납니다. For information about the legacy state machine project templates, see [How to: Create State Machine Workflow Console Applications (Legacy)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) and [How to: Create a State Machine Workflow Library (Legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 상태 시스템 워크플로는 상태 집합으로 구성됩니다. 하나의 상태가 초기 상태로 표시됩니다. 각 상태는 특정 이벤트 집합을 받을 수 있으며 이벤트에 따라 다른 상태로 전환될 수 있습니다. 상태 시스템 워크플로는 최종 상태를 가질 수 있으며, 최종 상태로 전환되면 워크플로가 완료됩니다.

## <a name="state-machine-designer-views"></a>상태 시스템 디자이너 뷰
 상태 시스템 디자이너는 자유형 디자이너로서, 디자인 화면에서 활동을 자유롭게 이동할 수 있습니다. The state machine designer has two views: *state* view and *event-driven* view.

 상태 뷰에서는 상태 활동 및 상태 활동에 포함할 수 있는 이벤트 구동 활동을 표시합니다. 이 뷰에서는 상태 전환이 한 상태의 이벤트 구동 활동에서 다른 상태로 이어지는 선으로 표현됩니다. 직접 선을 그려서 전환을 만들 수도 있습니다. 전환을 그리려면 이벤트 구동 활동을 선택한 다음 해당 활동의 핸들 중 하나를 선택하여 끕니다. 그러면 선이 그려집니다. 그려진 선은 대상 상태에 연결되어 상태 전환을 나타냅니다.

 이벤트 구동 뷰에 액세스하려면 이벤트 구동 활동을 두 번 클릭합니다. 순차 워크플로 디자이너와 매우 비슷한 디자이너가 나타납니다. 디자이너 맨 위의 탐색 모음은 활동의 계층 구조를 표시하며 이 계층 구조에는 이벤트 구동 활동까지 나타납니다. 표시된 계층 구조에서 임의의 요소를 클릭하면 상태 뷰로 돌아갈 수 있습니다. 상태 뷰에서 상태 전환을 그렸고 해당 활동의 이벤트 구동 뷰를 표시하려는 경우, 설정된 상태 활동이 이벤트 구동 활동에 추가됩니다. 설정된 상태 활동의 속성을 변경하면 이는 다시 상태 뷰에 반영됩니다.

## <a name="state-machine-workflow-activities"></a>상태 시스템 워크플로 활동
 다음 표에서는 상태 시스템 Workflow Designer에서 사용되는 핵심 활동에 대해 설명합니다.

|도구 상자 이름|활동|설명|
|------------------|--------------|-----------------|
|**상태**|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|Represents a state in a state machine; may contain additional **StateActivity** activities. For more information, see [Using the StateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65083).|
|**SetState**|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|새 상태로의 전환을 지정합니다. For more information, see [Using the SetStateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|상태가 시작되면 실행되며, 다른 활동을 포함할 수도 있습니다. For more information, see [Using the StateInitialization Activity](https://go.microsoft.com/fwlink?LinkID=65006).|
|**StateFinalization**|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Executes contained activities when leaving a [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) activity. For more information, see [Using the StateFinalizationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|실행 시작 여부가 외부 이벤트에 따라 달라지는 상태에 사용됩니다. The **EventDrivenActivity** activity must have an activity that implements the [IEventActivity](https://go.microsoft.com/fwlink?LinkID=65032) interface as the first child activity. For more information, see [Using the EventDrivenActivity Activity](https://go.microsoft.com/fwlink?LinkID=65068).|

 The main component in a state machine workflow is the [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) activity. 상태 시스템 워크플로의 여러 지점에서 이벤트가 캡처되므로 이벤트와 연결된 작업을 처리하기 위해 여러 상태가 시작됩니다. 워크플로 수명 중에 워크플로가 여러 상태를 끝내고 시작할 수 있습니다. These states connect to each other by using the [SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041) activity.

 When you drag a new **StateActivity** onto the workflow design surface, you can add [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043), or additional **StateActivity** activities as child activities.

> [!CAUTION]
> When you use the state machine workflow designer to create workflows, you must monitor the structure of the workflow you are designing with the **Document Outline** view window. The view of the structure of the state machine workflow in the **Document Outline** view window mirrors the logical layout of the activities in the workflow markup file. 디자인 화면에 나타나는 워크플로 활동의 실제 레이아웃은 워크플로 마크업 파일의 활동에 대한 논리 레이아웃을 미러링하지 않을 수도 있습니다.
>
> To open the **Document Outline** window, on the **View** menu, point to **Other Windows**, and then select **Document Outline**.

## <a name="see-also"></a>관련 항목:
 [How to: Create State Machine Workflow Console Applications (Legacy)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) [How to: Create a State Machine Workflow Library (Legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) [State Machine Workflows](https://go.microsoft.com/fwlink?LinkID=65016) [Using the StateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65083) [Using the StateInitializationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65006) [Using the StateFinalizationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65008) [Using the SetStateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65082) [Using the EventDrivenActivity Activity](https://go.microsoft.com/fwlink?LinkID=65068)