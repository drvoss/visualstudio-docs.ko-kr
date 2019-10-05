---
title: SharePoint를 위한 페이지 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f58af55b18d7cd6341b779d71da2994875c98a62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62419891"
---
# <a name="create-pages-for-sharepoint"></a>SharePoint에 대 한 페이지 만들기
  응용 프로그램 페이지, 사이트 페이지, 마스터 페이지 및 SharePoint 사이트에 대 한 페이지 레이아웃을 만들 수 있습니다.

 Visual Studio에서 템플릿을 사용 하 여 응용 프로그램 페이지를 만들 수 있습니다. SharePoint Designer를 사용 하 여 사이트 페이지, 마스터 페이지 및 페이지 레이아웃을 만듭니다. 그런 다음 SharePoint 프로젝트에서 사용 하려면 Visual Studio로 이러한 페이지를 가져올 수 있습니다.

 스타일 시트, ECMAScript, 및 테마를 사용 하 여 페이지의 동작과 모양을 수정할 수 있습니다.

## <a name="types-of-sharepoint-pages"></a>SharePoint 페이지 형식
 다음 표에서 SharePoint 사이트를 포함 하는 페이지의 네 가지 기본 유형을 설명 합니다.

|페이지 유형|설명|
|---------------|-----------------|
|응용 프로그램 페이지|사용자 지정 코드를 포함 하도록 페이지를 원하는 경우 여러 사이트 간에 공유 될 페이지를 원하는 응용 프로그램 페이지를 만듭니다. 그렇지 않으면 사이트 페이지 적합 수 있습니다.|
|사이트 페이지|다음 작업을 수행 하려는 경우에 사이트 페이지를 만듭니다.<br /><br /> -SharePoint 라이브러리에 페이지를 추가 합니다.<br />-동적 웹 파트와 웹 파트 영역을 같은 호스트 기능 페이지를 사용 하도록 설정 합니다.<br />-사용자가 SharePoint Designer를 사용 하 여 페이지를 사용자 지정할 수 있게 합니다.<br /><br /> 사용자 지정 코드를 포함 하도록 페이지를 원하는 경우 사이트 페이지를 만들지 마십시오. 사용자 지정 코드를 사이트 페이지에 추가할 수 있지만 코드 사용자가 SharePoint Designer를 사용 하 여 페이지를 사용자 지정 실행이 중지 됩니다.|
|마스터 페이지|사이트 페이지에 대 한 일반적인 구조를 정의 하려는 경우 마스터 페이지 및 응용 프로그램 페이지를 만듭니다.|
|페이지 레이아웃|페이지 레이아웃에 따라 다릅니다 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 추가로 사이트 페이지 및 응용 프로그램 페이지에 대 한 공통 구조를 정의할 수 있습니다.|

 각 페이지 유형의 개요를 참조 하세요. [문서 블록: 페이지 및 사용자 인터페이스](http://go.microsoft.com/fwlink/?LinkID=182095), 및 [페이지 레이아웃 및 마스터 페이지](http://go.microsoft.com/fwlink/?LinkID=182096)합니다.

## <a name="create-application-pages"></a>응용 프로그램 페이지 만들기
 추가 하 여 Visual Studio에서 응용 프로그램 페이지를 만들 수는 **응용 프로그램 페이지** SharePoint 프로젝트 항목입니다. 페이지에 컨트롤을 추가 하 고 코드를 추가 하 여 컨트롤 이벤트를 처리할 수 있습니다.

 페이지의 코드 파일에서 중단점을 설정 하 고, 디버거를 시작 하 고, 추가 구성 단계를 수행 하지 않고 로컬 SharePoint 사이트의 페이지를 테스트할 수 있습니다. 자세한 내용은 [SharePoint 용 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)합니다.

## <a name="create-site-pages-master-pages-and-page-layouts"></a>사이트 페이지, 마스터 페이지 및 페이지 레이아웃 만들기
 SharePoint Designer를 사용 하 여 사이트 페이지, 마스터 페이지 및 페이지 레이아웃을 만들 수 있습니다. 그런 다음 Visual Studio로 이러한 페이지를 가져올 수 있습니다. 배포 또는 Visual Studio에서 사용할 수 있는 소스 제어 기능을 활용 하려는 경우 페이지를 가져옵니다. 자세한 내용은 [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)합니다.

 가져오기 후이 페이지를 수정 하기 어려운 이기 때문에 가져오기 전에 이러한 페이지를 디자인 해야 합니다.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>스타일 시트, ECMAScript, 및 테마 만들기
 Visual Studio 개발 스타일 시트 (CSS), ECMAScript (JavaScript, JScript) 또는 SharePoint 사이트에 대 한 테마 파일에 대 한 템플릿을 제공 하지 않습니다. SharePoint SDK에서 사용할 수 있는 지침을 사용 하 여 또는 SharePoint Designer와 같은 도구를 사용 하 여 이러한 파일을 만들 수 있습니다.

 솔루션에 이러한 파일 직접 추가 하거나 가져올 수 있습니다. 두 경우 모두 추가 하는 각 항목에 대 한 적절 한 매핑된 폴더를 만들어야 합니다. 매핑된 폴더를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [방법: 매핑된 폴더 추가 및 제거](../sharepoint/how-to-add-and-remove-mapped-folders.md)합니다.

 연계 스타일 시트를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [SharePoint Foundation에서 스타일 시트 클래스 사용 연계](http://go.microsoft.com/fwlink/?LinkID=182098)합니다. SharePoint 솔루션에 대 한 JavaScript 및 JScript 파일을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [설정 하는 기본 ASPX 페이지 ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099)합니다. 테마에 대 한 자세한 내용은 참조 하세요. [문서 블록: 페이지 및 사용자 인터페이스](http://go.microsoft.com/fwlink/?LinkID=182095)합니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[SharePoint 용 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)|응용 프로그램 페이지를 추가 하는 방법에 설명 합니다. *.aspx* SharePoint 마스터 페이지를 사용 하 여 병합 되는 콘텐츠입니다.|
|[방법: 응용 프로그램 페이지 만들기](../sharepoint/how-to-create-an-application-page.md)|SharePoint 사이트에서 실행 되는 ASP.NET 페이지를 만드는 방법을 보여 줍니다.|
|[연습: SharePoint 응용 프로그램 페이지 만들기](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|디자인 하 고 SharePoint 사이트에 대 한 ASP.NET 웹 페이지를 디버그 하는 방법을 보여 줍니다.|
