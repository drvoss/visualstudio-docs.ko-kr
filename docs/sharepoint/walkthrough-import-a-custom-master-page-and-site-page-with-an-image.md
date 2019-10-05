---
title: 사용자 지정 마스터 페이지 및 이미지를 사용 하 여 사이트 페이지 가져오기
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8bd2d9054571e52bc9fbb3906bc1880bb94e407a
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66400901"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>연습: 사용자 지정 마스터 페이지 및 사이트 페이지를 이미지로 가져오기
  이 연습에서는 SharePoint 사용자 지정 마스터 페이지와 이미지가 있는 사이트 페이지를 가져오는 방법을 보여는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 프로젝트입니다.

 이 연습에서는 다음 작업을 수행 하는 방법을 보여 줍니다.

- SharePoint Designer에서 이미지를 사용 하 여 사용자 지정 마스터 페이지 및 사이트 페이지를 만듭니다.

- SharePoint 솔루션에 사용자 지정 마스터 페이지, 이미지 및 사이트 페이지를 내보내기 ( *.wsp*) 파일입니다.

- 가져오기 및 배포 합니다 *.wsp* 파일을 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 솔루션 패키지 가져오기 프로젝트를 사용 하 여 SharePoint 프로젝트입니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료 하려면 다음 구성 요소가 있어야 합니다.

- 지원 되는 버전 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 및 SharePoint입니다.

- Visual Studio.

- SharePoint Designer 2010.

## <a name="create-items-in-sharepoint-designer"></a>SharePoint Designer에서 항목 만들기
 이 예제에는 내보내기에 대 한 SharePoint Designer에서 세 개의 항목을 만드는 방법을 보여 줍니다: 사용자 지정 마스터 페이지, 사용자 지정 마스터 페이지 및 사이트 페이지에 표시할 이미지 파일을 참조 하는 사이트 페이지입니다. 이미지는 SharePoint /images/ 폴더에 추가 됩니다.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>SharePoint Designer에서 사용자 지정 마스터 페이지를 만들려면

1. SharePoint 디자이너의 탐색 창에서 선택 합니다는 **마스터 페이지** 사이트 개체입니다.

2. 에 **마스터 페이지** 리본에서 선택 **빈 마스터 페이지**합니다.

3. 새 마스터 페이지 선택를 선택한 후는 **마스터 페이지** 리본에서 선택 **파일 편집**합니다.

4. SharePoint Designer의 맨 아래에서 선택 합니다 **코드** 탭 합니다.

5. 기존 태그를 다음 태그로 바꿉니다.

    ```aspx-csharp
    <%@ Master Language="C#" %>
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <html dir="ltr">
    <head runat="server">
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>
    <title>Web Page</title>
    </head>
    <body>
    <form id="form1" runat="server">
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"
            runat="server">
          </asp:ContentPlaceHolder>
    </form>
    </body>
    </html>
    ```

6. 페이지 저장을 선택 합니다 **마스터 페이지** 탭을 마스터 페이지 이름 바꾸기 **mybasic1.master**합니다.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>SharePoint Designer에서 콘텐츠 데이터베이스에 이미지 추가
 이제 사이트 페이지에 표시할 이미지를 추가할 수 있습니다. 이미지는 SharePoint 콘텐츠 데이터베이스에 배포 됩니다.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>SharePoint Designer에서 콘텐츠 데이터베이스에 이미지를 추가 하려면

1. 탐색 창에서 선택 합니다 **모든 파일** 사이트 개체를 한 다음 트리 뷰를 선택 합니다 **이미지** 폴더입니다.

2. 에 **모든 파일** 리본에서 선택 **파일 가져오기**, 사용자가 선택한 파일을 선택한 다음 합니다 **확인** 단추. 이 예제에서는 파일 이름은 **myimg1.png**합니다.

     필요에 따라 이미지를 구성 하는 데 하위 폴더를 만들 수 있습니다.

3. 닫기 합니다 **가져오기** 대화 상자.

## <a name="create-a-site-page"></a>사이트 페이지 만들기
 이 기본 사이트 페이지 사용자 지정 마스터 페이지를 사용 하 고 이전 단계에서 추가한 이미지를 표시 합니다.

#### <a name="to-create-a-site-page"></a>사이트 페이지를 만들려면

1. 탐색 창에서 선택 합니다 **사이트 페이지** 개체입니다.

2. 에 **페이지** 리본에서 선택 합니다 **페이지** 단추를 선택는 **ASPX** 형식 페이지 및 다음 새 파일 이름을 **mycontentpage1.aspx**.

     필요에 따라 사이트 페이지를 구성 하는 데 하위 폴더를 만들 수 있습니다.

3. 사이트 페이지 목록에서 선택 **MyContentPage1.aspx** 해당 속성 페이지를 열고 다음 페이지의 맨 아래에서 선택 합니다 **파일 편집** 링크 합니다.

     메시지 및이 페이지에 안전 모드에서 편집 가능한 모든 영역이 포함 되어 있지 않은지 라는 나타나고 고급 모드에서이 페이지를 열고 것인지 여부를 묻는 경우 합니다 **예** 단추입니다.

