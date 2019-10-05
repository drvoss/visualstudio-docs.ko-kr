---
title: '연습: 기본 사이트 정의 프로젝트 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d781b2fe3ab597760a397c6ff0ec3c946bbe7653
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009413"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>연습: 기본 사이트 정의 프로젝트 만들기
  이 연습에서는 일부 컨트롤에 시각적 웹 파트를 포함 하는 기본 사이트 정의 만드는 방법을 보여 줍니다. 명확성을 위해 사용자가 만든 시각적 웹 파트에만 몇 가지 컨트롤이 있습니다. 그러나 더 많은 기능을 포함 하는 보다 복잡 한 SharePoint 사이트 정의 만들 수 있습니다.

 이 연습에서는 다음 작업을 수행합니다.

- 사이트 정의 사용 하 여 만들기는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 프로젝트 템플릿.

- SharePoint에서 사이트 정의 사용 하 여 SharePoint 사이트를 만드는 중입니다.

- 시각적 웹 파트를 솔루션에 추가 합니다.

- 새 시각적 웹 파트를 추가 하 여 사이트의 default.aspx 페이지를 사용자 지정 합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- 지원되는 Microsoft Windows 및 SharePoint 버전. 자세한 내용은 SharePoint 솔루션 개발 요구 사항을 참조 합니다.

- Visual Studio.

## <a name="create-a-site-definition-solution"></a>사이트 정의 솔루션 만들기
 사이트 정의 프로젝트를 먼저 만듭니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

#### <a name="to-create-a-site-definition-project"></a>사이트 정의 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다. IDE는 메뉴 모음에서 Visual Basic 개발 설정을 사용 하도록 설정 하는 경우 선택할 **파일** > **새 프로젝트**합니다.

    **새 프로젝트** 대화 상자가 나타납니다.

2. 확장을 **Visual C#** 노드 또는 **Visual Basic** 노드를 확장 합니다 **SharePoint** 노드를 선택한 후는 **2010** 노드.

3. 에 **템플릿을** 목록에서 선택 합니다 **SharePoint 2010 프로젝트** 템플릿.

4. 에 **이름** 상자에 입력 합니다 **TestSiteDef**를 선택한 후는 **확인** 단추입니다.

    합니다 **SharePoint 사용자 지정 마법사** 나타납니다.

5. 에 **디버깅에 대 한 사이트 및 보안 수준을 지정할** 페이지에서 사이트 정의 디버그 하려는 SharePoint 사이트에 대 한 URL을 입력 하거나 기본 위치를 사용 하 여 (http://<em>시스템 이름</em>/).

6. 에 **이 SharePoint 솔루션의 신뢰 수준을?** 섹션을 선택 합니다 **팜 솔루션으로 배포** 옵션 단추입니다.

    모든 사이트 정의 프로젝트가 팜 솔루션으로 배포 되어야 합니다. 샌드박스 솔루션과 팜 솔루션 비교에 대 한 자세한 내용은 참조 하세요. [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)합니다.

7. 선택 된 **완료** 단추입니다.

    프로젝트에 나타납니다 **솔루션 탐색기**합니다.

8. **솔루션 탐색기**, 프로젝트 노드를 선택한 다음, 메뉴 모음에서 **프로젝트** > **새 항목 추가**합니다.

9. 준 **Visual C#** 또는 **Visual Basic**를 확장 합니다 **SharePoint** 노드를 선택한 후는 **2010** 노드.

10. 에 **템플릿** 창 선택는 **사이트 정의** 템플릿을 유지를 **이름** 으로 **SiteDefinition1**를 선택한 다음 합니다  **추가** 단추입니다.

## <a name="create-a-visual-web-part"></a>비주얼 웹 파트 만들기
 다음으로 사이트 정의 기본 페이지에 표시할 시각적 웹 파트를 만듭니다.

#### <a name="to-create-a-visual-web-part"></a>비주얼 웹 파트를 만들려면

1. **솔루션 탐색기**를 선택 합니다 **모든 파일 표시** 단추입니다.

2. 선택 된 **SiteDefinition1** 프로젝트 노드를 선택한 다음 메뉴 모음에서 **프로젝트** > **새 항목 추가**합니다.

     **새 항목 추가** 대화 상자가 나타납니다.

3. 확장을 **Visual C#** 노드 또는 **Visual Basic** 노드를 확장 합니다 **SharePoint** 노드를 선택한 후는 **2010** 노드.

4. 템플릿 목록에서 선택 합니다 **비주얼 웹 파트** 템플릿, 기본 VisualWebPart1, 이름을 지정 하 고 선택한 유지 합니다 **추가** 단추.

     합니다 *VisualWebPart1.ascx* 파일 열립니다.

5. 맨 아래에 *VisualWebPart1.ascx*, 3 개의 컨트롤을 폼에 추가 하려면 다음 태그를 추가 합니다: 텍스트 상자, 단추 및 레이블이:

    ```aspx-csharp
    <table>
      <tr>
        <td>
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>
        </td>
        <td>
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>
        </td>
        <td>
          <asp:Label runat="server" ID="lblName"></asp:Label>
        </td>
      </tr>
    </table>
    ```

6. 아래 *VisualWebPart1.ascx*오픈 합니다 *VisualWebPart1.ascx.cs* 파일 (에 대 한 [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) 또는 *VisualWebPart1.ascx.vb* (에 대 한 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)])를 추가한 다음 다음 코드는

     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

     이 코드는 웹 파트의 단추 클릭에 대 한 기능을 추가 합니다.

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>기본 ASPX 페이지에 시각적 웹 파트 추가
 다음으로, 사이트 정의 기본 ASPX 페이지에 시각적 웹 파트를 추가 합니다.

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>기본 ASPX 페이지에 비주얼 웹 파트를 추가 하려면

