---
title: 워크플로 디자이너-DoWhile 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0069d352897d2d98288988d549d9733a39b2c35
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949736"
---
# <a name="dowhile-activity-designer"></a>DoWhile 활동 디자이너

<xref:System.Activities.Statements.DoWhile> 활동 실행에 포함 된 해당 <xref:System.Activities.Statements.DoWhile.Body%2A> 최소한 한 번에 지정된 된 조건이 평가 될 때까지 **false**합니다. 루프 본문에 포함된 활동을 0번 이상 실행해야 할 경우 <xref:System.Activities.Statements.While> 활동을 대신 사용하세요.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Workflow Designer의 DoWhile 속성

다음 표에서 가장 유용한 <xref:System.Activities.Statements.DoWhile> 활동 속성을 디자이너에서 사용 하는 방법을 설명 합니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|조건은 하는 동안 실행할 활동입니다 **true**합니다. 추가할를 <xref:System.Activities.Statements.DoWhile.Body%2A> 활동을 도구 상자에서 활동을 **본문** 상자에 **DoWhile** 여기에 작업 놓기 "힌트 텍스트가 있는 활동 디자이너.|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|루프를 반복할 때마다 평가할 조건입니다. 설정 하는 <xref:System.Activities.Statements.DoWhile.Condition%2A>, Visual Basic 식을 입력 합니다 **조건** 상자에 **DoWhile** 활동 디자이너나 속성 표의.|

## <a name="see-also"></a>참고자료

- [While](../workflow-designer/while-activity-designer.md)
- [제어 흐름](../workflow-designer/control-flow-activity-designers.md)