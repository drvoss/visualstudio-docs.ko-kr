---
title: InvokeMethod 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 61398efe1849c6038e13a68ae3b2e2f5f80f1d5d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952011"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod 활동 디자이너
**InvokeMethod** 디자이너 만들기 및 구성 되는 <xref:System.Activities.Statements.InvokeMethod> 활동입니다.  
  
## <a name="the-invokemethod-activity"></a>InvokeMethod 활동  
 <xref:System.Activities.Statements.InvokeMethod>는 지정한 개체 또는 형식의 public 메서드를 호출합니다.  
  
### <a name="using-the-invokemethod-activity-designer"></a>InvokeMethod 활동 디자이너 사용  
 **InvokeMethod** 활동 디자이너에서 찾을 수 있습니다는 **기본형** 범주의 **도구 상자**, 클릭 하 여 액세스를 **도구상자** 탭 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 합니다 **뷰** 메뉴 또는 CRTL + ALT + X를 누릅니다.)  
  
 **InvokeMethod** 활동 디자이너에서 끌 수 있습니다를 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 노출 곳은 일반적으로 등 활동을 배치 내로 <xref:System.Activities.Statements.Sequence>합니다. 그러면 기본 <xref:System.Activities.Statements.InvokeMethod>인 InvokeMethod라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에서 편집할 수 있습니다 합니다 **InvokeMethod** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자.  
  
### <a name="the-invokemethod-properties"></a>InvokeMethod 속성  
 다음 표에서는 <xref:System.Activities.Statements.InvokeMethod> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 디자이너 화면에서 편집할 수 있습니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeMethod> 활동의 이름입니다. 기본값은 InvokeMethod입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|작업이 실행될 때 호출할 메서드의 이름입니다. 호출된 된 메서드에서 선언 해야 합니다 **공용**합니다. 이 속성은 디자이너 화면에서 편집할 수 있습니다. 이 속성은 필수 속성입니다.|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|호출되는 메서드의 매개 변수 컬렉션입니다. 메서드 시그니처에 표시되는 것과 동일한 순서대로 컬렉션에 매개 변수를 추가해야 합니다. 속성 눈금에서 줄임표 단추를 클릭 합니다 **매개 변수** 표시 필드를 **매개 변수** 대화 상자를이 속성을 설정할 수 있습니다. 클릭 합니다 **인수 만들기** 단추 매개 변수를 추가 합니다.|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|메서드 호출의 반환 값입니다.|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|메서드가 비동기적으로 호출되는지 여부를 지정합니다. 기본값은 **False**합니다.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|호출할 메서드가 포함된 개체입니다. 이 속성은 디자이너 화면에서 편집할 수 있습니다.<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 또는 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>을 설정해야 합니다.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>의 형식입니다. 이 속성은 디자이너 화면에서 편집할 수 있습니다. 이 속성은 호출된 메서드가 정적인 경우에만 설정해야 합니다.|  
  
 매개 변수를 전달 하는 C# **아웃** 매개 변수 (예를 들어 `Method1(out myParam)),` 사용할지 **OutArgument** 대신 **InOutArgument**  
  
 메서드 호출 인수를 사용 하 여 **TargetObject** 또는 **결과** 사용 하 여 호출할 수 없습니다는 <xref:System.Activities.Statements.InvokeMethod> 활동입니다. 그 이유는 <xref:System.Activities.Statements.InvokeMethod> 활동이 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 및 <xref:System.Activities.Statements.InvokeMethod.Result%2A>를 <xref:System.Activities.Activity.CacheMetadata%2A>에 등록하기 때문입니다.  
  
 <xref:System.Activities.Activity.CacheMetadata%2A>에 매개 변수를 등록하는 알고리즘이 다음 목록에 나와 있습니다.  
  
1. <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 인수를 등록합니다.  
  
2. <xref:System.Activities.Statements.InvokeMethod.Result%2A> 인수를 등록합니다.  
  
3. <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> 컬렉션을 반복하고 각 인수를 등록합니다.  
  
   예외가 발생 합니다 형식의 <xref:System.Activities.InvalidWorkflowException> 다음 메시지와 함께 합니다. 'InvokeMethod': 이름이 ''를 사용 하 여 변수를 RuntimeArgument 또는 DelegateArgument를을 이미 존재합니다. 이름은 환경 범위 내에서 고유해야 합니다.  
  
   <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> 및 <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>는 워크플로 인수가 아니고 따라서 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> 메서드에서 <xref:System.Activities.Statements.InvokeMethod> 활동의 <xref:System.Activities.Activity.CacheMetadata%2A> 컬렉션에 등록되어 있지 않기 때문에 이러한 제한이 적용되지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [기본 형식](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [지연](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)