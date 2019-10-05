---
title: While 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 36752df3d8ffbf33b8ea95570d6a4efe8c8cd3be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855406"
---
# <a name="while-activity-designer"></a>While 활동 디자이너

합니다 <xref:System.Activities.Statements.While> 활동 실행에 포함 된 해당 <xref:System.Activities.Statements.While.Body%2A> 지정 된 조건이 평가 되는 동안 **true**합니다. 포함된 활동이 실행되지 않을 수도 있습니다. 포함된 활동이 적어도 한 번은 실행되도록 하려면 그 대신 <xref:System.Activities.Statements.DoWhile> 활동을 사용하세요.

## <a name="while-properties-in-workflow-designer"></a>Workflow Designer의 While 속성

다음 표에서는 가장 유용한 <xref:System.Activities.Statements.While> 활동 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|사용|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|머리글에 <xref:System.Activities.Statements.While> 활동 디자이너의 이름을 지정합니다. 기본값은 While입니다. 값을 편집할 수 있습니다 합니다 **속성** 창 또는 활동 디자이너 머리글에서 직접.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.While.Body%2A>|False|활동 실행을 포함 하는 동안 합니다 <xref:System.Activities.Statements.While.Condition%2A> 로 평가 **true**합니다.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]의 활동을 실행할지 여부를 결정하기 위해 평가하는 <xref:System.Activities.Statements.While.Body%2A> 식을 포함합니다.|

## <a name="see-also"></a>참고자료

- [제어 흐름](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)