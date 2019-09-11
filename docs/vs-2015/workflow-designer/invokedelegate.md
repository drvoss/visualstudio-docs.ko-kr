---
title: InvokeDelegate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30281d8cd5d5ed94ed89a980006f9618292a778d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951972"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** 디자이너 만들기 및 구성 되는 <xref:System.Activities.Statements.InvokeDelegate> 활동.

## <a name="the-invokedelegate-activity"></a>InvokeDelegate 활동

<xref:System.Activities.Statements.InvokeDelegate>는 public 대리자를 호출합니다.

### <a name="using-the-invokedelegate-activity-designer"></a>InvokeDelegate 활동 디자이너 사용

**InvokeDelegate** 활동 디자이너에서 찾을 수 있습니다는 **기본형** 범주의 **도구 상자**, 클릭 하 여 액세스를 **도구상자** 탭 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 합니다 **뷰** 메뉴 또는 CRTL + ALT + X를 누릅니다.)

**InvokeDelegate** 활동 디자이너에서 끌 수 있습니다를 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 노출 곳은 일반적으로 등 활동을 배치 내로 <xref:System.Activities.Statements.Sequence>합니다. 그러면 기본 <xref:System.Activities.Statements.InvokeDelegate>인 InvokeDelegate라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에서 편집할 수 있습니다 합니다 **InvokeDelegate** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자.

### <a name="the-invokedelegate-properties"></a>InvokeDelegate 속성

다음 표에서는 <xref:System.Activities.Statements.InvokeDelegate> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.InvokeDelegate> 활동의 이름입니다. 기본값은 InvokeDelegate입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|작업이 실행될 때 호출할 <xref:System.Activities.ActivityDelegate>의 이름입니다. 이 속성은 디자이너 화면에서 편집할 수 있습니다. 이 속성은 필수 속성입니다.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|호출한 대리자의 인수 컬렉션입니다. 키는 <xref:System.Activities.DelegateArgument>에 대한 <xref:System.Activities.ActivityDelegate> 개체의 이름이고 값은 식이 평가되고 해당 <xref:System.Activities.DelegateArgument> 개체에 할당되는 인수입니다. 속성 눈금에서 줄임표 단추를 클릭 합니다 **DelegateArguments** 표시 필드를 **DelegateArguments** 대화 상자를이 속성을 설정할 수 있습니다. 클릭 합니다 **인수 만들기** 필드는 인수를 추가 합니다.|

## <a name="see-also"></a>참고자료

- [방법: 워크플로 디자이너에서 활동 대리자 정의 및 사용](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)