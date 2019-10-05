---
title: InitializeCorrelation 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 383a2e892c8f0962ab8c09d5e8984d3cc570ebaa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979984"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation 활동 디자이너
합니다 **InitializeCorrelation** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.ServiceModel.Activities.InitializeCorrelation> 보내거나 받기 전에 메시지 간 상관 관계를 설정 하는 데 사용 되는 작업입니다.  
  
## <a name="the-initializecorrelation-activity"></a>InitializeCorrelation 활동  
 <xref:System.ServiceModel.Activities.InitializeCorrelation> 활동은 메시지를 보내거나 받지 않고 상관 관계를 초기화하는 데 사용됩니다. 일반적으로 상관 관계는 메시지를 보내거나 받을 때 초기화됩니다. 메시지를 보내거나 받기 전에 상관 관계를 설정해야 하는 경우 <xref:System.ServiceModel.Activities.InitializeCorrelation>을 사용하여 상관 관계를 초기화합니다.  
  
### <a name="using-the-initializecorrelation-activity-designer"></a>InitializeCorrelation 활동 디자이너 사용  
 **InitializeCorrelation** 활동 디자이너에서 찾을 수 있습니다 합니다 **메시징** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구 상자**  탭의 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **보기** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 **InitializeCorrelation** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면. 이렇게를 <xref:System.ServiceModel.Activities.InitializeCorrelation> 기본값을 사용 하 여 활동 <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation.The의 <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에서 편집할 수 있습니다 합니다 **InitializeCorrelation** 활동 디자이너 또는  **DisplayName** 상자는 **속성** 창입니다.  
  
 <xref:System.ServiceModel.Activities.CorrelationHandle> 수 지정 합니다 **상관 관계** 필드 **속성** 창에서를 **InitializeCorrelation** activity designer 화면.  
  
 줄임표 단추를 클릭 하 여 **CorrelationData** 필드에 **속성** 창 또는 "보기..." 텍스트에서 힌트 **InitializeCorrelation** activity designer 화면을 표시 합니다 **상관 관계 초기화** 하는 데 사용 하는 키-값 쌍과 상관 관계 핸들을 지정할 수 있는 대화 상자 초기화 합니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 대화 상자를 사용 하 여 참조를 [형식 컬렉션 편집기 대화 상자](../workflow-designer/type-collection-editor-dialog-box.md) 항목입니다.  
  
### <a name="the-initializecorrelation-properties"></a>InitializeCorrelation 속성  
 다음 표에서는 <xref:System.ServiceModel.Activities.InitializeCorrelation> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성을 편집할 수 있습니다 **속성** 창 또는 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 활동의 이름입니다. 기본값은 InitializeCorrelation입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>에 꼭 기본값 이외의 값을 사용할 필요는 없지만 그런 값을 사용하는 것이 좋습니다.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|상관 관계에서 워크플로 활동을 연결하는 데 사용되는 <xref:System.ServiceModel.Activities.CorrelationHandle>입니다.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|메시지를 워크플로 인스턴스와 연결하는 상관 관계 데이터의 사전입니다.<br /><br /> 사용 된 **상관 관계 초기화** 대화 상자를 구성할 수는 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>합니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 사용 하 여가 대화 상자를 참조 합니다 [형식 컬렉션 편집기 대화 상자](../workflow-designer/type-collection-editor-dialog-box.md) 항목입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [수신](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [보내기](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)