---
title: 워크플로 디자이너 InitializeCorrelation 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98a9a6bccb6eab2c4565a717daa897f93dbe8f53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650218"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation 활동 디자이너

**InitializeCorrelation** 활동 디자이너는 <xref:System.ServiceModel.Activities.InitializeCorrelation> 활동을 만들고 구성 하는 데 사용 됩니다. @No__t_0 작업은 메시지를 보내거나 받기 전에 메시지 간의 상관 관계를 설정 합니다.

## <a name="the-initializecorrelation-activity"></a>InitializeCorrelation 활동

<xref:System.ServiceModel.Activities.InitializeCorrelation> 활동은 메시지를 보내거나 받지 않고 상관 관계를 초기화하는 데 사용됩니다. 일반적으로 상관 관계는 메시지를 보내거나 받을 때 초기화됩니다. 메시지를 보내거나 받기 전에 상관 관계를 설정해야 하는 경우 <xref:System.ServiceModel.Activities.InitializeCorrelation>을 사용하여 상관 관계를 초기화합니다.

### <a name="using-the-initializecorrelation-activity-designer"></a>InitializeCorrelation 활동 디자이너 사용

**도구 상자**의 **메시징** 범주에서 **InitializeCorrelation** 활동 디자이너에 액세스 합니다.

**InitializeCorrelation** 활동 디자이너를 **도구 상자** 에서 끌어서 워크플로 디자이너 화면에 놓을 수 있습니다. 활동 디자이너를 삭제 하면 기본 <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation의 <xref:System.ServiceModel.Activities.InitializeCorrelation> 활동이 만들어집니다. **InitializeCorrelation** 활동 디자이너의 머리글 또는 **속성** 창의 **DisplayName** 상자에서 <xref:System.Activities.Activity.DisplayName%2A> 편집할 수 있습니다.

**InitializeCorrelation** activity Designer 화면의 **속성** 창에서 **상관 관계** 필드에 <xref:System.ServiceModel.Activities.CorrelationHandle>를 지정할 수 있습니다.

상관 관계 **초기화** 대화 상자를 표시 하려면 상관 관계 핸들 및이를 초기화 하는 데 사용 되는 키-값 쌍을 지정할 수 있습니다. 그런 다음 **속성** 창에서 **CorrelationData** 필드 옆에 있는 줄임표 단추를 선택 합니다. 또는 "보기 ..."를 선택 합니다. **InitializeCorrelation** activity designer 화면의 힌트 텍스트입니다. 이 대화 상자를 사용 하는 방법에 대 한 자세한 내용은 [형식 컬렉션 편집기 대화 상자](../workflow-designer/type-collection-editor-dialog-box.md) 문서를 참조 하세요.

### <a name="the-initializecorrelation-properties"></a>InitializeCorrelation 속성

다음 표에서는 <xref:System.ServiceModel.Activities.InitializeCorrelation> 속성을 보여 주고 디자이너에서 이러한 속성을 사용 하는 방법을 설명 합니다. 이러한 속성은 **속성** 창이 나 워크플로 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필요한 공간|사용 현황|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> 활동의 이름입니다. 기본값은 InitializeCorrelation입니다.<br /><br /> 친숙 한 <xref:System.Activities.Activity.DisplayName%2A>에 대해 기본값이 아닌 값을 사용 하는 것이 반드시 필요한 것은 아니지만이 값을 사용 하는 것이 좋습니다.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|상관 관계에서 워크플로 활동을 연결하는 데 사용되는 <xref:System.ServiceModel.Activities.CorrelationHandle>입니다.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|메시지를 워크플로 인스턴스와 연결하는 상관 관계 데이터의 사전입니다.<br /><br /> **상관 관계 초기화** 대화 상자를 사용 하 여 <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>를 구성할 수 있습니다. 이 대화 상자 사용에 대 한 자세한 내용은 [형식 컬렉션 편집기 대화 상자](../workflow-designer/type-collection-editor-dialog-box.md) 문서를 참조 하세요.|

## <a name="see-also"></a>참조

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)