1. Default.aspx 페이지를 연 다음 아래의 다음 줄을 추가 합니다 `WebPartPages` 태그:

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     이 줄 웹 파트 및 해당 코드를 사용 하 여 이름을 MyWebPartControls를 연결합니다. 합니다 *Namespace* 매개 변수에서 사용 되는 네임 스페이스와 일치 하는 *VisualWebPart1.ascx* 코드 파일.

2. 후 합니다 `</asp:Content>` 요소인 전체를 바꿉니다 `ContentPlaceHolderId="PlaceHolderMain"` 섹션 및 다음 코드를 사용 하 여 해당 콘텐츠:

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     이 코드는 앞서 만든 시각적 웹 파트에 대 한 참조를 만듭니다.

3. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SiteDefinition1** 노드를 선택한 후 **시작 항목으로 설정**합니다.

## <a name="deploy-and-run-the-site-definition-solution"></a>배포 하 고 사이트 정의 솔루션 실행
 다음으로 프로젝트를 SharePoint에 배포 하 고 프로젝트를 실행 합니다.

#### <a name="to-deploy-and-run-the-site-definition"></a>사이트 정의를 배포 및 실행하려면

- 메뉴 모음에서 선택 **빌드합니다** > **TestSiteDef 배포**합니다.

- **F5** 키를 선택합니다.

     Visual Studio에서 코드를 컴파일합니다, 그리고 해당 기능을 추가, SharePoint 솔루션 (WSP) 파일로 파일의 모든 패키지 및 WSP 파일을 SharePoint 서버에 배포 합니다. SharePoint는 다음 파일을 설치 하 고 기능을 활성화 합니다.

## <a name="create-a-site-based-on-the-site-definition"></a>사이트 정의 기반으로 사이트 만들기
 다음으로 새 사이트 정의 사용 하 여 사이트를 만듭니다.

#### <a name="to-create-a-site-by-using-the-site-definition"></a>사이트 정의 사용 하 여 사이트를 만들려면

1. SharePoint 사이트에서 새 SharePoint 사이트 페이지가 표시 됩니다.

2. 에 **제목과 설명을** 섹션에서 입력 **내 새 사이트** 제목과 설명은 사이트에 대 한 합니다.

3. 에 **웹 사이트 주소** 섹션에서 입력 **mynewsite** 에 **URL 이름** 상자입니다.

4. 에 **템플릿** 섹션을 선택 합니다 **SharePoint 사용자 지정** 탭 합니다.

5. 에 **템플릿을 선택** 목록에서 선택 **SiteDefinition1**합니다.

6. 해당 기본값에서 다른 설정을 그대로 두고를 선택 합니다 **만들기** 단추입니다.

     새 사이트에는 다음이 표시 됩니다.

## <a name="test-the-new-site"></a>새 사이트를 테스트 합니다.
 다음으로, 올바르게 작동 하는지 여부를 확인 하려면 새 사이트를 테스트 합니다.

#### <a name="to-test-the-new-site"></a>새 사이트를 테스트 하려면

- 기본 ASPX 페이지에서 일부 텍스트를 입력 하 고 다음을 선택 합니다 **레이블 텍스트 변경** 입력란 옆에 있는 단추입니다.

     텍스트가 레이블에 단추 오른쪽에 나타납니다.

## <a name="see-also"></a>참고자료
- [방법: 이벤트 수신기 만들기](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
