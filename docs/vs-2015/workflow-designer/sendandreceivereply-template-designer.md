---
title: SendAndReceiveReply 템플릿 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 689f3a57dc3de9bbe63b0ef69a969cac57a639c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62948028"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply 템플릿 디자이너
**SendAndReceiveReply** 서식 파일은 쌍을 만드는 데 미리 구성 된 <xref:System.ServiceModel.Activities.Send> 및 <xref:System.ServiceModel.Activities.ReceiveReply> 내에서 작업을 <xref:System.Activities.Statements.Sequence> 요청/응답 메시지 교환의 일환으로 상호 연결 되는 클라이언트에서 패턴입니다.  

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply 템플릿  
 추가 **SendAndReceiveReply** 템플릿을 만드는 것 외에 세 가지 작업을 수행 합니다 <xref:System.ServiceModel.Activities.Send> 및 <xref:System.ServiceModel.Activities.ReceiveReply> 내에서 활동을 <xref:System.Activities.Statements.Sequence> 활동:  

1. <xref:System.ServiceModel.Activities.Send.OperationName%2A> 활동의 <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A>, <xref:System.ServiceModel.Activities.Send> 속성이 구성됩니다.  

2. <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> 활동의 <xref:System.ServiceModel.Activities.ReceiveReply> 속성이 <xref:System.ServiceModel.Activities.Send> 활동에 바인딩됩니다.  

3. 부모 활동의 변수로 <xref:System.ServiceModel.Activities.CorrelationHandle>이 만들어집니다.  

### <a name="using-the-sendandreceivereply-template-designer"></a>SendAndReceiveReply 템플릿 디자이너 사용  
 **SendAndReceiveReply** 활동 디자이너에서 찾을 수 있습니다 합니다 **메시징** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구 상자 ** 탭에서 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **뷰** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  

 **SendAndReceiveReply** 활동 디자이너에서 끌 수 있습니다는 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면 아무 곳에 나 작업은 일반적으로 배치 합니다. 이렇게를 <xref:System.ServiceModel.Activities.Send> 구성할 수 있는 작업을 **보내기** 활동 디자이너 및 상호 연관 된 <xref:System.ServiceModel.Activities.ReceiveReply> 사용 하 여 구성할 수 있는 **ReceiveReplyForSend** 디자이너.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] 사용 하 여는 **보낼** 구성 디자이너를 <xref:System.ServiceModel.Activities.Send> 활동 참조를 [보내기](../workflow-designer/send-activity-designer.md) 항목입니다.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] 사용 하 여는 **ReceiveReplyForSend** 구성 디자이너를 <xref:System.ServiceModel.Activities.ReceiveReply> 활동, 다음 섹션을 참조 합니다.  

### <a name="properties-of-receivereply"></a>ReceiveReply의 속성  
 다음 표에서는 <xref:System.ServiceModel.Activities.ReceiveReply> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 디자이너 화면에서 편집할 수 있습니다.  

|                                 속성 이름                                 | 필수 |                                                                                                                                                                                                                                                                                                                                                        사용                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            <xref:System.ServiceModel.Activities.ReceiveReply> 활동의 선택적 이름입니다. 기본값은 ReceiveReplyForSend입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>에 꼭 기본값 이외의 값을 사용할 필요는 없지만 그런 값을 사용하는 것이 좋습니다.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | 이 <xref:System.ServiceModel.Activities.Send> 활동과 한 쌍을 이루는 <xref:System.ServiceModel.Activities.ReceiveReply> 활동에 대한 참조입니다. 이 속성은 아니어야 **null**합니다. <xref:System.ServiceModel.Activities.Send> 및 <xref:System.ServiceModel.Activities.ReceiveReply> 활동은 클라이언트에서 요청/응답 메시징 패턴을 모델링하는 데 함께 사용됩니다. 이 속성은 쌍을 이루는 <xref:System.ServiceModel.Activities.Send> 활동을 지정합니다. 이 속성은 <xref:System.ServiceModel.Activities.Send> 활동을 만들었던 <xref:System.ServiceModel.Activities.ReceiveReply> 활동에 자동으로 바인딩되기 때문에 디자이너에서 편집할 수 없습니다. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        받을 메시지 또는 매개 변수 콘텐츠를 지정합니다. <xref:System.ServiceModel.Activities.ReceiveMessageContent> 활동이거나 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 활동일 수 있습니다. 옆에 있는 줄임표 단추를 클릭 하 여이 속성을 편집 합니다 **콘텐츠** 필드를 클릭 하거나 속성 표를 **정의 하는 중...** 옆에 있는 단추는 **콘텐츠** 에 레이블을 지정 합니다 **수신** activity designer 화면. 모두 표시 합니다 **콘텐츠 정의** 대화 합니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 상자를 사용 하는 합니다 [콘텐츠 정의 대화 상자](../workflow-designer/content-definition-dialog-box.md) 항목입니다.                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              워크플로 내에서 이 <xref:System.ServiceModel.Activities.CorrelationInitializer> 활동을 구성하는 <xref:System.ServiceModel.Activities.CorrelationHandle> 개체를 여러 개 초기화하는 <xref:System.ServiceModel.Activities.Receive> 개체 컬렉션을 지정합니다. 다음 줄임표 단추를 클릭 합니다 <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> 열려면 속성 표에서 속성을 **상관 관계 이니셜라이저 추가** 대화 상자. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 상자를 사용 하 여 참조를 [상관 관계 이니셜라이저 추가 대화 상자](../workflow-designer/add-correlationinitializers-dialog-box.md) 항목입니다.               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               메시지의 동작 헤더를 지정합니다. 동작 헤더가 명시적으로 설정되어 있지 않으면 기본값인<br /><br /> <strong>https://tempuri.org/{service 계약 네임 스페이스} / {서비스 계약 이름} /} /{operation name}.</strong>                                                                                                                                                                                                                                               |

## <a name="see-also"></a>참고 항목  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [수신](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [보내기](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)