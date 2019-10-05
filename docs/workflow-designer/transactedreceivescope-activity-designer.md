---
title: TransactedReceiveScope 활동 디자이너-워크플로 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a103b0db53ced447e16d269d747fa3355aeb00c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433996"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope 활동 디자이너

합니다 **TransactedReceiveScope** 디자이너는 만들기 및 구성 하는 데 사용 됩니다는 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 활동입니다.

## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope 활동

<xref:System.ServiceModel.Activities.TransactedReceiveScope> 활동을 통해 트랜잭션을 워크플로 또는 디스패처에 의해 만들어진 서버 트랜잭션으로 이동할 수 있습니다.

### <a name="using-the-transactedreceivescope-activity-designer"></a>TransactedReceiveScope 활동 디자이너 사용

액세스는 **TransactedReceiveScope** 활동 디자이너를 **메시징** 범주의 합니다 **도구 상자**. 합니다 **TransactedReceiveScope** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 일반적으로 활동을 배치 하는 위치는 워크플로 디자이너 화면에 끌어 놓 및 합니다. 이렇게 한 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 기본값을 사용 하 여 활동 **DisplayName** transactedreceivescope입니다. <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에서 편집할 수 있습니다 합니다 **TransactedReceiveScope** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자.

합니다 **TransactedReceiveScope** 디자이너 포함 **요청** 하 고 **본문** 상자입니다. 이 상자는 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 속성을 구성하는 데 사용되고, 이 속성은 <xref:System.ServiceModel.Activities.Receive> 활동과 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 속성을 지정하며, 이 속성은 다시 몇 가지 다른 <xref:System.Activities.Activity>를 지정합니다. <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>는 트랜잭션을 만듭니다. 그러면 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 범위의 트랜잭션이 앰비언트 트랜잭션이 되어 이 범위의 모든 활동이 이 트랜잭션 내에서 실행됩니다.

### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope 속성

다음 표에서는 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 <xref:System.Activities.Activity.DisplayName%2A> 워크플로 디자이너 화면 또는 속성 표의 속성을 편집할 수 있습니다 하지만 다른 디자인 화면에서 편집 해야 합니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.TransactedReceiveScope> 활동의 선택적 이름입니다. 기본값은 TransactedReceiveScope입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> 이름이 꼭 필요하지 않더라도 표시 이름을 사용하는 것이 좋습니다.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|삭제를 <xref:System.ServiceModel.Activities.Receive> 활동을 **요청** activity designer 화면에는 블록입니다.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|삭제를 <xref:System.Activities.Activity> 에 **본문** activity designer 화면에서 차단 합니다.|

## <a name="see-also"></a>참고자료

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)