---
title: '방법: 이벤트 수신기 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc42a92e1d7dcc73bb6bc0433da4e6a31d7fefb2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966759"
---
# <a name="how-to-create-an-event-receiver"></a>방법: 이벤트 수신기 만들기
  만들어 *이벤트 수신기*, SharePoint 등 목록 또는 목록 항목을 사용 하 여 상호 작용할 때 응답할 수 있습니다. 예를 들어, 사용자 일정을 변경 하거나 연락처 목록에서 이름을 삭제 하는 경우 이벤트 수신기의 코드를 트리거할 수 있습니다. 이 항목에 따라 목록 인스턴스에 이벤트 수신기를 추가 하는 방법을 알아보십시오.

 이러한 단계를 완료 하려면 설치 해야 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Windows 및 SharePoint 버전을 지원 합니다. 이 예제에서는 SharePoint 프로젝트를 필요로 하므로 완료 해야 항목의 절차 [연습: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)합니다.

## <a name="adding-an-event-receiver"></a>이벤트 수신기 추가
 만든 프로젝트 [연습: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) 사용자 지정 사이트 열, 사용자 지정 목록 및 콘텐츠 형식을 포함 합니다. 다음 절차에서는 SharePoint 목록 등에서 발생 하는 이벤트를 처리 하는 방법을 보여 주는 목록 인스턴스에 (이벤트 수신기) 간단한 이벤트 처리기를 추가 하 여이 프로젝트를 확장 하겠습니다.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>목록 인스턴스에 이벤트 수신기를 추가 하려면

1. 만든 프로젝트를 열고 [연습: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)합니다.

2. **솔루션 탐색기**, 이름으로 지정 된 SharePoint 프로젝트 노드를 선택 **클리닉**합니다.

3. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택합니다.

4. 준 **Visual C#** 또는 **Visual Basic**를 확장 합니다 **SharePoint** 노드를 선택한 후는 **2010** 항목입니다.

5. 에 **템플릿** 창 선택 **이벤트 수신기**, 이름을 **TestEventReceiver1**를 선택한 후는 **확인** 단추입니다.

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다.

6. 에 **이벤트 수신기 유형을 선택 하십시오?** 목록에서 선택 **목록 항목 이벤트**합니다.

7. 에 **이벤트 소스를 사용할 항목을?** 목록에서 선택 **환자 (Clinic\Patients)** 합니다.

8. 에 **다음 이벤트를 처리할** 목록 옆에 확인란을 선택 합니다 **항목이 추가 되었습니다**를 선택한 후는 **완료** 단추.

     새 이벤트 수신기에 대 한 코드 파일 이라고 하는 단일 메서드를 포함 `ItemAdded`합니다. 다음 단계에서는 모든 연락처 이름이 Scott Brown 기본적으로 지정 됩니다 있도록이 방법으로 코드를 추가할 수 있습니다.

9. 기존 바꿉니다 `ItemAdded` 메서드를 다음 코드를 선택한 후 합니다 **F5** 키:

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     코드 실행 및 SharePoint 사이트가 웹 브라우저에 나타납니다.

10. 빠른 실행 모음에서 선택 합니다 **환자** 링크를 선택한 다음는 **새 항목 추가** 링크 합니다.

     새 항목에 대 한 항목 양식이 열립니다.

11. 데이터 필드에 입력 한 다음 선택 합니다 **저장** 단추입니다.

     선택한 후는 **저장** 단추를 **환자 이름** Scott Brown 이름 열을 자동으로 업데이트 합니다.

## <a name="see-also"></a>참고자료

- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)