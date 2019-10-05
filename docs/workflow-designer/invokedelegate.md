---
title: 워크플로 디자이너-InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 511d73ea2992887f31bc8750cc9ba32934bddd91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62537090"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** 디자이너 만들기 및 구성 되는 <xref:System.Activities.Statements.InvokeDelegate> 활동.

## <a name="the-invokedelegate-activity"></a>InvokeDelegate 활동

<xref:System.Activities.Statements.InvokeDelegate>는 public 대리자를 호출합니다.

### <a name="use-the-invokedelegate-activity-designer"></a>InvokeDelegate 활동 디자이너 사용

액세스는 **InvokeDelegate** 에서 활동 디자이너를 **기본형** 범주의 **도구 상자**. **InvokeDelegate** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 작업은 일반적으로, 등 배치 하는 때에 있는 Workflow Designer 화면에 끌어 놓 및를 <xref:System.Activities.Statements.Sequence>. Activity designer 만들어집니다는 <xref:System.Activities.Statements.InvokeDelegate> 기본값을 사용 하 여 작업 <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate입니다. <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에서 편집할 수 있습니다 합니다 **InvokeDelegate** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자.

### <a name="the-invokedelegate-properties"></a>InvokeDelegate 속성

다음 표에서는 <xref:System.Activities.Statements.InvokeDelegate> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있습니다 하 고 일부는 워크플로 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeDelegate> 활동의 이름입니다. 기본값은 InvokeDelegate입니다.<br /><br /> 하지만 <xref:System.Activities.Activity.DisplayName%2A> 은 꼭 필요 하지 하나를 사용 하는 것이 좋습니다.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|작업이 실행될 때 호출할 <xref:System.Activities.ActivityDelegate>의 이름입니다. 이 속성에는 디자이너 화면에서 편집할 수 있습니다 이며 필수입니다.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|호출한 대리자의 인수 컬렉션입니다. 키 매개 변수 개체의 이름에는 <xref:System.Activities.ActivityDelegate>, 값은 인수 식에서 해당 평가 되 고 해당 매개 변수 개체에 할당 합니다. 표시할 합니다 **DelegateArguments** 이 속성을 설정할 수 있는 대화 상자에서 줄임표 단추를 클릭 합니다 **DelegateArguments** 속성 그리드의 필드입니다. 클릭 합니다 **인수 만들기** 필드는 인수를 추가 합니다.|

## <a name="see-also"></a>참고자료

- [방법: 워크플로 디자이너에서 활동 대리자 정의 및 사용](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)