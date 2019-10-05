---
title: TerminateWorkflow 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b471cee4a07722e37ae4b58817823dd4fa48ee26
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004435"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow 활동 디자이너
합니다 **TerminateWorkflow** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.TerminateWorkflow> 활동입니다.  
  
## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow 활동  
 <xref:System.Activities.Statements.TerminateWorkflow> 활동은 워크플로의 실행을 종료합니다.  
  
### <a name="using-the-terminateworkflow-activity-designer"></a>TerminateWorkflow 활동 디자이너 사용  
 **TerminateWorkflow** 활동 디자이너에서 찾을 수 있습니다는 **런타임** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구상자** 탭 (또는 선택할 **도구 상자** 에서 합니다 **보기** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 **TerminateWorkflow** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면 아무 곳에 나 작업은 일반적으로, 등 배치를 <xref:System.Activities.Statements.Sequence>. 이렇게를 <xref:System.Activities.Statements.TerminateWorkflow> 기본값을 사용 하 여 활동 **DisplayName** TerminateWorkflow입니다. <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에서 편집할 수 있습니다 합니다 **TerminateWorkflow** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자.  
  
### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow 속성  
 다음 표에서는 <xref:System.Activities.Statements.TerminateWorkflow> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면에서 편집할 수 있습니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TerminateWorkflow> 활동의 이름입니다. 기본값은 TerminateWorkflow입니다. 표시 이름이 꼭 필요하지 않더라도 표시 이름을 사용하는 것이 좋습니다.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|워크플로가 종료될 때 throw할 예외입니다. 이 속성은 속성 표에서 설정합니다.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|워크플로가 왜 종료되었는지 설명하는 이유입니다. 이 속성은 속성 표에서 설정합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [런타임](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)