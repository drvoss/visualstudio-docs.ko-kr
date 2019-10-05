---
title: '연습: SharePoint 응용 프로그램 페이지 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 749ec5f7f7bd68911accb33e4e8631b42de8e630
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778634"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>연습: SharePoint 응용 프로그램 페이지 만들기

응용 프로그램 페이지는 특수 한 형태의 ASP.NET 페이지입니다. 응용 프로그램 페이지에는 SharePoint 마스터 페이지를 사용 하 여 병합 되는 콘텐츠가 포함 됩니다. 자세한 내용은 [SharePoint 용 응용 프로그램 페이지를 만들](../sharepoint/creating-application-pages-for-sharepoint.md)합니다.

이 연습에서는 응용 프로그램 페이지를 만들고 다음 로컬 SharePoint 사이트를 사용 하 여 디버그 하는 방법을 보여 줍니다. 이 페이지에는 각 사용자가 만들거나 서버 팜의 모든 사이트에서 수정한 모든 항목이 표시 됩니다.

이 연습에서는 다음 작업을 수행합니다.

- SharePoint 프로젝트를 만듭니다.
- SharePoint 프로젝트에 응용 프로그램 페이지를 추가 합니다.
- 응용 프로그램 페이지에 ASP.NET 컨트롤을 추가 합니다.
- ASP.NET 컨트롤에 숨김 코드를 추가 합니다.
- 응용 프로그램 페이지를 테스트 합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>전제 조건

- Windows 및 SharePoint 버전을 지원 합니다.

## <a name="create-a-sharepoint-project"></a>SharePoint 프로젝트 만들기

첫째, 만듭니다는 **빈 SharePoint 프로젝트**합니다. 나중에 추가 합니다는 **응용 프로그램 페이지** 이 프로젝트 항목입니다.

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 엽니다는 **새 프로젝트** 대화 상자에서 **Office/SharePoint** 언어를 사용 하 고 선택 하려는 아래의 노드를 **SharePoint 솔루션** 노드.

3. 에 **Visual Studio 설치 된 템플릿** 창 선택 합니다 **SharePoint 2010-빈 프로젝트** 템플릿. 프로젝트 이름을 **MySharePointProject**를 선택 합니다 **확인** 단추입니다.

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다. 이 마법사를 사용 하면 프로젝트 및 솔루션의 신뢰 수준을 디버그 하는 데 사용할 사이트를 선택할 수 있습니다.

4. 선택 합니다 **팜 솔루션으로 배포** 옵션 단추를 선택한 후는 **마침** 기본 로컬 SharePoint 사이트를 적용 하는 단추입니다.

## <a name="create-an-application-page"></a>응용 프로그램 페이지 만들기

응용 프로그램 페이지를 만들려면 추가 **응용 프로그램 페이지** 프로젝트 항목입니다.

1. **솔루션 탐색기**를 선택 합니다 **MySharePointProject** 프로젝트입니다.

2. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택합니다.

