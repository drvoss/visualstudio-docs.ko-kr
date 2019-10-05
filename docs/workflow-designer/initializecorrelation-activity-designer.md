---
title: 워크플로 디자이너-InitializeCorrelation 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 496aefb2679edd87c892c54f44b14876b4ebce5b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62536441"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation 활동 디자이너

합니다 **InitializeCorrelation** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.ServiceModel.Activities.InitializeCorrelation> 활동입니다. <xref:System.ServiceModel.Activities.InitializeCorrelation> 활동 보내거나 받기 전에 메시지를 처리 간의 상관 관계를 설정 합니다.

## <a name="the-initializecorrelation-activity"></a>InitializeCorrelation 활동

<xref:System.ServiceModel.Activities.InitializeCorrelation> 활동은 메시지를 보내거나 받지 않고 상관 관계를 초기화하는 데 사용됩니다. 일반적으로 상관 관계는 메시지를 보내거나 받을 때 초기화됩니다. 메시지를 보내거나 받기 전에 상관 관계를 설정해야 하는 경우 <xref:System.ServiceModel.Activities.InitializeCorrelation>을 사용하여 상관 관계를 초기화합니다.

### <a name="using-the-initializecorrelation-activity-designer"></a>InitializeCorrelation 활동 디자이너 사용

액세스는 **InitializeCorrelation** 활동 디자이너를 **메시징** 범주의 합니다 **도구 상자**.

**InitializeCorrelation** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 워크플로 디자이너 화면에 끌어 놓 및 합니다. Activity designer 만들어집니다를 <xref:System.ServiceModel.Activities.InitializeCorrelation> 기본값을 사용 하 여 작업 <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation입니다. <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에서 편집할 수 있습니다 합니다 **InitializeCorrelation** 활동 디자이너 또는 합니다 **DisplayName** 상자를 **속성** 창.

<xref:System.ServiceModel.Activities.CorrelationHandle> 수 지정 합니다 **상관 관계** 필드 **속성** 창에서를 **InitializeCorrelation** activity designer 화면.

표시할 합니다 **상관 관계 초기화** 상관 관계 핸들을 초기화 하는 데 사용 되는 키-값 쌍 선택 줄임표 단추 옆에 지정할 수 있는 대화 상자를 **CorrelationData** 필드에 **속성** 창입니다. 또는에서 "보기..." 힌트 텍스트를 선택 합니다 **InitializeCorrelation** activity designer 화면. 이 대화 상자를 사용 하는 방법에 대 한 자세한 내용은 참조는 [형식 컬렉션 편집기 대화 상자](../workflow-designer/type-collection-editor-dialog-box.md) 문서.

### <a name="the-initializecorrelation-properties"></a>InitializeCorrelation 속성

다음 표는 <xref:System.ServiceModel.Activities.InitializeCorrelation> 속성 디자이너에서 사용 하는 방법을 설명 합니다. 이러한 속성을 편집할 수 있습니다 **속성** 창 또는 워크플로 디자이너 화면입니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 활동의 이름입니다. 기본값은 InitializeCorrelation입니다.<br /><br /> 하지만 기본이 아닌 값의 식별 사용 <xref:System.Activities.Activity.DisplayName%2A> 엄격 하 게 필요 하지 않습니다 것이 좋습니다.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|상관 관계에서 워크플로 활동을 연결하는 데 사용되는 <xref:System.ServiceModel.Activities.CorrelationHandle>입니다.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|메시지를 워크플로 인스턴스와 연결하는 상관 관계 데이터의 사전입니다.<br /><br /> 사용 된 **상관 관계 초기화** 대화 상자를 구성할 수는 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>합니다. 사용에 대 한 자세한 내용은이 대화 상자를 참조 합니다 [형식 컬렉션 편집기 대화 상자](../workflow-designer/type-collection-editor-dialog-box.md) 문서.|

## <a name="see-also"></a>참고자료

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)