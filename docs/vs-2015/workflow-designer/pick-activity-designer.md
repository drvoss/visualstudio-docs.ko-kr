---
title: Pick 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 15320289c3f668f2bc0a84d9653110d02536a32e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694506"
---
# <a name="pick-activity-designer"></a>Pick 활동 디자이너
<xref:System.Activities.Statements.Pick> 활동은 이벤트 기반의 제어 흐름을 제공합니다. 이 활동은 트리거를 시작하는 이벤트에 대해 몇 가지 분기 중 하나를 실행합니다.  
  
## <a name="the-pick-activity"></a>Pick 활동  
 <xref:System.Activities.Statements.Pick> 활동에는 <xref:System.Activities.Statements.PickBranch> 개체 컬렉션이 포함되어 있는데, <xref:System.Activities.Statements.Pick> 활동은 트리거 역할을 하는 들어오는 이벤트로 이러한 개체 중 하나를 실행할 수 있습니다. 이러한 방식으로 [!INCLUDE[wfd1](../includes/wfd1-md.md)]는 이벤트 기반 제어 흐름 모델링을 제공합니다. 각 <xref:System.Activities.Statements.PickBranch>에는 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 및 <xref:System.Activities.Statements.PickBranch.Action%2A>이 포함되어 있습니다. <xref:System.Activities.Statements.Pick> 활동을 실행하기 시작할 때 <xref:System.Activities.Statements.PickBranch> 요소의 트리거 활동이 모두 예약됩니다. 첫 번째 활동이 완료되면 해당 동작 작업이 예약되고 다른 트리거 활동은 모두 취소됩니다.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Pick 활동 디자이너를 사용하는 방법  
 **선택** 활동 디자이너에서 찾을 수 있습니다 합니다 **제어 흐름** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구상자**탭 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **보기** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 **선택** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면의 아무 곳에 나 활동 디자이너 일반적으로 배치 하는 내부를  **시퀀스** 활동 디자이너입니다. [!INCLUDE[wfd2](../includes/wfd2-md.md)]에 끌어 놓으면 <xref:System.Activities.Statements.Pick> 활동이 만들어집니다. 이 활동에는 기본적으로 빈 <xref:System.Activities.Statements.PickBranch> 활동 두 개가 요소(표시 이름 Branch1 및 Bracnh2)로 포함되어 있습니다. 이러한 각 <xref:System.Activities.Statements.PickBranch.DisplayName%2A> 속성 값을 편집할 수 있습니다 합니다 **PickBranch** 활동 디자이너 머리글 또는 합니다 **속성** 각 분기에 대 한 창.  
  
 추가 하는 방법은 두 가지가 <xref:System.Activities.Statements.PickBranch> 활동의 컬렉션을를 <xref:System.Activities.Statements.Pick> 개체: 끌어서 놓기 합니다 **PickBranch** 에서 디자이너를 **도구 상자** 또는에서 상황에 맞는 메뉴를 사용 하 여 내 합니다 **선택** 디자인 화면입니다. 자세한 내용은 참조는 [PickBranch](../workflow-designer/pickbranch-activity-designer.md) 항목입니다. 내부 표시는 유일한 항목에 배치할 수는 **선택** activity designer가는 **PickBranch** 활동 디자이너입니다.  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>Workflow Designer의 Pick 활동 속성  
 다음 표에서는 <xref:System.Activities.Statements.Pick> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표 또는 디자이너 화면에서 편집할 수 있습니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|머리글에 <xref:System.Activities.Statements.Pick> 활동 디자이너의 이름을 지정합니다. 기본값은 Pick입니다. 속성 표에서 또는 활동 디자이너의 머리글에서 직접 값을 편집할 수 있습니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|  
  
## <a name="see-also"></a>참고 항목  
 [제어 흐름](../workflow-designer/control-flow-activity-designers.md)   
 [선택 활동](https://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [Pick 작업 사용](https://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)