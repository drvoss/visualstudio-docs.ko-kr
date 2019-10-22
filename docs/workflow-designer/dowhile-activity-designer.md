---
title: 워크플로 디자이너 DoWhile 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85f8d6c442982fff47a679e8fc2ccc04ee515a9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650521"
---
# <a name="dowhile-activity-designer"></a>DoWhile 활동 디자이너

@No__t_0 작업은 지정 된 조건이 **false**로 평가 될 때까지 <xref:System.Activities.Statements.DoWhile.Body%2A>에 포함 된 활동을 한 번 이상 실행 합니다. 루프 본문에 포함된 활동을 0번 이상 실행해야 할 경우 <xref:System.Activities.Statements.While> 활동을 대신 사용하세요.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Workflow Designer의 DoWhile 속성

다음 표에서는 가장 유용한 <xref:System.Activities.Statements.DoWhile> 작업 속성을 보여 주고 디자이너에서 이러한 속성을 사용 하는 방법을 설명 합니다.

|속성 이름|필요한 공간|사용 현황|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|조건이 **true**인 동안 실행할 작업입니다. @No__t_0 활동을 추가 하려면 도구 상자의 활동을 "여기에 작업 놓기" 힌트 텍스트가 있는 **DoWhile** 활동 디자이너의 **본문** 상자로 끌어 놓습니다.|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|루프를 반복할 때마다 평가할 조건입니다. @No__t_0 설정 하려면 **DoWhile** activity 디자이너의 **조건** 상자 또는 속성 표에 Visual Basic 식을 입력 합니다.|

## <a name="see-also"></a>참조

- [While](../workflow-designer/while-activity-designer.md)
- [제어 흐름](../workflow-designer/control-flow-activity-designers.md)