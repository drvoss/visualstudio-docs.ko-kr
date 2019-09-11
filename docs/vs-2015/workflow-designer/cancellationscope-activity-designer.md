---
title: CancellationScope 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6207d1fcd2e920de979a13624e5cf1b442c2703c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977207"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope 활동 디자이너
합니다 **CancellationScope** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.CancellationScope> 활동입니다.  
  
## <a name="the-cancellationscope-activity"></a>CancellationScope 활동  
 <xref:System.Activities.Statements.CancellationScope> 활동을 사용하여 실행할 활동과 해당 활동에 대한 취소 논리를 지정할 수 있습니다.  
  
### <a name="using-the-cancellationscope-activity-designer"></a>CancellationScope 활동 디자이너 사용  
 **CancellationScope** 활동 디자이너에서 찾을 수 있습니다 합니다 **트랜잭션** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구 상자**  탭의 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **보기** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 **CancellationScope** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면 아무 곳에 나 작업은 일반적으로, 등 배치를 <xref:System.Activities.Statements.Sequence>. 이렇게 하면 기본 <xref:System.Activities.Statements.CancellationScope>인 CancellationScope라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> 헤더의 값을 편집할 수 있습니다 합니다 **CancellationScope** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자.  
  
### <a name="the-cancellationscope-properties"></a>CancellationScope 속성  
 다음 표에서는 <xref:System.Activities.Statements.CancellationScope> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. <xref:System.Activities.Activity.DisplayName%2A> 속성은 속성 표에서 편집할 수 있지만 다른 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면에서 편집해야 합니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> 활동의 선택적 이름입니다. 기본값은 CancellationScope입니다. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|취소 논리가 제공되는 활동을 지정합니다. 추가할를 <xref:System.Activities.Statements.CancellationScope.Body%2A> 활동에서 활동을 **도구 상자** 에 **본문** 상자에 **CancellationScope** "놓기 힌트 텍스트가 있는 활동 디자이너 여기에 작업 "입니다.|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|취소 시 실행할 활동을 지정합니다. 추가할를 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 활동에서 활동을 **도구 상자** 에 **CancellationHandler** 상자에 **CancellationScope** 힌트를 사용 하 여 활동 디자이너 여기에 작업 놓기 "텍스트입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [트랜잭션](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [보정](../workflow-designer/compensate-activity-designer.md)   
 [확인](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)