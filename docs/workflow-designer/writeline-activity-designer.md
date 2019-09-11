---
title: 워크플로 디자이너-WriteLine 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17dd6e3c617749d82533d8bccb7f0caaa073ac26
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838622"
---
# <a name="writeline-activity-designer"></a>WriteLine 활동 디자이너

합니다 **WriteLine** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.WriteLine> 활동입니다.

## <a name="the-writeline-activity"></a>WriteLine 활동

<xref:System.Activities.Statements.WriteLine> 활동은 지정된 <xref:System.IO.TextWriter> 개체에 텍스트를 씁니다. 지정된 <xref:System.IO.TextWriter>가 없는 경우 <xref:System.Activities.Statements.WriteLine>은 콘솔에 텍스트를 씁니다.

### <a name="using-the-writeline-activity-designer"></a>WriteLine 활동 디자이너 사용

액세스는 **WriteLine** 에서 활동 디자이너를 **기본형** 범주의 **도구 상자**. **WriteLine** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 작업은 일반적으로, 등 배치 위치는 워크플로 디자이너 화면에 끌어 놓 및를 <xref:System.Activities.Statements.Sequence>합니다. 그러면 기본 <xref:System.Activities.Statements.WriteLine>인 WriteLine이라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에서 편집할 수 있습니다 합니다 **WriteLine** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자.

### <a name="the-writeline-properties"></a>WriteLine 속성

다음 표에서는 <xref:System.Activities.Statements.WriteLine> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있습니다 하 고 그 중 일부는 워크플로 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.WriteLine> 활동의 이름입니다. 기본값은 WriteLine입니다. <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|쓸 텍스트입니다. 속성을 설정 하려면 Visual Basic 식을 입력 합니다 **텍스트** 상자에 **WriteLine** 활동 디자이너나 속성 표의 합니다.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter>이 <xref:System.Activities.Statements.WriteLine>를 쓸 대상 <xref:System.Activities.Statements.WriteLine.Text%2A>입니다. 기본값은 콘솔입니다.|

## <a name="see-also"></a>참고자료

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)