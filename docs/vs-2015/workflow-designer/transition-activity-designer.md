---
title: 전환 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
caps.latest.revision: 7
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 026ee7af3c60b3832449f5f2ed996f00c75a1c87
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435374"
---
# <a name="transition-activity-designer"></a>전환 활동 디자이너
<xref:System.Activities.Statements.Transition>은 두 상태 간 전환을 나타냅니다.  
  
## <a name="using-the-transition-activity-designer"></a>전환 활동 디자이너 사용  
 전환 활동 디자이너를 사용하면 두 상태 간에 전환을 구성할 수 있습니다.  
  
### <a name="transition-properties-in-the-workflow-designer"></a>Workflow Designer의 Transition 속성  
 다음 표에서는 워크플로 디자이너를 사용하여 설정할 수 있는 <xref:System.Activities.Statements.Transition> 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다.  
  
|속성 이름|필수|사용법|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|<xref:System.Activities.Statements.Transition> 활동 디자이너의 이름을 지정합니다. 기본값은 **T1**합니다. 값은 속성 표, 확장된 전환 디자이너의 헤더 및 확장된 전환 디자이너 내에서 작업 섹션의 헤더에서 편집할 수 있습니다. <xref:System.Activities.Activity.DisplayName%2A>은 워크플로 디자이너 상단에 표시되는 이동 경로 탐색에 사용됩니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|  
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|있는 경우 계산 되어야 하는 식을 지정 **True** 전에 대상 상태로 제어가 전달 됩니다. 속성 표 및 확장 전환 디자이너에서 이 조건을 편집할 수 있습니다. 전환 디자이너에 나타나는 순서로 공유 전환의 여러 조건을 평가합니다. **참고:**  경우는 <xref:System.Activities.Statements.Transition.Condition%2A> 로 전환 **False** (모든 공유 트리거 전환 조건이 또는 **False**), 전환이 발생 하지 것입니다 및 모두에 대 한 모든 트리거를 상태 전환은 다시 실행 됩니다. 이 자습서에서는 조건이 구성된 방식(추측이 올바른지 또는 잘못되었는지에 따라 특정 동작이 지정됨) 때문에 이러한 상황이 발생할 수 없습니다.|  
|**소스**|True|이 전환이 원래 발생한 상태를 나타냅니다. 소스 상태의 이름을 클릭하면 디자이너 보기가 해당 상태의 확장된 보기로 전환됩니다. 이 값은 전환이 만들어질 때 설정되며 변경될 수 있습니다.|  
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|완료 시 전환을 시작하는 활동을 지정합니다. 활동을 끌어이 작업을 설정 하려면 합니다 **도구 상자** 놓습니다 합니다 **트리거** 전환의 섹션입니다.|  
|<xref:System.Activities.Statements.Transition.Action%2A>|False|트리거 활동이 완료 되 면 실행 되는 활동을 지정 하며 <xref:System.Activities.Statements.Transition.Condition%2A>가 있으면로 **true**합니다. 이 활동은 소스 상태(있을 경우)에 대한 <xref:System.Activities.Statements.State.Exit%2A> 활동이 실행된 후에 대상 상태로 전환할 때 실행됩니다. 전환 디자이너가 확장 되는 경우이 값에서 활동을 끌어 설정할 수 있습니다 합니다 **도구 상자** 놓으면 합니다 **작업** 전환의 섹션입니다. 단일 전환에 여러 작업이 있을 수 있습니다. 개별 작업을 확장하고 수축할 수 있으며 전환 중인 작업이 여러 개 있을 때 작업에 나타나는 위 또는 아래 화살표를 클릭하여 순서를 지정할 수 있습니다.|  
|**대상**|True|전환이 완료된 후 상태 시스템이 전환하는 상태를 나타냅니다. 이는 개체 모델에 있는 전환의 <xref:System.Activities.Statements.Transition.To%2A> 속성에 해당합니다. 대상 상태의 이름을 클릭하면 디자이너 보기가 해당 상태의 확장된 보기로 전환됩니다. 이 값은 전환이 만들어지면 설정되고 전환을 디자이너의 대상 상태에 연결하는 화살표를 끌어 변경할 수 있습니다.|  
  
### <a name="creating-transitions"></a>전환 만들기  
 전환은 한 상태에서 다른 상태로 선을 끌거나 한 상태를 다른 상태 위로 끌어갈 때 나타나는 삼각형에 상태를 놓으면 만들어집니다. 끌어서 전환을 만들려면 소스 상태의 가장자리 위로 마우스를 가져가 소스 상태에서 대상 상태로 선을 끕니다. 놓아서 전환을 만들려면 대상 상태를 끌어 소스 상태 위로 가져가 소스 상태 주변에 나타나는 4개의 삼각형 중 하나에 놓습니다. 대상 상태에서 끌어온 새로운 상태 수를 **도구 상자**, 워크플로 디자이너에서 끌어온 기존 상태가 또는 합니다.  
  
> [!NOTE]
> 상태 시스템에서 하나의 상태는 Workflow Designer를 사용하여 만들어지는 전환을 76개까지 사용할 수 있습니다. 디자이너 밖에서 만들어지는 워크플로 상태의 전환에 대한 제한은 시스템 리소스로만 제한됩니다.  
  
 공유 트리거 전환은 같은 트리거 이벤트를 공유하는 전환 집합입니다. 공유 트리거를 사용하면 공통의 트리거 이벤트를 공유하는 여러 전환에 대해 구성된 식의 평가를 기준으로 대상 상태로 조건적 진행이 가능합니다. 전환에 추가 작업을 추가하고 공유 전환을 만들려면 원하는 전환의 시작을 나타내는 원을 클릭하고 원하는 상태로 끕니다. 새 전환은 초기 전환과 동일한 트리거를 공유하지만 고유한 조건과 작업을 사용합니다. 공유 전환을 만들 수도 있습니다에서 전환 디자이너 내에서 클릭 하 여 **공유 트리거 전환 추가** 아래쪽의 전환 디자이너, 한 다음 원하는 대상 상태를 선택 하 여  **연결에 사용할 상태** 드롭 다운 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [상태](../workflow-designer/state-activity-designer.md)