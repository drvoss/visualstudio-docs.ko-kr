---
title: CompensableActivity 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f11743e0027866fd45687f716f1989e98020c68e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977289"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity 활동 디자이너
합니다 **CompensableActivity** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.CompensableActivity> 활동입니다.  
  
## <a name="the-compensableactivity-activity"></a>CompensableActivity 활동  
 <xref:System.Activities.Statements.CompensableActivity>는 성공적으로 완료한 후 확인 또는 보정할 수 있는 작업 단위를 정의합니다.  
  
### <a name="using-the-compensableactivity-activity-designer"></a>CompensableActivity 활동 디자이너 사용  
 **CompensableActivity** 활동 디자이너에서 찾을 수 있습니다 합니다 **트랜잭션** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구 상자**  탭의 왼쪽에는 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **뷰** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 **CompensableActivity** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면 아무 곳에 나 작업은 일반적으로, 등 배치를 <xref:System.Activities.Statements.Sequence>. 그러면 기본 <xref:System.Activities.Statements.CompensableActivity>인 CompensableActivity라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> 헤더의 값을 편집할 수 있습니다 합니다 **CompensableActivity** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자.  
  
### <a name="the-compensableactivity-properties"></a>CompensableActivity 속성  
 다음 표에서는 <xref:System.Activities.Statements.CompensableActivity> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. <xref:System.Activities.Activity.DisplayName%2A> 및 <xref:System.Activities.Activity%601.Result%2A> 속성은 속성 표에서 편집할 수 있지만 다른 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면에서 편집해야 합니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CompensableActivity> 활동의 선택적 이름입니다. 기본값은 CompensableActivity입니다.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|<xref:System.Activities.Statements.CompensableActivity>의 반환 값을 지정합니다. 이 속성은 속성 표에서 편집해야 합니다.|  
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|보정, 취소 및 확인 논리를 제공할 활동을 지정합니다. 추가할를 <xref:System.Activities.Statements.CompensableActivity.Body%2A> 활동에서 활동을 **도구 상자** 에 **본문** 상자에 **CompensableActivity** "놓기 힌트 텍스트가 있는 활동 디자이너 여기에 작업 "입니다.|  
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|취소 시 실행할 활동을 지정합니다. 활동을 추가 하려면의 해당 디자이너를 삭제 합니다 **도구 상자** 에 **CancellationHandler** 상자에 **CompensableActivity** "놓기 힌트 텍스트가 있는 활동 디자이너 여기에 작업 "입니다.|  
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|<xref:System.Activities.Statements.CompensableActivity.Body%2A> 활동을 보정할 때 실행할 활동을 지정합니다. <xref:System.Activities.Statements.Compensate> 활동을 사용하여 이 처리기를 명시적으로 호출할 수 있습니다.<br /><br /> 활동을 추가 하려면 해당 활동 디자이너를 삭제 합니다 **도구 상자** 에 **CompensationHandler** 상자에 **CompensableActivity** 힌트 텍스트가 있는 활동 디자이너 " 여기에 작업 놓기 "입니다.|  
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|<xref:System.Activities.Statements.CompensableActivity.Body%2A> 활동을 확인할 때 실행할 활동을 지정합니다. <xref:System.Activities.Statements.Confirm> 활동을 사용하여 이 처리기를 명시적으로 호출할 수 있습니다.<br /><br /> 활동을 추가 하려면 해당 활동 디자이너를 삭제 합니다 **도구 상자** 에 **ConfirmationHandler** 상자에 **CompensableActivity** 힌트 텍스트가 있는 활동 디자이너 " 여기에 작업 놓기 "입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [트랜잭션](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [보정](../workflow-designer/compensate-activity-designer.md)   
 [확인](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)