---
title: 활동 디자이너를 지연 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 528317a97a9b2582442dacfcf9ba8a35943736e8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976705"
---
# <a name="delay-activity-designer"></a>Delay 활동 디자이너
합니다 **지연** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.Delay> 활동입니다.  
  
## <a name="the-delay-activity"></a>Delay 활동  
 <xref:System.Activities.Statements.Delay> 활동은 지정된 시간 동안 워크플로 실행을 지연시킵니다.  
  
### <a name="using-the-delay-activity-designer"></a>Delay 활동 디자이너 사용  
 **지연** 활동 디자이너에서 찾을 수 있습니다를 **기본형** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구상자**탭의 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **보기** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 **지연** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면 아무 곳에 나 작업은 일반적으로, 등 배치를 <xref:System.Activities.Statements.Sequence>. 그러면 기본 <xref:System.Activities.Statements.Delay>인 Delay라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에서 편집할 수 있습니다 합니다 **지연** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자.  
  
### <a name="the-delay-properties"></a>Delay 속성  
 다음 표에서는 <xref:System.Activities.Statements.Delay> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 디자이너 화면에서 편집할 수 있습니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Delay> 활동의 이름입니다. 기본값은 Delay입니다. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|워크플로를 지연할 시간입니다. 이 속성은 속성 표에서 설정합니다. 리터럴 <xref:System.TimeSpan>을 00:00:00 형식으로 입력하거나 Visual Basic 식을 입력하여 시간을 지정합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [기본 형식](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay 활동 디자이너](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)