3. 에 **새 항목 추가** 대화 상자를 선택 합니다 **응용 프로그램 페이지 (팜 솔루션만** 템플릿.

4. 페이지의 이름을 **SearchItems**를 선택 합니다 **추가** 단추입니다.

     Visual Web Developer 디자이너에서 응용 프로그램 페이지를 표시 **원본** 페이지의 HTML 요소를 볼 수 있습니다. 여러 태그를 표시 하는 디자이너 <xref:System.Web.UI.WebControls.Content> 컨트롤입니다. 각 컨트롤에 매핑되는 <xref:System.Web.UI.WebControls.ContentPlaceHolder> 기본 응용 프로그램 마스터 페이지에 정의 된 컨트롤입니다.

## <a name="design-the-layout-of-the-application-page"></a>응용 프로그램 페이지의 레이아웃 디자인

응용 프로그램 페이지 항목을 사용 하면 디자이너를 사용 하 여 응용 프로그램 페이지를 ASP.NET 컨트롤을 추가할 수 있습니다. 이 디자이너는 Visual Web Developer에서 사용 하는 동일한 디자이너입니다. 레이블, 라디오 단추 목록 및 테이블을 추가 합니다 **원본** 디자이너의 보기 및 표준 ASP.NET 페이지를 디자인할 때와 마찬가지로 다음 속성을 설정 합니다.

1. 메뉴 모음에서 **보기** > **도구 상자**를 선택합니다.

2. 표준 노드의 합니다 **도구 상자**, 다음 단계 중 하나를 수행 합니다.

    - 바로 가기 메뉴를 열고 합니다 **레이블** 항목을 선택 **복사**, 아래의 줄에 대 한 바로 가기 메뉴를 열고 합니다 **PlaceHolderMain** 콘텐츠 컨트롤 디자이너에서 차례로 선택할 **붙여넣기**합니다.

    - 끌어서 합니다 **레이블** 에서 항목는 **도구 상자** 의 본문에는 **PlaceHolderMain** 콘텐츠 컨트롤입니다.

3. 추가 하려면 이전 단계를 반복을 **DropDownList** 항목 및 **테이블** 항목을 **PlaceHolderMain** 콘텐츠 컨트롤입니다.

4. 디자이너에서 값을 변경 합니다 `Text` 레이블 컨트롤의 특성 **모든 항목 표시**합니다.

5. 디자이너에서 대체는 `<asp:DropDownList>` 다음 xml 요소입니다.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>페이지의 컨트롤의 이벤트를 처리 합니다.

ASP.NET 페이지와 마찬가지로 응용 프로그램 페이지의 컨트롤을 처리 합니다. 이 절차에서는 처리할지를 `SelectedIndexChanged` 드롭다운 목록의 이벤트입니다.

1. 에 **뷰** 메뉴 선택 **코드**합니다.

     응용 프로그램 페이지 코드 파일이 코드 편집기에서 열립니다.

2. 다음 메서드를 `SearchItems` 클래스에 추가합니다. 이 코드를 처리 합니다 <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> 의 이벤트를 <xref:System.Web.UI.WebControls.DropDownList> 이 연습의 뒷부분에서 만들 메서드를 호출 하 여 합니다.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. 응용 프로그램 페이지 코드 파일의 맨 위에 다음 문을 추가 합니다.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. 다음 메서드를 `SearchItems` 클래스에 추가합니다. 이 메서드는 서버 팜의 모든 사이트를 통해 반복 하 고 현재 사용자가 만들거나 수정한 항목을 검색 합니다.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. 다음 메서드를 `SearchItems` 클래스에 추가합니다. 이 메서드는 테이블에서 현재 사용자가 만들거나 수정한 항목을 표시 합니다.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>응용 프로그램 페이지 테스트

프로젝트를 실행 하면 SharePoint 사이트가 열리고 응용 프로그램 페이지가 나타납니다.

1. **솔루션 탐색기**선택한를 응용 프로그램 페이지에 대 한 바로 가기 메뉴를 열고 **시작 항목으로 설정**합니다.

2. **F5** 키를 선택합니다.

     SharePoint 사이트가 열립니다.

3. 응용 프로그램 페이지를 선택 합니다 **내가 수정** 옵션입니다.

     응용 프로그램 페이지가 새로 고쳐지고 서버 팜의 모든 사이트에서 수정한 항목이 모두 표시 됩니다.

4. 응용 프로그램 페이지에서 선택 **내가 만든** 목록에서입니다.

     응용 프로그램 페이지가 새로 고쳐지고 서버 팜의 모든 사이트에서 만든 모든 항목을 표시 합니다.

## <a name="next-steps"></a>다음 단계

SharePoint 응용 프로그램 페이지에 대 한 자세한 내용은 참조 하세요. [SharePoint 용 응용 프로그램 페이지를 만들](../sharepoint/creating-application-pages-for-sharepoint.md)합니다.

자세한 내용은 다음이 항목에서는 Visual Web Designer를 사용 하 여 SharePoint 페이지 콘텐츠를 디자인 하는 방법에 대 한 합니다.

- [SharePoint 용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)합니다.

- [웹 파트 또는 응용 프로그램 페이지에 대 한 재사용 가능한 컨트롤 만들기](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)합니다.

## <a name="see-also"></a>참고자료

[방법: 응용 프로그램 페이지 만들기](../sharepoint/how-to-create-an-application-page.md)
[응용 프로그램 _layouts 페이지 형식](http://go.microsoft.com/fwlink/?LinkID=169274)
