---
title: 워크플로 디자이너-InvokeMethod 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eed5d81cce05b316ef7593639e868936e7f2fa69
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62537643"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod 활동 디자이너

**InvokeMethod** 디자이너 만들기 및 구성 되는 <xref:System.Activities.Statements.InvokeMethod> 활동입니다.

## <a name="the-invokemethod-activity"></a>InvokeMethod 활동

<xref:System.Activities.Statements.InvokeMethod>는 지정한 개체 또는 형식의 public 메서드를 호출합니다.

### <a name="use-the-invokemethod-activity-designer"></a>InvokeMethod 활동 디자이너 사용

액세스는 **InvokeMethod** 에서 활동 디자이너를 **기본형** 범주의 **도구 상자**. **InvokeMethod** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 작업은 일반적으로, 등 배치 하는 때에 있는 Workflow Designer 화면에 끌어 놓 및를 <xref:System.Activities.Statements.Sequence>. Activity designer 만들어집니다는 <xref:System.Activities.Statements.InvokeMethod> 기본값을 사용 하 여 작업 <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod입니다. <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에서 편집할 수 있습니다 합니다 **InvokeMethod** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자.

### <a name="the-invokemethod-properties"></a>InvokeMethod 속성

다음 표는 <xref:System.Activities.Statements.InvokeMethod> 속성 디자이너에서 사용 하는 방법을 설명 합니다. 이러한 속성은 속성 표에서 편집할 수 있습니다 하 고 일부는 워크플로 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeMethod> 활동의 이름입니다. 기본값은 InvokeMethod입니다.<br /><br /> 하지만 <xref:System.Activities.Activity.DisplayName%2A> 은 꼭 필요 하지 하나를 사용 하는 것이 좋습니다.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|작업이 실행될 때 호출할 메서드의 이름입니다. 호출된 된 메서드에서 선언 해야 합니다 **공용**합니다. 이 속성에는 디자이너 화면에서 편집할 수 있습니다 이며 필수입니다.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|호출되는 메서드의 매개 변수 컬렉션입니다. 메서드 시그니처에 표시되는 것과 동일한 순서대로 컬렉션에 매개 변수를 추가해야 합니다. 표시할 합니다 **매개 변수** 이 속성을 설정할 수 있는 대화 상자에서 줄임표 단추를 클릭 합니다 **매개 변수** 속성 그리드의 필드입니다. 클릭 합니다 **인수 만들기** 단추 매개 변수를 추가 합니다.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|메서드 호출의 반환 값입니다.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|메서드가 비동기적으로 호출되는지 여부를 지정합니다. 기본값은 **False**합니다.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|호출할 메서드가 포함된 개체입니다. 이 속성은 디자이너 화면에서 편집할 수 있습니다.<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 또는 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>을 설정해야 합니다.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>의 형식입니다. 이 속성은 디자이너 화면에서 편집할 수 있습니다. 이 속성은 호출된 메서드가 정적인 경우에만 설정해야 합니다.|

매개 변수를 전달 하는 C# **아웃** 매개 변수 (예를 들어 `Method1(out myParam))`를 사용 하 여 **OutArgument** 대신 **InOutArgument**

메서드 호출 인수를 사용 하 여 **TargetObject** 또는 **결과** 사용 하 여 호출할 수 없습니다는 <xref:System.Activities.Statements.InvokeMethod> 활동입니다. 그 이유는 <xref:System.Activities.Statements.InvokeMethod> 활동이 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 및 <xref:System.Activities.Statements.InvokeMethod.Result%2A>를 <xref:System.Activities.Activity.CacheMetadata%2A>에 등록하기 때문입니다.

<xref:System.Activities.Activity.CacheMetadata%2A>에 매개 변수를 등록하는 알고리즘이 다음 목록에 나와 있습니다.

1. <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> 인수를 등록합니다.

2. <xref:System.Activities.Statements.InvokeMethod.Result%2A> 인수를 등록합니다.

3. <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> 컬렉션을 반복하고 각 인수를 등록합니다.

예외가 발생 합니다 형식의 <xref:System.Activities.InvalidWorkflowException> 다음 메시지와 함께 합니다. 'InvokeMethod': 이름이 ''를 사용 하 여 변수를 RuntimeArgument 또는 DelegateArgument를을 이미 존재합니다. 이름은 환경 범위 내에서 고유해야 합니다.

이 제한에 적용 되지 않습니다 <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> 고 <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>입니다. 워크플로 인수가 아닙니다 하며에 등록 되지 않습니다는 <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> 의 컬렉션을 <xref:System.Activities.Statements.InvokeMethod> 활동에서를 <xref:System.Activities.Activity.CacheMetadata%2A> 메서드.

## <a name="see-also"></a>참고자료

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)