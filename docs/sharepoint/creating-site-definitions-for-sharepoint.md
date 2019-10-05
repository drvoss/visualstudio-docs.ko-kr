---
title: SharePoint 용 사이트 정의 만들기 | Microsoft Docs
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
ms.openlocfilehash: 2abf61bbc960e342a395e9c0ff3395ecde852137
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62580978"
---
# <a name="create-site-definitions-for-sharepoint"></a>SharePoint 용 사이트 정의 만들기
  SharePoint 사이트 정의 프로젝트 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 만들 수 있습니다를 *사이트 정의*를 새 SharePoint 사이트에 대 한 기반으로 역할을 하는 합니다. 이러한 정의 뿐만 아니라 모양 및 SharePoint 사이트에 있지만 해당 기본 콘텐츠 및 기능 동작을 결정합니다. 정의에서 미리 구성 된 목록, 콘텐츠 형식, 이벤트 수신기, 이미지 및 기타 항목을 넣을 수 있습니다. SharePoint에는 블로그 등의 사이트 정의가 포함되어 있습니다. 블로그 사이트 정의 기반으로 하는 사이트를 만들 때 사이트 목록, 웹 파트 및 사이트를 블로깅 하면서 필요한 기타 항목을 포함 합니다.

 사이트 정의 대 한 자세한 내용은 참조 하세요. [사이트 템플릿 및 정의](http://go.microsoft.com/fwlink/?LinkId=179134)합니다.

## <a name="site-definition-projects"></a>사이트 정의 프로젝트
 사이트 정의 프로젝트에서는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 사이트는 기본 파일만 제공; 기본 기능을 제공 하지 않습니다. 파일 및 원하는 기능을 제공 하는 콘텐츠를 추가 해야 합니다. 만들고 해야 하는 파일을 추가 하 여 사이트를 수동으로 빌드할 수 있습니다.

## <a name="feature-stapling"></a>기능 스테이플링
 사이트 정의 만들 때의 장점은 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 자동으로 사용 한다는 것 *기능 스테이플링*합니다. 기능 스테이플링 자체 사이트 정의에 해당 기능을 포함 하는 대신 사이트 정의에 기능을 연결 합니다. 이렇게 원래 사이트 정의 수정 하지 않고 사이트 정의 사용 하 여 만든 모든 사이트에 기능을 추가할 수 있습니다. 자세한 내용은 [기능 스테이플링](http://go.microsoft.com/fwlink/?LinkID=119283)합니다.

## <a name="site-definition-project-components"></a>사이트 정의 프로젝트 구성 요소
 다음 기본 파일에 추가 됩니다 사이트 정의 솔루션을 만들면 해당 **SiteDefinition** 노드.

|파일 이름|설명|
|---------------|-----------------|
|*default.aspx*|새 SharePoint 사이트에 대 한 기본 ASPX 홈 페이지.|
|*onet.xml*|새 사이트의 구성, 사이트 정의 템플릿 및 기본 동작의 구성 요소를 지정합니다. 이러한 설정은 콘텐츠 형식 사용할 수 있는 기본 목록 보기 문서 템플릿 파일을 같은 특성을 포함 하 고 웹 사이트에 포함 된 파트 수 있습니다. 기본적으로 `Modules` 섹션에서는 SharePoint 사이트 및 구성 하는 방법에 추가할 파일을 나열 합니다.|
|*webtemp_\<SiteDefinitionName>.xml*|에 표시 되는 사이트 정의 구성을 지정 합니다 **템플릿 선택** 섹션을 **새 SharePoint 사이트** 페이지.|

 기본적으로 모든 사이트 정의에 저장 합니다  *\<드라이브: > \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* 폴더입니다. 각 사이트 정의는 자체 하위 폴더를 있습니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[연습: 기본 사이트 정의 프로젝트 만들기](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|기본 사이트 정의 프로젝트를 만드는 과정을 단계별로 안내 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.|
|[방법: 사용자 지정 사이트 정 및 구성 만들기](http://go.microsoft.com/fwlink/?LinkId=183309)|기존 사이트 정의 복사한 다음이 사본을 수정 하 여 SharePoint에서 사용자 지정 사이트 정의 만드는 방법을 설명 합니다.|
|[*WebTemp.xml*](http://go.microsoft.com/fwlink/?LinkId=183310)|사용할 수 있는 사이트 정의 지정 하는 원본 파일에 설명 합니다는 **서식 파일 선택** 섹션을 **새 SharePoint 사이트** 페이지.|
|[SharePoint 솔루션 지역화](../sharepoint/localizing-sharepoint-solutions.md)|전역 사용에 대 한 SharePoint 솔루션을 준비 하는 방법에 설명 합니다.|
|[SharePoint 용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)|사용자가 수정할 수 있는 SharePoint 페이지의 부분을 만드는 방법을 설명 합니다.|
|[웹 파트 또는 응용 프로그램 페이지에 대 한 재사용 가능한 컨트롤 만들기](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|응용 프로그램 페이지 및 웹 파트에서 실행 되는 재사용 가능한 컨트롤을 만드는 방법에 대해 설명 합니다.|
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|프로젝트에서 웹 페이지를 열 때 표시 되는 디자이너를 사용 하는 방법을 설명 합니다.|
|[ASP.NET 웹 페이지 개요](http://go.microsoft.com/fwlink/?LinkId=178726)|구조에 대 한 일반 정보 제공 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 웹 페이지, 페이지를 처리 하 여 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], 방법과 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 페이지 XHTML 표준을 준수 하는 태그를 표시 합니다.|
|[ASP.NET 웹 페이지 구문](http://go.microsoft.com/fwlink/?LinkId=178727)|ASP.NET 페이지를 구성 하는 태그 요소를 설명 합니다.|
|[ASP.NET 웹 페이지 프로그래밍](http://go.microsoft.com/fwlink/?LinkId=178728)|이벤트 처리기를 만드는 방법에 대 한 정보를 제공 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 페이지 및 클라이언트 스크립트를 사용 하는 방법입니다.|
|[Windows SharePoint Services의 프로그래밍](http://go.microsoft.com/fwlink/?LinkId=178729)|제공 되는 관리 되는 개체 모델을 사용 하는 방법에 설명 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]합니다.|

## <a name="see-also"></a>참고자료
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
