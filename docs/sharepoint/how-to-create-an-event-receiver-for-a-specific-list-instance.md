---
title: '방법: 특정 목록 인스턴스에 대 한 이벤트 수신기 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: 34114c12ef47fb796de7354aa3133af1fc704267
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408544"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>방법: 특정 목록 인스턴스에 대 한 이벤트 수신기 만들기
  목록 인스턴스 이벤트 수신자 목록 정의의 모든 인스턴스에서 발생 하는 이벤트에 응답 합니다. 이벤트 수신기 템플릿 특정 목록 인스턴스에의 타기 팅을 사용 하지 않습니다 하지만 특정 목록 인스턴스에 이벤트에 응답 하는 목록 정의에 범위가 지정 된 이벤트 수신기를 수정할 수 있습니다.

 특정 목록 인스턴스를 대상으로 합니다 *Elements.xml* 이벤트 수신기에 대 한 대체 `ListTemplateId` 사용 하 여 `ListUrl` 목록 인스턴스의 URL을 추가 합니다.

## <a name="create-a-list-instance-event-receiver"></a>목록 인스턴스 이벤트 수신기 만들기
 다음 단계를 사용자 지정 알림 목록을 인스턴스에서 발생 하는 이벤트에만 응답 하도록 목록 항목 이벤트 수신기를 수정 하는 방법을 보여 줍니다.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>특정 목록 인스턴스에 응답할 이벤트 수신기를 수정 하려면

1. 브라우저에서 SharePoint 사이트를 엽니다.

2. 탐색 창에서 **나열** 링크 합니다.

3. 에 **모든 사이트 콘텐츠** 페이지를 선택 합니다 **만들기** 링크 합니다.

4. 에 **만들기** 대화 상자를 선택 합니다 **공지** 입력, 알림의 이름을 **TestAnnouncements**, 선택한 후를 **만들기**단추입니다.

5. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 이벤트 수신기 프로젝트를 만듭니다.

6. 에 **이벤트 수신기 유형을 선택 하십시오?** 목록에서 선택 **목록 항목 이벤트**합니다.

    > [!NOTE]
    > 다른 유형의 예를 들어 목록 정의를 범위 지정 하는 이벤트 수신기를 선택할 수도 있습니다 **전자 메일 이벤트 목록** 하거나 **목록 워크플로 이벤트**합니다.

7. 에 **이벤트 소스를 사용할 항목을?** 목록에서 선택 **공지**합니다.

8. 에 **다음 이벤트를 처리할** 목록에서를 **항목이 추가 되** 확인란을 선택한 후는 **마침** 단추.

9. **솔루션 탐색기**를 열고의 EventReceiver1 아래에서 *Elements.xml*합니다.

     이벤트 수신기가 다음 코드 줄을 사용하여 알림 목록 정의를 현재 참조합니다.

    ```xml
    <Receivers ListTemplateId="104">
    ```

     이 줄을 다음 텍스트로 변경합니다.

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     이벤트 수신기가 새 발생 하는 이벤트에만 응답 하도록이 지시 **TestAnnouncements** 방금 만든 공지 사항 목록입니다. 변경할 수는 `ListURL` SharePoint 서버의 모든 목록 인스턴스를 참조 하는 특성입니다.

10. 이벤트 수신기에 대 한 코드 파일을 열고 ItemAdding 메서드에서 중단점을 설정 합니다.

11. 선택 된 **F5** 키를 빌드하고 솔루션을 실행 합니다.

12. Sharepoint에서 선택 합니다 **TestAnnouncements** 탐색 창에서 링크 합니다.

13. 선택 된 **새 알림 추가** 링크 합니다.

14. 알림의 제목을 입력 하 고 다음을 선택 합니다 **저장** 단추입니다.

     사용자 지정 알림 목록에 새 항목이 추가 되 면 중단점이 적중 되는 알 수 있습니다.

15. 선택 된 **F5** 키를 다시 시작 합니다.

16. 탐색 창에서 선택 합니다 **나열** 링크를 선택한 다음는 **공지** 링크.

17. 새 공지 사항을 추가 합니다.

     수신자는 사용자 지정 알림 목록 인스턴스에 이벤트에만 응답 하도록 구성 되었기 때문에 이벤트 수신기가 새 알림에서 트리거하지 되었다는 **TestAnnouncements**합니다.

## <a name="see-also"></a>참고자료
- [방법: 이벤트 수신기 만들기](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