4. 페이지의 맨 아래에서 선택 합니다 **코드** 단추입니다.

5. 기존 태그를 다음 태그로 바꿉니다.

    ```aspx-csharp
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>
    <%@ Import Namespace="Microsoft.SharePoint" %>
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>

    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />
    </asp:Content>
    ```

6. 업데이트 된 사이트 페이지를 저장 합니다.

## <a name="export-the-items-from-sharepoint"></a>SharePoint에서 항목 내보내기
 SharePoint 솔루션을 SharePoint에서 항목을 내보낼 ( *.wsp*) 파일입니다.

#### <a name="to-export-items-from-sharepoint-designer"></a>SharePoint Designer에서 항목을 내보내려면

1. SharePoint 디자이너의 탐색 창에서 선택 합니다는 **팀 사이트** 개체를 선택한 다음는 **사이트** 리본에서 선택 **템플릿으로 저장**합니다.

2. 에 **템플릿으로 저장** 대화 상자, 파일 이름 및 템플릿 이름을 입력는 **콘텐츠 포함** 확인란을 선택한 후는 **확인** 단추.

     이 사이트의 콘텐츠를 저장 합니다 *.wsp* 파일입니다.

3. 솔루션을 내보낸 후 선택 합니다 **솔루션 갤러리** 링크를 사용할 수 있는 솔루션 파일의 목록을 표시 합니다.

4. 새 바로 가기 메뉴를 열고 *.wsp* 파일을 선택한 후 **이름으로 대상 저장** 시스템에 저장 합니다.

## <a name="import-the-items-into-visual-studio"></a>Visual Studio로 항목 가져오기
 가져오기의 *.wsp* 파일 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다. 콘텐츠를 가져온 후 사용자 지정할 수 있습니다, 그리고 더 많은 항목을 추가 및 배포 합니다.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Visual Studio에.wsp 파일에서 항목을 가져오려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 만들기는 **SharePoint 2010 솔루션 패키지 가져오기** 프로젝트입니다.

2. 에 **가져올 항목 선택** 페이지의 **모듈** 에 **형식** 열 가져오기에 대 한 다음 해당 파일에 대해서만 확인란을 선택 합니다.

   | 파일 이름 | 설명 |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | 사용자 지정 마스터 페이지입니다. |
   | images_ | SharePoint 파일 시스템에서 이미지 파일입니다. |
   | SitePages_ | 사이트 페이지입니다. |

3. 선택 합니다 **완료** 단추는 선택한 항목을 가져올 수 있습니다.

4. **솔루션 탐색기**를 선택 합니다 \_catalogsmasterpage\_ 노드를 값을 설정 하 고 해당 **배포 충돌 해결** 속성을 **자동** .

    이렇게 하면 배포 충돌이 자동으로 해결 됩니다.

5. 새 마스터 페이지에 기존 페이지와 같은 이름을 기존 페이지 기본 마스터 페이지 또는 SharePoint Designer에서 사용자 지정 마스터 페이지 표시 되지 않도록 해야 합니다.

    기존 마스터 페이지는 기본 마스터 페이지 또는 사용자 지정 마스터 페이지도 표시 되 면 하는 경우 마스터 페이지를 삭제할 수 없습니다 상태는 배포 오류를 받습니다. 이 문제를 방지 하려면이 수행 합니다.

   - 기존 마스터 페이지가 마스터 페이지 기본으로 설정 되어 일시적으로 다른 마스터 페이지 기본 마스터 페이지로 설정 합니다. SharePoint에 파일을 배포한 후 기본 마스터 페이지와 새 마스터 페이지를 설정 합니다.

   - 기존 마스터 페이지는 사용자 지정 마스터 페이지로 설정 됩니다, 경우 일시적으로 다른 마스터 페이지 사용자 지정 마스터 페이지. SharePoint에 파일을 배포한 후 사용자 지정 마스터 페이지와 새 마스터 페이지를 설정 합니다.

6. 메뉴 모음에서 선택 **빌드합니다** > **솔루션 배포**합니다.

7. 배포 항목을 표시 하도록 SharePoint 사이트를 엽니다.

   대안에는 파일을 가져오는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 하 고 배포 합니다 SharePoint 파일의 모듈에 추가 하는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [어떻게: 마스터 페이지 또는 테마 가져오기](../sharepoint/how-to-import-a-master-page-or-theme.md) 하 고 [모듈을 사용 하 여 솔루션에 파일을 포함](../sharepoint/using-modules-to-include-files-in-the-solution.md)합니다.

## <a name="see-also"></a>참고자료
- [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [웹 파트 또는 응용 프로그램 페이지에 대 한 재사용 가능한 컨트롤 만들기](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
