---
title: FinalState 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
caps.latest.revision: 5
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0a969b81e3291191cf42df4e1775c4212f54e4cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951998"
---
# <a name="finalstate-activity-designer"></a>FinalState 활동 디자이너
<xref:System.Activities.Core.Presentation.FinalState> 디자이너는 상태 시스템 인스턴스를 종료하는 <xref:System.Activities.Statements.State>를 만드는 데 사용됩니다.  
  
## <a name="using-the-finalstate-activity-designer"></a>FinalState 활동 디자이너 사용  
 합니다 **FinalState** 디자이너를 만드는 데 사용 되는 <xref:System.Activities.Statements.State> 상태 시스템에서 종료 상태로 미리 구성 되는 합니다. <xref:System.Activities.Statements.State> 를 사용 하 여 만든 합니다 <xref:System.Activities.Core.Presentation.FinalState> 활동 디자이너에 해당 <xref:System.Activities.Statements.State.IsFinal%2A> 속성이로 설정 **true**, 되지 <xref:System.Activities.Statements.State.Exit%2A> 활동과에서 시작 되는 전환이 없는 합니다. 사용 하는 <xref:System.Activities.Core.Presentation.FinalState> 추가할 활동 디자이너를 <xref:System.Activities.Statements.State> 상태 시스템에서 종료 상태로 미리 구성 된 활동으로 끌어 합니다 **FinalState** 활동 디자이너의는 **상태 시스템**섹션의 **도구 상자** 워크플로 디자이너에 끌어 놓습니다. <xref:System.Activities.Core.Presentation.FinalState> 활동 디자이너를 <xref:System.Activities.Statements.StateMachine>에 끌어 놓고 나중에 전환을 추가하거나 <xref:System.Activities.Core.Presentation.FinalState> 활동 디자이너를 끌어 놓을 때 전환을 만들 수 있습니다. 전환 만들기에 대 한 자세한 내용은 참조 하세요. [전환](../workflow-designer/transition-activity-designer.md)합니다.  
  
### <a name="state-activity-properties-in-the-workflow-designer"></a>Workflow Designer의 State 활동 속성  
 다음 표에서는 <xref:System.Activities.Core.Presentation.FinalState> 디자이너를 사용하여 설정할 수 있는 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다. 이러한 일부 속성은 속성 표에서 편집할 수 있으며 일부 속성은 디자이너 화면에서 편집할 수 있습니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|머리글에 <xref:System.Activities.Statements.State> 활동 디자이너의 이름을 지정합니다. 기본값은 **상태**합니다. 속성 표에서 또는 활동 디자이너의 머리글에서 직접 값을 편집할 수 있습니다. <xref:System.Activities.Statements.State.DisplayName%2A>은 워크플로 디자이너 상단에 표시되는 이동 경로 탐색에 사용됩니다.<br /><br /> <xref:System.Activities.Statements.State.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|이 상태가 전환될 때 발생하는 동작을 지정합니다. 활동을 끌어이 값을 설정할 수 있습니다 합니다 **도구 상자** 놓으면는 <xref:System.Activities.Statements.State.Entry%2A> 상태 섹션입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [State](../workflow-designer/state-activity-designer.md)   
 [Transition](../workflow-designer/transition-activity-designer.md)