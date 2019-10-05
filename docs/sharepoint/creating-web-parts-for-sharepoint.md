---
title: SharePoint를 위한 웹 파트 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1105e6c68e1ec9083fd790ad8a38b09870345af2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62580952"
---
# <a name="create-web-parts-for-sharepoint"></a>SharePoint 용 웹 파트 만들기
  웹 파트를 사용 하 여 브라우저를 사용 하 여 콘텐츠, 모양 및 SharePoint 사이트의 페이지의 동작을 수정할 수 있습니다. 웹 파트는 웹 파트 페이지 내에서 실행 되는 서버 쪽 컨트롤: SharePoint 사이트에 표시 되는 페이지의 구성 요소 들은 합니다. 참조 [문서 블록: 웹 파트](http://go.microsoft.com/fwlink/?LinkID=182097)합니다.

 수 만들고 Visual Studio에서 템플릿을 사용 하 여 SharePoint 사이트에서 웹 파트를 디버그 합니다.

## <a name="create-a-web-part-in-visual-studio"></a>Visual Studio에서 웹 파트 만들기
 웹 파트를 추가 하 여 만듭니다는 **웹 파트** SharePoint 프로젝트 항목입니다. 사용할 수는 **웹 파트** 샌드박스 솔루션 또는 팜 솔루션의 항목입니다.

 만들기, 디자이너를 사용 하 여 웹 파트를 시각적으로 디자인 하려는 경우는 **비주얼 웹 파트** 프로젝트 또는 추가 **시각적 웹 파트** SharePoint 프로젝트 항목입니다. 사용할 수는 **비주얼 웹 파트** 항목은 팜 솔루션만 합니다.

### <a name="web-part-item"></a>웹 파트 항목
 A **웹 파트** 항목은 SharePoint 사이트에 대 한 웹 파트를 디자인 하는 데 사용할 수 있는 파일을 제공 합니다. 추가 하는 경우는 **웹 파트** 항목, Visual Studio 프로젝트에 폴더를 만듭니다 및 폴더에 여러 파일이 추가 됩니다. 다음 표에서 각 파일을 보여 줍니다.

|파일|설명|
|----------|-----------------|
|*Elements.xml*|웹 파트를 배포 하려면 프로젝트의 기능 정의 파일을 사용 하는 정보가 포함 되어 있습니다.|
|.webpart 파일|SharePoint 웹 파트 갤러리에서 웹 파트를 표시 하는 데 필요한 정보를 제공 합니다.|
|코드 파일|웹 파트에 컨트롤을 추가 하 고 웹 파트 내에서 사용자 지정 콘텐츠를 생성 하는 메서드를 포함 합니다.|

 자세한 내용은 [방법: SharePoint 웹 파트를 만드는](../sharepoint/how-to-create-a-sharepoint-web-part.md)합니다.

### <a name="visual-web-part-item"></a>비주얼 웹 파트 항목
 비주얼 웹 파트는 Visual Studio에서 Visual Web Developer 디자이너를 사용 하 여 만든 웹 파트입니다. 비주얼 웹 파트를 다른 웹 파트와 동일 하 게 작동 합니다. 단추 및 텍스트 상자 같은 컨트롤에 웹 파트를 추가 하려면 XML 파일에 코드를 추가 합니다. 끌거나 Visual Studio에서 웹 파트를 복사 하 여 비주얼 웹 파트에 컨트롤을 추가 하는 반면 **도구 상자**합니다. 그러면 디자이너는 XML 파일에 필요한 코드를 생성합니다. [방법: 디자이너를 사용 하 여 SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)합니다.

## <a name="sharepoint-controls"></a>SharePoint 컨트롤
 Visual Studio 응용 프로그램 페이지와 같은 SharePoint 페이지를 만들기 위한 몇 가지 컨트롤을 제공 합니다. 이러한 컨트롤에 표시 된 **도구 상자** 아래에서 **SharePoint 컨트롤**합니다. 이러한 컨트롤의 기능에서 파생 되는 [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) SharePoint 사이트 및 목록 페이지에 사용 되는 ASP.NET 서버 컨트롤을 포함 하는 네임 스페이스입니다.

|컨트롤 이름|설명|
|------------------|-----------------|
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|ASP 메뉴를 삽입합니다. 자세한 내용은 [Menu 컨트롤 개요](http://go.microsoft.com/fwlink/?LinkId=235316)합니다.|
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|삽입을 **링크** 요소를 *.aspx* 정의한 하나 이상의 외부 스타일 시트를 적용 하 고 페이지 **CssRegistration**합니다.|
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|에 DateTime 컨트롤을 삽입 합니다 *.aspx* 페이지입니다.|
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|에 보안 유효성 검사를 삽입 합니다 *.aspx* 페이지|
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|지정 된 목록의 속성을 반환합니다.|
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|현재 웹 사이트의 전역 속성을 반환합니다.|
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|에 RSS 피드에 대 한 링크를 삽입 합니다 *.aspx* 페이지입니다.|
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|페이지를 렌더링할 때 요청할 수 있도록 페이지에 스크립트와 같은 리소스를 등록 하기 위한 메서드와 속성을 제공 합니다.|
|[테마](http://go.microsoft.com/fwlink/?LinkId=235314)|테마를 적용 합니다 *.aspx* 페이지입니다.|

## <a name="debug-a-web-part"></a>웹 파트를 디버그 합니다.
 다른 Visual Studio 프로젝트를 디버그할 때 처럼 웹 파트를 포함 하는 SharePoint 프로젝트를 디버깅할 수 있습니다. Visual Studio 디버거를 시작 하면 Visual Studio에 SharePoint 사이트가 열립니다.

 코드를 디버깅을 시작 하려면 sharepoint에서 웹 파트 페이지로 웹 파트를 추가 합니다.

 SharePoint 프로젝트를 디버깅 하는 방법에 대 한 자세한 내용은 참조 하십시오 [문제를 해결 하는 SharePoint 솔루션](../sharepoint/troubleshooting-sharepoint-solutions.md)합니다.

## <a name="visual-web-part-limitations"></a>비주얼 웹 파트 제한
 Visual Studio부터 샌드박스 SharePoint 솔루션 및 팜 솔루션에 비주얼 웹 파트를 추가할 수 있습니다. 그러나 비주얼 웹 파트는 다음 제한 사항이 있습니다.

- 비주얼 웹 파트는 대체 가능 매개 변수를 지원 하지 않습니다. 자세한 내용은 [대체 가능 매개 변수](../sharepoint/replaceable-parameters.md)합니다.

- 사용자 정의 컨트롤 또는 비주얼 웹 파트 놓 및 삭제 하거나 복사할 수 없습니다 비주얼 웹 파트에 있습니다. 이 작업에 빌드 오류가 발생 합니다.

- 비주얼 웹 파트 $SPUrl 같은 SharePoint 서버 토큰을 직접 지원 하지 않습니다. 자세한 내용은 항목의 "토큰 제한에 샌드박스 비주얼 웹 파트"를 참조 하세요 [문제를 해결 하는 SharePoint 솔루션](../sharepoint/troubleshooting-sharepoint-solutions.md)합니다.

- 샌드박스 솔루션의 비주얼 웹 파트에 오류 메시지가 가끔 표시, "샌드박스 코드 실행 요청이 거부 되었습니다는 샌드박스 코드 호스트 서비스 사용자가 너무 많아 요청을 처리 하기 때문에." 이 오류에 대 한 자세한 내용은의이 게시물을 참조 하세요. 합니다 [SharePoint Developer Team Blog](http://go.microsoft.com/fwlink/?LinkId=225932)합니다.

- Visual Studio에서 서버 측 JavaScript 디버깅은 지원 되지 않지만 클라이언트 쪽 JavaScript 디버깅은 지원 합니다.

   인라인 JavaScript를 서버측 태그 파일에 추가할 수 있지만 태그에 추가 된 중단점에 대 한 디버깅이 지원 되지 않습니다. JavaScript를 디버깅 하려면 태그 파일에서 외부 JavaScript 파일을 참조 하 고 JavaScript 파일에 중단점을 설정 합니다.

- 인라인 디버깅 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 코드 태그 파일 대신 생성 된 코드 파일에서 수행 해야 합니다.

- 비주얼 웹 파트 사용을 지원 하지 않습니다는 `<@ Assembly Src=` 지시문입니다.

- SharePoint 웹 컨트롤 및 일부 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 컨트롤은 SharePoint 샌드박스 환경에서 지원 되지 않습니다. 오류를 샌드박스 솔루션의 비주얼 웹 파트에서 지원 되지 않는 제어를 사용 하면 "형식 또는 네임 스페이스 이름 'Microsoft.SharePoint.WebControls 네임 스페이스에 'Theme' 존재 하지 않는" 나타납니다.

  샌드박스 솔루션에 대 한 자세한 내용은 참조 하세요. [차이점 샌드박스 솔루션과 팜 솔루션](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)합니다.

## <a name="create-older-style-sharepoint-based-web-parts"></a>이전 스타일의 SharePoint 기반 웹 파트 만들기
 사용자 지정을 만드는 데 Visual Studio에서 템플릿을 사용할 수 있습니다 [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] 웹 파트를 SharePoint에 대 한 합니다. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] 웹 파트 위에 빌드됩니다는 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 웹 파트 인프라 및 새 프로젝트에 대 한 권장 되는 형식이 있습니다.

 매우 드문 경우 이전 스타일의 SharePoint 기반 웹 파트를 사용 하 여 웹 파트를 만드는 해야 합니다. Visual Studio를 사용 하 여 이러한 유형의 웹 파트를 만들 수 있지만 Visual Studio는 이러한를 만들 수 있도록 특별히 고안 된 템플릿을 제공 하지 않습니다.

 이전 스타일의 SharePoint 기반 웹 파트를 만들려면 하려는 경우에 대 한 자세한 내용은 참조 하세요. [Windows SharePoint Services의 웹 파트 인프라](http://go.microsoft.com/fwlink/?LinkId=169290)합니다. 이전 스타일의 SharePoint 기반 웹 파트를 사용 하 여 웹 파트를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [기본 SharePoint 웹 파트를 만드는 연습](http://go.microsoft.com/fwlink/?LinkId=169288)합니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[방법: SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part.md)|SharePoint 페이지에 대 한 웹 파트를 만드는 방법을 보여 줍니다.|
|[방법: 디자이너를 사용 하 여 SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|시각적 디자인 화면을 사용 하 여 SharePoint 용 웹 파트를 만드는 방법을 보여 줍니다.|
|[방법: SharePoint 응용 프로그램 페이지 또는 웹 파트에 대 한 사용자 정의 컨트롤 만들기](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|응용 프로그램 페이지 및 SharePoint에서 실행 되는 웹 파트에서 사용할 수 있는 재사용 가능한 사용자 지정 컨트롤을 만드는 방법을 보여 줍니다.|
|[연습: SharePoint 용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|SharePoint 용 웹 파트를 디자인 하는 방법에 설명 합니다.|
|[연습: 디자이너를 사용 하 여 SharePoint 용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|시각적 디자인 화면에 컨트롤을 끌어와 SharePoint를 위한 웹 파트를 디자인 하는 방법에 설명 합니다.|
|[연습: SharePoint 용 OData를 표시 하는 Silverlight 웹 파트 만들기](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Silverlight 응용 프로그램을 호스팅하고 SharePoint 목록의 데이터를에서 표시 하는 SharePoint 용 웹 파트를 디자인 하는 방법에 설명 합니다.|
