---
title: '방법: 응용 프로그램 페이지 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb5c4d7497525706384ced52caae1ba8e02f3e23
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966772"
---
# <a name="how-to-create-an-application-page"></a>방법: 응용 프로그램 페이지 만들기
  하나 이상의 SharePoint 사이트에 대한 ASP.NET 웹 페이지를 만들 수 있습니다. Sharepoint에서 이러한 페이지는 응용 프로그램 페이지 라고 합니다. 사이트 페이지와 달리 응용 프로그램 페이지는 페이지 뒤에 실행 되는 코드를 포함 합니다. 자세한 내용은 [SharePoint 용 응용 프로그램 페이지를 만들](../sharepoint/creating-application-pages-for-sharepoint.md)합니다.

### <a name="to-create-an-application-page"></a>응용 프로그램 페이지를 만들려면

1. Visual Studio에서 SharePoint 프로젝트를 열거나 만듭니다.

     자세한 내용은 [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)합니다.

2. **솔루션 탐색기**에서 프로젝트 노드를 선택합니다.

3. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택합니다.

4. 에 **새 항목 추가** 대화 상자에서 **SharePoint** 노드를 선택한 후는 **2010** 항목입니다.

5. SharePoint 템플릿의 목록에서 선택 **응용 프로그램 페이지**합니다.

6. 에 **이름** 상자, 응용 프로그램 페이지에 대 한 이름을 지정 하 고 선택한 합니다 **추가** 단추입니다.

     Visual Studio 프로젝트에 여러 폴더와 파일을 추가합니다. 이러한 파일에 대 한 자세한 내용은 참조 하세요. [SharePoint 용 응용 프로그램 페이지를 만들](../sharepoint/creating-application-pages-for-sharepoint.md)합니다.

     에 **원본** ASP.NET 페이지 파일이 Visual Web Developer 디자이너 뷰가 나타납니다. 컨트롤을 추가 하 여 페이지를 디자인할 수는 **도구 상자** 콘텐츠 자리 표시자에 배치 하 고 있습니다. 자세한 내용은 [웹 페이지 디자이너, 소스 뷰](/previous-versions/aspnet/ms178154\(v\=vs.100\))합니다.

7. 컨트롤 이벤트를 처리하려면 애플리케이션 페이지의 코드 파일에 코드를 추가합니다.

     코드 파일을 ASP.NET 페이지 파일에 대 한 노드를 확장 하는 경우 나타나고에 *.cs* 하거나 *.vb* 프로젝트의 언어에 따라 확장 합니다. 응용 프로그램 페이지를 만드는 방법의 종단 간 예제를 참조 하세요. [연습: SharePoint 응용 프로그램 페이지 만들기](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 용 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)
- [연습: SharePoint 응용 프로그램 페이지 만들기](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
