---
title: SharePoint 앱 페이지나 웹 파트에 대 한 사용자 정의 컨트롤 만들기
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3a88a59e9b87a193329433e5eb0625afa1428026
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401486"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>방법: SharePoint 응용 프로그램 페이지 또는 웹 파트에 대 한 사용자 정의 컨트롤 만들기
  SharePoint 솔루션에 대한 사용자 지정 기능을 제공하는 사용자 지정 사용자 정의 컨트롤을 만들 수 있으며, 프로젝트 내에서 해당 기능을 다시 사용할 수 있습니다. 웹 파트 또는 애플리케이션 페이지에 사용자 정의 컨트롤을 포함하고, 다른 ASP.NET 컨트롤과 SharePoint 컨트롤을 추가하고, 컨트롤에 대한 속성과 메서드를 정의할 수 있습니다. 사용자 정의 컨트롤에 대 한 자세한 내용은 참조 하세요. [웹 파트 또는 응용 프로그램 페이지에 대 한 재사용 가능한 컨트롤을 만들](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) 하 고 [사용자 컨트롤 및 SharePoint에서 서버 컨트롤](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/)합니다.

### <a name="to-create-a-user-control-for-sharepoint"></a>SharePoint에 대 한 사용자 정의 컨트롤을 만들려면

1. Visual Studio에서 SharePoint 프로젝트를 열거나 만듭니다.

     참조 [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)합니다.

2. **솔루션 탐색기**에서 프로젝트 노드를 선택합니다.

3. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택합니다.

     **새 항목 추가** 대화 상자가 열립니다.

4. 에 **설치 됨** 창 선택 합니다 **Office/SharePoint** 노드.

5. SharePoint 템플릿의 목록에서 선택 **사용자 정의 컨트롤 (팜 솔루션만 해당)** 합니다.

    > [!NOTE]
    > 사용자 정의 컨트롤은 팜 솔루션에서만 작동합니다.

6. 에 **이름** 상자, 사용자 정의 컨트롤에 대 한 이름을 지정 하 고 선택한 합니다 **추가** 단추입니다.

     Visual Studio 프로젝트에 여러 폴더와 파일을 추가합니다. 이러한 파일에 대 한 자세한 내용은 참조 하세요. [웹 파트 또는 응용 프로그램 페이지에 대 한 재사용 가능한 컨트롤 만들기](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)합니다.

     기본적으로 사용자 정의 컨트롤 파일에 표시 된 **원본** Visual Web Developer 디자이너의 뷰. 이 뷰에서 컨트롤의 XML 태그를 편집할 수 있습니다. 전환할 수 있습니다 **디자인** 에서 컨트롤을 끌어 컨트롤을 시각적으로 디자인 하려는 경우를 확인 합니다 **도구 상자**합니다. 참조 [디자인 뷰, 웹 페이지 디자이너](/previous-versions/aspnet/ms178149\(v\=vs.100\))합니다.

7. 컨트롤에서 발생하는 이벤트를 처리하려면 사용자 정의 컨트롤의 코드 파일에 코드를 추가합니다.

     이 파일에 나타납니다 **솔루션 탐색기** 사용자 컨트롤 파일 아래에 있고를 *.cs* 또는 *.vb* 프로젝트의 언어에 따라 확장 합니다.

## <a name="see-also"></a>참고자료
- [웹 파트 또는 응용 프로그램 페이지에 대 한 재사용 가능한 컨트롤 만들기](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [SharePoint 용 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)
- [SharePoint 용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)
