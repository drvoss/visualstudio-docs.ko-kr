---
title: TransactionScope 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: abed15a1ce3d406cfd5e95318dd332a677f61095
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976547"
---
# <a name="transactionscope-activity-designer"></a>TransactionScope 활동 디자이너
합니다 **TransactionScope** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.TransactionScope> 활동입니다.  
  
## <a name="the-transactionscope-activity"></a>TransactionScope 활동  
 <xref:System.Activities.Statements.TransactionScope> 활동은 단일 트랜잭션에 포함된 활동을 실행합니다. 해당 트랜잭션의 <xref:System.Activities.Statements.TransactionScope.Body%2A> 활동 및 다른 모든 참가자가 성공적으로 완료되면 트랜잭션이 커밋됩니다.  
  
### <a name="using-the-transactionscope-activity-designer"></a>TransactionScope 활동 디자이너 사용  
 **TransactionScope** 활동 디자이너에서 찾을 수 있습니다 합니다 **트랜잭션** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구 상자 ** 탭의 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **뷰** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 **TransactionScope** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면 아무 곳에 나 작업은 일반적으로, 등 배치를 <xref:System.Activities.Statements.Sequence>. 그러면 기본 <xref:System.Activities.Statements.TransactionScope>인 TransactionScope라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> 헤더의 값을 편집할 수 있습니다 합니다 **TransactionScope** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자.  
  
### <a name="the-transactionscope-properties"></a>TransactionScope 속성  
 다음 표에서는 <xref:System.Activities.Statements.TransactionScope> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. <xref:System.Activities.Activity.DisplayName%2A> 및 <xref:System.Activities.Statements.TransactionScope.Body%2A> 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면에서 편집할 수 있습니다. 그러나 다른 속성은 속성 표에서 편집해야 합니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TransactionScope> 활동의 선택적 이름입니다. 기본값은 TransactionScope입니다. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|단일 트랜잭션에서 실행할 활동을 지정합니다. 추가할를 <xref:System.Activities.Statements.TransactionScope.Body%2A> 활동에서 활동을 **도구 상자** 에 **본문** 상자에 **TransactionScope** 활동 디자이너를 "드롭 작업 힌트 텍스트가 있는 여기에 "입니다.|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|이 <xref:System.Transactions.IsolationLevel>의 <xref:System.Activities.Statements.TransactionScope>을 지정합니다.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|트랜잭션을 완료해야 하는 시간 간격(시:분:초를 의미하는 00:00:00 형식)을 지정합니다. 기본값은 1분입니다(00:01:00).|  
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|True|트랜잭션이 중단되면 워크플로를 중단할지 여부를 나타내는 값을 지정합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [트랜잭션](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [보정](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)