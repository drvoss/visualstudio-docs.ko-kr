---
title: 웹 파트 또는 응용 프로그램 페이지에 대 한 재사용 가능한 컨트롤 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71e67ab41fd39563520370eb079fca1b7c82015e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952791"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>웹 파트 또는 응용 프로그램 페이지에 대 한 재사용 가능한 컨트롤 만들기
  Visual Studio에서는 SharePoint에서 실행되는 애플리케이션 페이지와 웹 파트에서 사용할 수 있는 재사용 가능한 사용자 지정 컨트롤을 만들 수 있습니다. 이러한 컨트롤은 사용자 컨트롤 이라고 합니다. 사용자 정의 컨트롤은 ASP.NET 웹 페이지와 비슷하게 작동 하는 복합 컨트롤의 한 종류-사용자 정의 컨트롤을 기존 웹 서버 컨트롤 및 태그를 추가 하 고 컨트롤의 메서드와 속성을 정의할 수 있습니다. 그런 다음 단위 프록시로 ASP.NET 웹 페이지에서 포함할 수 있습니다.

## <a name="create-a-user-control"></a>사용자 정의 컨트롤 만들기
 사용자 정의 컨트롤을 만들려면 추가 **사용자 정의 컨트롤** 에 **빈 SharePoint 프로젝트**합니다. 자세한 내용은 [방법: SharePoint 응용 프로그램 페이지 또는 웹 파트에 대 한 사용자 컨트롤을 만드는](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)합니다.

 추가 하는 경우는 **사용자 정의 컨트롤** 항목, Visual Studio 프로젝트에서 폴더를 만듭니다 및 폴더에 여러 파일이 추가 됩니다. 다음 표에서 각 파일을 보여 줍니다.

|파일|설명|
|----------|-----------------|
|사용자 정의 컨트롤 파일|사용자 정의 컨트롤을 정의합니다. 이 파일에 컨트롤 및 태그를 추가 하 여 사용자 정의 컨트롤을 디자인 합니다.|
|코드 파일|사용자 정의 컨트롤 코드를 포함합니다. 이 파일에 이벤트를 처리 하는 코드를 추가 합니다.|
|디자이너 코드 파일|디자이너에서 생성 된 코드를 포함 하 고 직접 편집할 수 없습니다.|

## <a name="design-the-user-control"></a>사용자 정의 컨트롤 디자인
 Visual Studio에서 Visual Web Developer 디자이너를 사용 하 여 사용자 정의 컨트롤을 디자인 합니다. 이 디자이너는 프로젝트에서 사용자 정의 컨트롤 파일을 열고 선택 하면 나타납니다 합니다 **디자인** 탭 합니다.

## <a name="consume-the-user-control"></a>사용자 정의 컨트롤 사용
 사용자 정의 컨트롤을 응용 프로그램 페이지 또는 웹 파트를 포함 해야 SharePoint에 표시 되지 않습니다.

 응용 프로그램 페이지에 사용자 정의 컨트롤을 포함 하는 ASP.NET 사용자 정의 컨트롤을 추가 하려는 웹 페이지를 엽니다. 디자인 뷰로 다음 솔루션 탐색기에서 사용자 정의 컨트롤 파일 선택 전환한 페이지로 끌어다 놓습니다. ASP.NET 사용자 컨트롤은 페이지에 추가 하 고 디자이너는 사용자 정의 컨트롤을 인식 하는 페이지에 필요한 @ Register 지시문을 만듭니다. 이제 컨트롤의 공용 속성 및 메서드와 함께 사용할 수 있습니다.

 사용자 정의 컨트롤을 웹 파트에 포함 하려면 웹 파트를 사용자 정의 컨트롤 추가 <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> 웹 파트 코드 파일의 컬렉션입니다. 다음 예제에서는 사용자 컨트롤을 추가 합니다 <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> 웹 파트의 컬렉션입니다.

 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]

## <a name="debug-a-user-control"></a>사용자 컨트롤 디버그
 사용자 정의 컨트롤을 디버깅 하려면 SharePoint 프로젝트에 사용자 정의 컨트롤을 응용 프로그램 페이지 또는 웹 파트에 포함 되어 있는지 확인 합니다. 그런 다음 Visual Studio 프로젝트에서 코드를 디버그할 때 처럼 사용자 정의 컨트롤에서 코드를 디버깅할 수 있습니다.

 Visual Studio 디버거를 시작 하면 Visual Studio에 SharePoint 사이트가 열립니다.

 SharePoint에서 사용자 정의 컨트롤을 포함 하는 응용 프로그램 페이지를 엽니다. 사용자 정의 컨트롤은 웹 파트에 포함 하는 경우 sharepoint에서 웹 파트 페이지로 웹 파트를 추가 합니다.

 SharePoint 프로젝트를 디버깅 하는 방법에 대 한 자세한 내용은 참조 하십시오 [문제를 해결 하는 SharePoint 솔루션](../sharepoint/troubleshooting-sharepoint-solutions.md)합니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[방법: SharePoint 응용 프로그램 페이지 또는 웹 파트에 대 한 사용자 정의 컨트롤 만들기](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|응용 프로그램 페이지 및 SharePoint에서 실행 되는 웹 파트에서 사용할 수 있는 재사용 가능한 사용자 지정 컨트롤을 만드는 방법을 보여 줍니다.|
