---
title: FlowDecision 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 46ff7dc7ae79ae8bf269a7a3d3cad780ad7654bb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943365"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision 활동 디자이너
<xref:System.Activities.Statements.FlowDecision> 노드는 지정된 조건이 충족되었는지 여부에 따라 제어 흐름을 두 가지 대안 중 하나로 보내는 분기를 제공하는 조건 노드입니다. 흐름에 두 개 이상의 분기가 필요하면 <xref:System.Activities.Statements.FlowSwitch%601>을 대신 사용합니다.  
  
## <a name="the-flowdecision-node"></a>FlowDecision 노드  
 흐름이 두 경로로 분기될 수 있는 경우 <xref:System.Activities.Statements.FlowDecision>을 사용합니다. <xref:System.Activities.Statements.FlowDecision> 노드에는 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 또는 <xref:System.Activities.Statements.FlowNode>의 두 가지 결과와 각각 연결된 <xref:System.Activities.Statements.FlowDecision.True%2A>와 <xref:System.Activities.Statements.FlowDecision.False%2A>이 있습니다. <xref:System.Activities.Statements.FlowDecision.Condition%2A>을 평가하고 이 평가의 값으로 <xref:System.Activities.Statements.FlowNode>에서 처리할 다음 번 <xref:System.Activities.Statements.Flowchart>를 결정합니다.  
  
### <a name="using-the-flowdecision-designer"></a>FlowDecision 디자이너 사용  
 **FlowDecision** 디자이너에서 찾을 수 있습니다 합니다 **순서도** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구 상자** 탭의 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **보기** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 **FlowDecision** 디자이너에서 끌 수 있습니다를 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 내에서 화면을 **순서도** 활동 디자이너. 이렇게를 <xref:System.Activities.Statements.FlowDecision> 레이블이 지정 된 **의사 결정** 내에서 <xref:System.Activities.Statements.Flowchart> 활동입니다. 디자이너 위로 마우스와 **True** 하 고 **False** 두 분기에 대 한 정사각형 핸들이 나타납니다.  
  
 위로 끌어 놓은 후는 **FlowDecision** 디자이너와 다른 디자이너를 합니다 **순서도**, 노드를 연결할 수 있습니다 실행 순서를 지정 하는 함께 합니다. 소스 노드 간의 링크를 만드는 (포함 된 **True** 및 **False** 의 분기를 **FlowDecision**) 및 대상 노드를 소스 노드의 디자이너 위로 마우스 및 정사각형 핸들이 양쪽에 나타납니다. 정사각형 핸들 중 하나를 클릭한 후 마우스 단추를 누른 상태에서 핸들 중 하나로 끕니다. 대상 노드 위로 마우스를 가져가면 대상 노드 주변에도 이 핸들이 비슷한 방식으로 나타납니다. 마우스 단추를 놓으면 두 노드 간 연결이 만들어지고 소스 디자이너에서 대상 디자이너를 향하는 화살표로 표시됩니다.  
  
 명시 하는 식을 합니다 <xref:System.Activities.Statements.FlowDecision.Condition%2A> 에 입력할 수 있습니다 합니다 **조건** 상자는 **속성** 힌트 텍스트를 "VB 식 입력" 이라고 표시를 클릭 하 여 창.  
  
### <a name="the-flowdecision-properties"></a>FlowDecision 속성  
 다음 표에서는 <xref:System.Activities.Statements.FlowDecision> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표 또는 디자이너 화면에서 편집할 수 있습니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|흐름 제어의 경로를 결정하는 조건입니다.|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|<xref:System.Activities.Statements.FlowDecision.Condition%2A>이 충족되는 경우의 흐름 제어 경로입니다.|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|<xref:System.Activities.Statements.FlowDecision.Condition%2A>이 충족되지 않는 경우의 흐름 제어 경로입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Flowchart](../workflow-designer/flowchart-activity-designers.md)   
 [Flowchart](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)