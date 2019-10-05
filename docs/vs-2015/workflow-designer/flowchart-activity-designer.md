---
title: 순서도 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3e89caded1b7388b79ea3232dc0a2809dc7b8222
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943466"
---
# <a name="flowchart-activity-designer"></a>순서도 활동 디자이너
<xref:System.Activities.Statements.Flowchart> 활동은 복잡한 흐름 제어를 정의하고 관리하는 워크플로를 만드는 데 사용됩니다. 코드 또는 <xref:System.Activities.Statements.Flowchart>를 사용하여 [!INCLUDE[wfd2](../includes/wfd2-md.md)]를 작성할 수 있습니다. 이 항목에서는 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 환경에 대해 설명합니다. 개발자는 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 워크플로 활동 디자이너를 사용하여 워크플로를 자연스럽게 작성할 수 있습니다.  
  
## <a name="the-flowchart-activity"></a>Flowchart 활동  
 <xref:System.Activities.Statements.Flowchart>는 워크플로를 시작할 때 실행되는 고유한 <xref:System.Activities.Statements.Flowchart.StartNode%2A>이며, 연결된 <xref:System.Activities.Statements.Flowchart.Nodes%2A> 네트워크를 사용하여 임의의 루프를 만들거나 정해진 시간에 실행 흐름을 워크플로의 다른 곳으로 전환합니다.  
  
### <a name="using-the-flowchart-activity-designer"></a>Flowchart 활동 디자이너 사용  
 **순서도** 활동 디자이너에서 찾을 수 있습니다 합니다 **순서도** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구상자**탭의 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **보기** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 **순서도** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면의 아무 곳에 나 활동 디자이너 일반적으로 배치 하는 루트 활동 또는 자식 다른 제어 흐름 활동입니다. 경우는 **순서도** 활동 디자이너는 빈 값으로 끌어 놓으면 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면을 만듭니다는 <xref:System.Activities.Statements.Flowchart> 기본적으로 자체 실행을 시작 하는 시작 노드가 확장 된 보기를 제공 하는 작업 녹색 공으로 표시 됩니다. 경우는 **순서도** 다른 제어 흐름 활동에 활동 디자이너를 두 번 클릭 하 여 확장할 수 있는 최소화 된 보기에 표시 된 **순서도** 활동 디자이너입니다. 워크플로의 모든 활동을 **도구 상자** 직접 끌어 놓을 수는 **순서도** 다른 제어 흐름 작업을 포함 하 여 활동 디자이너입니다.  
  
 여러 활동 디자이너를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 캔버스로 끌어 놓은 다음 해당 활동 디자이너의 <xref:System.Activities.Activity> 개체를 함께 연결하여 실행 순서를 지정할 수 있습니다. 소스 활동과 대상 활동 사이에 연결을 만들려면 소스 활동 디자이너 위로 마우스를 가져갑니다. 그러면 정사각형 핸들이 양쪽에 나타납니다. 정사각형 핸들 중 하나를 클릭한 후 마우스 단추를 누른 상태에서 핸들 중 하나로 끌어 놓습니다. 대상 활동 위로 마우스를 가져가면 대상 활동 주변에도 이 핸들이 비슷한 방식으로 나타납니다. 마우스 단추를 놓으면 두 활동 간 연결이 만들어지고 소스 디자이너에서 대상 디자이너를 향하는 화살표로 표시됩니다.  
  
### <a name="flowchart-activity-properties"></a>Flowchart 활동 속성  
 다음 표에서는 <xref:System.Activities.Statements.Flowchart> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표 또는 디자이너 화면에서 편집할 수 있습니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|머리글에 활동 디자이너의 표시 이름을 지정합니다. 기본값은 Flowchart입니다. 값을 편집할 수 있습니다 합니다 **속성** 창 또는 활동 디자이너 머리글에서 직접.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|  
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|자식 활동 간에 상태를 공유하기 위해 이 <xref:System.Activities.Statements.Flowchart> 내로 범위가 지정된 변수 컬렉션입니다.|  
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|<xref:System.Activities.Statements.FlowNode>를 시작할 때 실행되는 <xref:System.Activities.Statements.Flowchart>입니다.|  
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|<xref:System.Activities.Statements.FlowNode>에 있는 <xref:System.Activities.Statements.Flowchart> 개체 컬렉션을 포함합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Flowchart](../workflow-designer/flowchart-activity-designers.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)   
 [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)