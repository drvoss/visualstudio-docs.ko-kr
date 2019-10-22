---
title: FlowSwitch &lt;T &gt; Activity Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 27abb660766a7c04742eca221432af19f05f0d28
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656639"
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch &lt;T &gt; Activity Designer
<xref:System.Activities.Statements.FlowSwitch%601> 활동은 두 개 이상의 대안 분기가 필요할 때 일치 기준에 따라 제어 흐름에 대한 분기를 제공하는 조건 노드입니다. 흐름 분기에 두 경로만 필요한 경우 <xref:System.Activities.Statements.FlowDecision> 활동을 대신 사용합니다.

## <a name="the-flowswitcht-activity"></a>FlowSwitch \<T > 활동
 @No__t_0 작업에는 계산 시 제네릭 매개 변수로 지정 된 *t* 형식의 값을 반환 하는 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 포함 되어 있습니다. 또한 이 활동에는 가능한 계산 결과와 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 개체 집합 간의 고유 매핑을 지정하는 <xref:System.Activities.Statements.FlowNode> 집합도 포함되어 있습니다. 실행 되는 <xref:System.Activities.Statements.FlowNode>는 *t* 형식의 개체가 계산 된 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>의 값과 일치 하는 항목입니다. 일치하는 항목이 없는 case에 대해 선택적으로 <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> case를 제공할 수 있습니다.

### <a name="using-the-flowswitcht-activity-designer"></a>FlowSwitch \<T > 활동 디자이너 사용
 **FlowSwitch \<T >** 활동 디자이너는 **도구 상자**의 **순서도** 범주에 있습니다 .이 범주에 액세스 하려면 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 왼쪽에 있는 **도구 상자** 탭을 클릭 하거나 **도구 모음** 을 선택 합니다. **보기** 메뉴 또는 CTRL + ALT + X.)

 **FlowSwitch \<T >** 활동 디자이너를 **도구 상자** 에서 끌어다 **순서도** 활동 디자이너 내의 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면에 놓을 수 있습니다. 표시 되는 **형식 선택** 창을 사용 하 여 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 평가에서 얻은 형식 (제네릭 매개 변수로 <xref:System.Activities.Statements.FlowSwitch%601>와 연결 된 형식)을 지정 합니다. 이 프로시저는 <xref:System.Activities.Statements.Flowchart> 활동 내에서 **Switch** 이라는 <xref:System.Activities.Statements.FlowSwitch%601> 활동을 만듭니다. "VB 식 입력" 이라는 힌트 텍스트가 표시 되는 위치를 클릭 하 여 **속성** 창의 **식** 상자에 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>를 입력할 수 있습니다.

 **FlowSwitch \<T >** activity designer 위에 마우스를 놓으면 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>를 연결 하는 데 사용 되는 사각형 핸들이 가장자리 주위에 표시 됩니다. **FlowSwitch < T \>** 활동 디자이너와 기타 활동 디자이너를 **순서도**로 끌어 오면 표시 되는 <xref:System.Activities.Activity> 개체를 함께 연결 하 여 실행 순서를 지정할 수 있습니다. @No__t_1와 연결 된 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 중 하나를 만들려면 **> FlowSwitch \<T** 의 경계에 있는 사각형 case 핸들 중 하나를 클릭 하 고 마우스 단추를 누른 상태에서 다음의 비슷한 방식으로 표시 되는 핸들 중 하나로 끕니다. 마우스로 디자이너를 가리킬 때의 대상 활동입니다. 마우스 단추를 놓으면 **FlowSwitch \<T >** 의 화살표가이 사례를 나타내는 대상 디자이너에 표시 됩니다. 이 경우의 기본값은 화살표에 표시 되며 **속성** 창의 **case** 상자에서 편집할 수 있습니다.

### <a name="the-flowswitcht-properties"></a>FlowSwitch \<T > 속성
 다음 표에서는 <xref:System.Activities.Statements.FlowSwitch%601> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표 또는 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필요한 공간|사용 현황|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|실행 경로에서 전환할 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>를 결정하기 위해 계산할 식을 지정합니다.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 계산으로 얻은 가능한 결과와 <xref:System.Activities.Statements.FlowNode> 개체 집합 간의 고유 매핑을 지정합니다.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> 계산이 <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> 개체에 포함된 값 중 하나와 일치하지 않을 경우의 매핑을 지정합니다.|

## <a name="see-also"></a>관련 항목:
 [순서도](../workflow-designer/flowchart-activity-designers.md) [흐름도](../workflow-designer/flowchart-activity-designer.md) [flowdecision 결정](../workflow-designer/flowdecision-activity-designer.md)