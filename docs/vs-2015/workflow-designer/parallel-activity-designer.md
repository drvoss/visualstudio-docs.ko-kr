---
title: Parallel 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 627a99fec632871b815904abd798c0e4bbfd6505
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971344"
---
# <a name="parallel-activity-designer"></a>Parallel 활동 디자이너
<xref:System.Activities.Statements.Parallel> 활동은 자식 활동 컬렉션을 동시에 실행합니다.  
  
## <a name="the-parallel-activity"></a>Parallel 활동  
 <xref:System.Activities.Statements.Parallel> 활동은 자식 활동을 <xref:System.Activities.Statements.Parallel.Branches%2A> 컬렉션에 저장합니다. 일부 자식 활동이 유휴 상태가 될 수 있는 경우에는 <xref:System.Activities.Statements.Parallel> 활동 대신 <xref:System.Activities.Statements.Sequence> 활동을 사용합니다.  
  
 <xref:System.Activities.Statements.Parallel> 활동에는 사용자가 지정한 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 식이 포함된 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 속성이 있습니다. <xref:System.Activities.Statements.Parallel> 활동은 각 분기가 완료된 후 이 속성을 평가합니다. 로 평가 되 면 **True**, 그런 다음 <xref:System.Activities.Statements.Parallel> 다른 분기를 실행 하지 않고 작업을 완료 합니다. 경우는 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 계산 되지 않습니다 **True**, 해당 <xref:System.Activities.Statements.Parallel> 모든 자식 활동이 완료 되 면 활동이 완료 합니다.  
  
### <a name="using-the-parallel-activity-designer"></a>Parallel 활동 디자이너 사용  
 **병렬** 활동 디자이너에서 찾을 수 있습니다 합니다 **제어 흐름** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구상자**탭의 왼쪽에는 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **보기** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 합니다 **병렬** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면 아무 곳에 나 활동 디자이너는 일반적으로 놓인, 예를 들어를 **시퀀스** 활동 디자이너입니다. 에 삭제 한 후는 [!INCLUDE[wfd2](../includes/wfd2-md.md)]를 만들면를 <xref:System.Activities.Statements.Parallel> 기본적으로 포함 하는 작업을 <xref:System.Activities.Activity.DisplayName%2A> 의 **병렬**  
  
 활동을 추가 하는 <xref:System.Activities.Statements.Parallel.Branches%2A> 병렬 활동의 컬렉션에서 다른 활동 디자이너를 끌어를 **도구 상자** 삼각형 안에 놓습니다를 **병렬** 활동 디자이너입니다. 이 삼각형은 분기에 포함된 활동 옆에 표시됩니다. 이 절차를 반복하여 다른 활동을 추가할 수 있습니다. 끌어서 놓는 내에서 작업을 다시 정렬할 수 있습니다 합니다 **병렬** 활동 디자이너입니다.  
  
### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Workflow Designer의 Parallel 활동 속성  
 다음 표에서는 가장 유용한 Parallel 활동 속성을 보여 주고 디자이너에서 이러한 속성을 사용하는 방법을 설명합니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|머리글에 활동 디자이너의 표시 이름을 지정합니다. 기본값은 **병렬**합니다. 값을 선택적으로 편집할 수 있습니다 합니다 **속성** 표에서 또는 활동 디자이너 머리글에서 직접.|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|실행할 자식 활동의 컬렉션을 포함합니다.|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|분기가 완료된 후 확인됩니다. 로 평가 되 면 **True**, 예약 된 보류 중인 분기가 취소 됩니다. 이 속성이 설정 되지 않았거나를 평가 하는 경우 **False**, 모든 자식 활동이 완료 되 면 작업 완료 합니다. 기본값은 **null**합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [시퀀스](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [제어 흐름](../workflow-designer/control-flow-activity-designers.md)