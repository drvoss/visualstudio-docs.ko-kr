---
title: 디자이너를 사용 하 여 SharePoint에 대 한 웹 파트 만들기
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9963c2f7e829e9d295ca254aa651e37e3ad08efd
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401139"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>연습: 디자이너를 사용 하 여 SharePoint 용 웹 파트 만들기

SharePoint 사이트에 대 한 웹 파트를 만드는 경우 사용자가 직접 수정 콘텐츠, 모양 및 동작의 페이지의 브라우저를 사용 하 여 합니다. 이 연습에서는 SharePoint를 사용 하 여 시각적으로 웹 파트를 만드는 방법을 보여 줍니다 **비주얼 웹 파트** Visual Studio에서 프로젝트 템플릿.

웹 파트를 만들어야 하는 사이트에서 월별 달력 보기 및 각 달력 목록에 대 한 확인란을 표시 합니다. 사용자는 확인란을 선택 하 여 월별 달력 보기에 포함할 달력 목록을 지정할 수 있습니다.

이 연습에서는 다음 작업을 수행합니다.

- 웹 파트를 사용 하 여 만드는 합니다 **비주얼 웹 파트** 프로젝트 템플릿.
- Visual Studio에서 Visual Web Developer 디자이너를 사용 하 여 웹 파트를 디자인 합니다.
- 웹 파트에 있는 컨트롤의 이벤트를 처리 하는 코드를 추가 합니다.
- Sharepoint에서 웹 파트를 테스트 합니다.

    > [!NOTE]
    > 컴퓨터는 다음 지침에 다른 이름이 나 for Visual Studio 사용자 인터페이스의 일부 요소에 대 한 위치를 표시할 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>전제 조건

이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- Windows 및 SharePoint 버전을 지원 합니다.

## <a name="create-a-web-part-project"></a>웹 파트 프로젝트 만들기

사용 하 여 웹 파트 프로젝트를 먼저 만듭니다는 **비주얼 웹 파트** 프로젝트 템플릿.

1. 시작 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 를 사용 하 여 합니다 **관리자 권한으로 실행** 옵션입니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

     **새 프로젝트** 대화 상자가 나타납니다.

3. 에 **새 프로젝트** 준 대화 상자 **Visual C#** 또는 **Visual Basic**를 확장 **Office/SharePoint**를 선택한 다음 합니다  **SharePoint 솔루션** 범주입니다.

4. 템플릿 목록에서 선택 합니다 **SharePoint 2013-비주얼 웹 파트** 템플릿을 선택한 후는 **확인** 단추입니다.

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다. 이 마법사를 사용 하 여 프로젝트 및 솔루션의 신뢰 수준 디버깅을 사용 하는 사이트를 지정할 수 있습니다.

5. 에 **이 SharePoint 솔루션의 신뢰 수준을?** 섹션을 선택 합니다 **팜 솔루션으로 배포** 옵션 단추입니다.

6. 선택 된 **완료** 기본 로컬 SharePoint 사이트를 적용 하는 단추입니다.

## <a name="designing-the-web-part"></a>웹 파트 디자인

컨트롤을 추가 하 여 웹 파트를 디자인 합니다 **도구 상자** Visual Web Developer 디자이너의 화면입니다.

1. Visual Web Developer 디자이너에서 선택 합니다 **디자인** 디자인 뷰로 전환 하려면 탭 합니다.

2. 메뉴 모음에서 **보기** > **도구 상자**를 선택합니다.

3. 에 **표준** 노드의 **도구 상자**를 선택 합니다 **CheckBoxList** 컨트롤 하 고 다음 단계 중 하나를 수행:

    - 바로 가기 메뉴를 열고 합니다 **CheckBoxList** 컨트롤을 선택 **복사**, 디자이너에서 첫 번째 줄에 대 한 바로 가기 메뉴를 열고 선택한 후 **붙여넣기**합니다.

    - 끌어서 합니다 **CheckBoxList** 에서 제어 합니다 **도구 상자**, 디자이너에서 첫 번째 줄에 컨트롤을 연결 하 고 합니다.

4. 이전 단계를 반복 하지만 단추를 디자이너의 다음 줄으로 이동 합니다.

5. 디자이너에서 선택 합니다 **Button1** 단추입니다.

6. 메뉴 모음에서 선택 **뷰** > **속성 창**합니다.

     합니다 **속성** 창이 열립니다.

7. 에 **텍스트** 단추의 속성 입력 **업데이트**합니다.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>웹 파트에 있는 컨트롤의 이벤트 처리

사용자가 마스터 달력 보기에 달력을 추가할 수 있는 코드를 추가 합니다.

1. 다음 단계 중 하나를 수행합니다.

   - 디자이너에서 두 번 클릭 합니다 **업데이트** 단추입니다.

   - 에 **속성** 창에 대 한는 **업데이트** 단추를 선택 합니다 **이벤트** 단추. 에 **클릭** 속성인 입력 **Button1_Click**, Enter 키를 선택 하 고 합니다.

     사용자 컨트롤 코드 파일이 코드 편집기에서 열립니다 및 `Button1_Click` 이벤트 처리기가 나타납니다. 나중에이 이벤트 처리기에 코드를 추가 합니다.

