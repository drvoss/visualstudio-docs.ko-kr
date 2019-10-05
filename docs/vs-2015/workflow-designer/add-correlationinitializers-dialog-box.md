---
title: 추가 상관 관계 이니셜라이저 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0c90a2d0e0297a00454e38f428093a2f2db1e46d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977482"
---
# <a name="add-correlationinitializers-dialog-box"></a>상관 관계 이니셜라이저 추가 대화 상자
**상관 관계 이니셜라이저 추가** 대화 상자에서 사용 됩니다 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 구성 하는 **CorrelationInitializers** 의 속성을 <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, 및 <xref:System.ServiceModel.Activities.ReceiveReply> 활동입니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 상자를 사용 하는 활동 디자이너 참조를 [보낼](../workflow-designer/send-activity-designer.md), [수신](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), 및 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) 항목입니다.  
  
 이 대화 상자에서 지정한 컬렉션의 상관 관계 이니셜라이저는 쿼리 기반, 컨텍스트, 콜백 컨텍스트 또는 메시징 활동 간의 요청-회신 상관 관계를 초기화할 수 있습니다.  
  
 다음 표에 사용자 인터페이스 (UI) 요소에는 **상관 관계 이니셜라이저 추가** 대화 상자.  
  
|UI 요소|설명|  
|----------------|-----------------|  
|**이니셜라이저 추가**|클릭 합니다 **추가 초기화** 상자 컬렉션에 추가 이니셜라이저를 추가할 수 있습니다.|  
|**상관 관계 유형**|상관 관계 이니셜라이저의 형식을 지정합니다. 다음 네 가지 형식 중에서 선택할 수 있습니다.<br /><br /> 1.  <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>를 지정하는 콜백 상관 관계 이니셜라이저<br />2.  <xref:System.ServiceModel.Activities.CorrelationInitializer>를 지정하는 컨텍스트 상관 관계 이니셜라이저<br />3.  <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>를 지정하는 요청-회신 상관 관계 이니셜라이저<br />4.  <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>를 지정하는 쿼리 상관 관계 이니셜라이저<br /><br /> 편집 하 여 **CorrelationType**<br /><br /> 1.  특정 행을 탭 합니다 **이니셜라이저 추가** DataGrid.<br />2.  Ctrl + Tab 키를 눌러 포커스를 **CorrelationTypeComboBox**<br />3.  팝업 Alt + 아래쪽 화살표 키를 눌러 합니다 **ComboBox** 하 고 편집 합니다.|  
|**XPath 쿼리**|들어오는 메시지와 나가는 메시지에서 상관 관계 데이터를 추출하는 데 사용되는 쿼리가 포함된 키/값 쌍입니다. 이 목록은 <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 형식을 사용하는 경우에만 유효합니다.|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>상관 관계 이니셜라이저 추가 대화 상자를 시작하려면  
 **상관 관계 이니셜라이저 추가** 대화 상자를 사용 하 여 합니다 **보낼**를 **수신**, **ReceiveAndSendReply**, 및  **SendAndReceiveReply** 디자이너입니다. 액세스 하는 것은 각 사례에는 유사 합니다 **수신** 디자이너 절차를 설명 하기 위해 여기에 사용 됩니다.  
  
 **수신** 활동 디자이너에서 끌 수 있습니다는 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면 아무 곳에 나 작업은 일반적으로 배치 합니다. 그러면 기본 <xref:System.ServiceModel.Activities.Receive>인 Receive라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. 선택 합니다 **수신** 활동 디자이너 및 (컬렉션) 텍스트 옆 줄임표 단추를 클릭 합니다 **CorrelationInitializers** 속성 표에서 속성을 **추가 상관 관계 이니셜라이저** 대화 상자를 표시 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [상관 관계 초기화 대화 상자](../workflow-designer/initialize-correlation-dialog-box.md)