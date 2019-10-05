---
title: CorrelationScope 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 95c8422d53903c3c7b81db9f6ef042c5ea9ff1c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976762"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope 활동 디자이너
**CorrelationScope** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.ServiceModel.Activities.CorrelationScope> 사용 하 여 자식 메시징 활동을 암시적으로 관리 하는 작업을 <xref:System.ServiceModel.Activities.CorrelationHandle> 개체입니다.  
  
## <a name="the-correlationscope-activity"></a>CorrelationScope 활동  
 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 속성은 자식 메시징 활동을 관리하는 데 사용되는 <xref:System.ServiceModel.Activities.CorrelationHandle>을 지정합니다. <xref:System.ServiceModel.Activities.Send>에 포함된 <xref:System.ServiceModel.Activities.Receive> 및 <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> 활동은 해당 활동을 포함하는 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> 활동의 <xref:System.ServiceModel.Activities.CorrelationScope> 속성을 사용하여 상호 연결을 수행하도록 구성됩니다.  
  
### <a name="using-the-correlationscope-activity-designer"></a>CorrelationScope 활동 디자이너 사용  
 **CorrelationScope** 활동 디자이너에서 찾을 수 있습니다는 **메시징** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구상자** 탭의 왼쪽에는 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **뷰** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 **CorrelationScope** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면. 이렇게를 <xref:System.ServiceModel.Activities.CorrelationScope> 기본값을 사용 하 여 활동 **DisplayName** CorrelationScope입니다. <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에서 편집할 수 있습니다 합니다 **CorrelationScope** 활동 디자이너 또는 합니다 **DisplayName** 상자를 **속성** 창.  
  
 지정 하는 <xref:System.ServiceModel.Activities.CorrelationHandle> 옆에 있는 줄임표 단추를 클릭 자식 메시징 활동에 사용 되는 **CorrelatesWith** 필드 **속성** 창에 표시는 **식 편집기**  대화 상자. 이 속성은 활동 디자이너 화면에서도 설정할 수 있습니다.  
  
 해당 디자이너를 삭제 하 여 활동 상관 관계 내에서 범위가 지정 된 된 **본문** 상자 안에 합니다 **CorrelationScope** 디자이너입니다.  
  
### <a name="the-correlationscope-properties"></a>CorrelationScope 속성  
 다음 표에서는 <xref:System.ServiceModel.Activities.CorrelationScope> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성 수에서 편집할 **속성** 창 또는 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 디자이너 화면에 자주 둘 다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 활동의 선택적 이름입니다.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|자식 메시징 활동을 관리하는 데 사용되는 <xref:System.ServiceModel.Activities.CorrelationHandle>을 지정합니다. 이 속성을 설정하지 않으면 <xref:System.ServiceModel.Activities.CorrelationScope>는 자동으로 <xref:System.ServiceModel.Activities.CorrelationHandle>을 만듭니다.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|상관 관계 범위 내에 활동을 지정합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [수신](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [보내기](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)