2. 사용자 정의 컨트롤 코드 파일의 맨 위에 다음 문을 추가 합니다.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. 코드의 다음 줄을 추가 합니다 `VisualWebPart1` 클래스입니다. 이 코드는 월별 달력 보기 컨트롤을 선언합니다.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. 대체는 `Page_Load` 메서드는 `VisualWebPart1` 클래스를 다음 코드로 합니다. 이 코드는 다음 작업을 수행합니다.

   - 사용자 정의 컨트롤에는 월별 달력 보기를 추가합니다.

   - 사이트의 각 달력 목록에 대 한 확인란을 추가합니다.

   - 달력 보기에 표시 되는 항목의 각 형식에 대 한 서식 파일을 지정 합니다.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. 대체는 `Button1_Click` 메서드는 `VisualWebPart1` 클래스를 다음 코드로 합니다. 이 코드 마스터 달력 보기에 각 선택한 일정에서 항목을 추가합니다.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>웹 파트 테스트

프로젝트를 실행 하면 SharePoint 사이트가 열립니다. 웹 파트는 sharepoint에서 웹 파트 갤러리에 자동으로 추가 됩니다. 이 프로젝트를 테스트 하려면 다음 작업을 수행 합니다.

- 두 개의 별도 일정 목록의 각 이벤트를 추가 합니다.
- 웹 파트 페이지에 웹 파트를 추가 합니다.
- 월별 달력 보기에 포함할 목록을 지정 합니다.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>사이트의 달력 목록에 이벤트를 추가 하려면

1. Visual Studio에서 선택 합니다 **F5** 키입니다.

     SharePoint 사이트가 열리고 및 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 빠른 실행 도구 모음 페이지에 나타납니다.

2. 빠른 실행 모음에서 아래 **나열**를 선택 합니다 **달력** 링크 합니다.

     합니다 **달력** 페이지가 나타납니다.

     일정 링크가 나타나면 빠른 실행 모음에서을 선택 합니다 **사이트 콘텐츠** 링크 합니다. 사이트 내용 페이지에 표시 되지 않으면를 **달력** 항목을 만들어야 합니다.

3. 달력 페이지의 하루를 선택한 다음 선택 합니다 **추가** 이벤트를 추가 하려면 선택한 날에 대 한 링크입니다.

4. 에 **제목** 상자에 입력 합니다 **기본 달력에서 이벤트**를 선택한 후는 **저장** 단추.

5. 선택 된 **사이트 콘텐츠** 링크를 선택한 후는 **앱 추가** 타일입니다.

6. 에 **만들기** 페이지를 선택 합니다 **달력** 입력, 일정의 이름 및 선택한를 **만들기** 단추.

7. 새 일정에 이벤트를 추가, 이벤트 이름 **사용자 지정 일정에서 이벤트**를 선택한 후 합니다 **저장** 단추입니다.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>웹 파트 페이지에 웹 파트를 추가 하려면

1. 에 **사이트 콘텐츠** 페이지를 열고 합니다 **사이트 페이지** 폴더입니다.

2. 리본에서 선택 합니다 **파일** 탭을 열고를 **새 문서** 메뉴에서 선택한 후는 **웹 파트 페이지** 명령.

3. 에 **새 웹 파트 페이지** 페이지에서 페이지의 이름을 **SampleWebPartPage.aspx**를 선택한 후는 **만들기** 단추입니다.

     웹 파트 페이지에 표시 됩니다.

4. 웹 파트 페이지의 위쪽 영역을 선택 합니다 **삽입** 탭을 선택한 다음는 **웹 파트** 단추입니다.

5. 선택 합니다 **사용자 지정** 폴더를 선택 합니다 **VisualWebPart1** 웹 파트를 선택한 후는 **추가** 단추.

     웹 파트 페이지에 나타납니다. 다음 컨트롤은 웹 파트에 나타납니다.

    - 월별 달력 보기입니다.

    - **업데이트** 단추입니다.

    - A **달력** 확인란 합니다.

    - A **Custom Calendar** 확인란 합니다.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>월별 달력 보기에 포함할 목록을 지정 하려면

웹 파트를 선택 하 고 월별 달력 보기에 포함할 원하는 일정을 지정 합니다 **업데이트** 단추입니다.

지정한 모든 달력의 이벤트가 월별 달력 보기에 나타납니다.

## <a name="see-also"></a>참고자료

[SharePoint 용 웹 파트를 만들](../sharepoint/creating-web-parts-for-sharepoint.md)
[방법: SharePoint 웹 파트를 만듭니다](../sharepoint/how-to-create-a-sharepoint-web-part.md)
[연습: SharePoint 용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
