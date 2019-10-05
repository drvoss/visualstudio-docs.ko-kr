---
title: ForEach&lt;T&gt; 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 97732b92c5a90334917ad4e74667f88d605b647d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943292"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; 활동 디자이너
<xref:System.Activities.Statements.ForEach%601> 활동은 지정된 <xref:System.Activities.Statements.ForEach%601.Body%2A> 컬렉션의 각 항목에 대해 <xref:System.Activities.Statements.ForEach%601.Values%2A>에 포함된 활동을 실행합니다.  
  
## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach\<T > 워크플로 디자이너의 속성  
 다음 표에서는 가장 유용한 <xref:System.Activities.Statements.ForEach%601> 활동 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ForEach%601> 활동의 이름입니다. 기본값은 ForEach\<Int32 >. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|반복할 항목의 컬렉션입니다. 설정 하는 <xref:System.Activities.Statements.ForEach%601.Values%2A>, 입력 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 식에는 **값** 상자에 **ForEach\<T >** 활동 디자이너나 속성 표의.|  
|*TypeArgument*|True|항목의 형식 합니다 <xref:System.Activities.Statements.ForEach%601.Values%2A> 제네릭 매개 변수로 지정 된 컬렉션 *T*합니다. 기본적으로 *TypeArgument* 로 설정 된 **Int32**합니다. 유형을 변경 하려면 값을 변경 합니다 *TypeArgument* 속성 표의 콤보 상자입니다.|  
  
 기본적으로 루프 반복기 라고 **항목**합니다. <xref:System.Activities.Statements.ForEach%601> 활동 디자이너에서 반복기 변수의 이름을 변경할 수 있습니다. 루프 반복기는 <xref:System.Activities.Statements.ForEach%601> 활동의 자식에 포함된 식에서 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [제어 흐름](../workflow-designer/control-flow-activity-designers.md)