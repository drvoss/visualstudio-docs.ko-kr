---
title: ReceiveAndSendReply 템플릿 디자이너-워크플로 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f6f3f874d00dff8a171a169dca6fe2d94f14fe6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969347"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply 템플릿 디자이너

합니다 **ReceiveAndSendReply** 서식 파일은 쌍을 만드는 데 미리 구성 된 <xref:System.ServiceModel.Activities.Receive> 및 <xref:System.ServiceModel.Activities.SendReply> 활동입니다. 활동의 일부인는 <xref:System.Activities.Statements.Sequence> 작업과 상관 관계가 지정 된 서버에서 요청/응답 메시지 교환 패턴의 일부로.

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply 템플릿

추가 **ReceiveAndSendReply** 템플릿을 만드는 것 외에 세 가지 작업을 수행 합니다 <xref:System.ServiceModel.Activities.Receive> 및 <xref:System.ServiceModel.Activities.SendReply> 사용 하 여 활동을 <xref:System.Activities.Statements.Sequence> 활동:

- 구성 합니다 <xref:System.ServiceModel.Activities.Receive.OperationName%2A> 및 <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> 의 속성을 <xref:System.ServiceModel.Activities.Receive> 활동입니다.

- <xref:System.ServiceModel.Activities.SendReply.Request%2A> 활동의 <xref:System.ServiceModel.Activities.Receive> 속성이 <xref:System.ServiceModel.Activities.Send> 활동에 바인딩됩니다.

- 부모 활동의 변수로 <xref:System.ServiceModel.Activities.CorrelationHandle>이 만들어집니다.

### <a name="use-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply 템플릿 디자이너를 사용 하 여

액세스는 **ReceiveAndSendReply** 활동 디자이너를 **메시징** 범주의 합니다 **도구 상자**. 합니다 **ReceiveAndSendReply** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 일반적으로 활동을 배치 하는 위치는 워크플로 디자이너 화면에 끌어 놓 및 합니다. Activity designer 만들어집니다를 <xref:System.ServiceModel.Activities.Receive> 구성할 수 있는 작업을 **보내기** 활동 디자이너 및 상호 연관 된 <xref:System.ServiceModel.Activities.SendReply> 활동과 SendReplyToReceive 디자이너로 구성할 수 있습니다.

사용에 대 한 자세한 내용은 합니다 **수신** 구성 디자이너를 <xref:System.ServiceModel.Activities.Receive> 활동 참조 [수신 활동 디자이너](../workflow-designer/receive-activity-designer.md)합니다.

### <a name="properties-of-sendreply"></a>SendReply 속성

다음 표에서는 <xref:System.ServiceModel.Activities.SendReply> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있습니다 하 고 일부는 워크플로 디자이너 화면에서 편집할 수 있습니다.

| 속성 이름 | 필수 | 사용 |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | <xref:System.ServiceModel.Activities.SendReply> 활동의 선택적 이름입니다. 기본값은 SendReplyToReceive입니다.<br /><br /> 하지만 기본이 아닌 값의 식별 사용 <xref:System.Activities.Activity.DisplayName%2A> 은 꼭 필요 하지 이러한 값을 사용 하는 것이 좋습니다. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | 이 <xref:System.ServiceModel.Activities.Receive> 활동과 한 쌍을 이루는 <xref:System.ServiceModel.Activities.SendReply> 활동에 대한 참조입니다. 이 속성은 아니어야 **null**합니다. <xref:System.ServiceModel.Activities.Receive> 및 <xref:System.ServiceModel.Activities.SendReply> 활동은 서버에서 요청/응답 메시징 패턴을 모델링하는 데 함께 사용됩니다. 이 속성은 쌍을 이루는 <xref:System.ServiceModel.Activities.Send> 활동을 지정합니다. 디자이너에서 편집할 수 없습니다를 자동으로 바인딩되어 있기 때문에이 속성을 <xref:System.ServiceModel.Activities.Send> 를 만든 활동은 <xref:System.ServiceModel.Activities.SendReply> 활동. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | 받을 메시지 또는 매개 변수 콘텐츠를 지정합니다. <xref:System.ServiceModel.Activities.ReceiveMessageContent> 활동이거나 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 활동일 수 있습니다. 옆에 있는 줄임표 단추를 클릭 하 여이 속성을 편집 합니다 **콘텐츠** 클릭 하 여 또는 속성 표의 필드를 **정의** 단추 옆에 **콘텐츠** 레이블 합니다  **수신** activity designer 화면. 모두 표시 합니다 **콘텐츠 정의** 대화 합니다. 이 상자를 사용 하는 방법에 대 한 자세한 내용은 참조는 [콘텐츠 정의 대화 상자](../workflow-designer/content-definition-dialog-box.md) 항목입니다. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | 워크플로 내에서 이 <xref:System.ServiceModel.Activities.CorrelationInitializer> 활동을 구성하는 <xref:System.ServiceModel.Activities.CorrelationHandle> 개체를 여러 개 초기화하는 <xref:System.ServiceModel.Activities.Receive> 개체 컬렉션을 지정합니다. 다음 줄임표 단추를 클릭 합니다 <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> 열려면 속성 표에서 속성을 **상관 관계 이니셜라이저 추가** 대화 상자. 이 상자를 사용 하는 방법에 대 한 자세한 내용은 참조는 [상관 관계 이니셜라이저 추가 대화 상자](../workflow-designer/add-correlationinitializers-dialog-box.md) 항목입니다. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | 메시지의 동작 헤더를 지정합니다. 명시적으로 설정 된 경우 기본값:<br /><br /> <strong>https://tempuri.org/{service 계약 네임 스페이스} / {서비스 계약 이름} /} /{operation name}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | 회신 메시지를 보내기 전에 워크플로 인스턴스를 유지할지 여부를 지정합니다. 기본값은 **false**입니다. |

## <a name="see-also"></a>참고자료

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)