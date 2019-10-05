---
title: SharePoint 용 응용 프로그램 페이지 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8ac9340ea853a1852d039f05a3ecbb100845ab84
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443548"
---
# <a name="create-application-pages-for-sharepoint"></a>SharePoint 용 응용 프로그램 페이지 만들기
  *응용 프로그램 페이지* SharePoint 웹 사이트에서 사용 하기 위해 설계 된 ASP.NET 웹 페이지입니다. 응용 프로그램 페이지는 ASP.NET 페이지의 특수화 된 형식입니다. 응용 프로그램 페이지 및 표준 ASP.NET 페이지 간의 주요 차이점은 응용 프로그램 페이지는 SharePoint 마스터 페이지를 사용 하 여 병합 되는 콘텐츠를 포함 합니다. 마스터 페이지를는 응용 프로그램 페이지를 사이트에서 다른 페이지와 동일한 모양 및 동작을 공유할 수 있습니다.

 Visual Studio를 사용 하면 디자이너를 사용 하 여 응용 프로그램 페이지를 디자인할 수 있습니다. 디자이너는 마스터 페이지에 정의 된 각 콘텐츠 자리 표시자에 대 한 콘텐츠 영역을 표시 합니다. 이러한 콘텐츠 영역에 컨트롤을 끌어 응용 프로그램 페이지를 디자인할 수 있습니다.

## <a name="application-pages"></a>응용 프로그램 페이지
 응용 프로그램 페이지는 반면 사이트 페이지는 한 사이트에 특정 서버의 모든 사이트에서 공유 됩니다. 자세한 내용은 [SharePoint 페이지 형식](http://go.microsoft.com/fwlink/?LinkID=211584)합니다.

 기본적으로 대부분의 SharePoint 사이트를 만들 때 표시 되는 페이지는 사이트 페이지입니다. 사이트 페이지를 SharePoint 페이지 라이브러리에 추가할 수 있습니다. 사용자가 SharePoint Designer와 같은 도구를 사용 하 여 사이트 페이지를 사용자 지정할 수 있습니다. 사이트 페이지에서 동적 웹 파트와 웹 파트 영역 등의 기능을 호스팅할 수도 있습니다.

 응용 프로그램 페이지는 이러한 작업을 수행할 수 없습니다. 그러나 응용 프로그램 페이지는 가장 적합 한 유형의 사용자 지정 코드를 포함 하도록 페이지를 원하는 경우 만들려면 페이지입니다. 사용자 지정 코드를 사이트 페이지에 추가할 수 있지만 코드 사용자가 SharePoint Designer와 같은 도구를 사용 하 여 페이지를 사용자 지정 실행이 중지 됩니다.

> [!NOTE]
> Visual Studio에서는 도움이 되는 템플릿은 SharePoint 사이트에 대 한 사이트 페이지를 만듭니다. 자세한 내용은 [SharePoint 페이지 형식](http://go.microsoft.com/fwlink/?LinkID=211584)합니다.

## <a name="create-an-application-page"></a>응용 프로그램 페이지 만들기
 응용 프로그램 페이지를 만들려면 추가 **응용 프로그램 페이지** SharePoint 프로젝트 항목입니다. 응용 프로그램 페이지를 만들면 Visual Studio 프로젝트에 다음 폴더를 추가 합니다.

|폴더|설명|
|------------|-----------------|
|레이아웃|SharePoint 파일 시스템의 레이아웃 가상 디렉터리에 매핑됩니다.|
|레이아웃 하위 폴더|응용 프로그램 페이지를 구성 하는 파일을 포함 합니다. 기본적으로이 폴더에 프로젝트와 동일한 이름이 있습니다. 언제 든 지가이 폴더를 바꿀 수 있습니다. 프로젝트를 실행 하면 Visual Studio SharePoint 파일 시스템의 _layouts 가상 디렉터리에이 폴더를 배포 합니다.|

 Visual Studio 프로젝트에 다음 파일을 추가합니다.

|파일|설명|
|----------|-----------------|
|ASP.NET 페이지 파일 (*.aspx*)|페이지를 정의 하는 XML 태그를 포함 합니다.|
|응용 프로그램 페이지 코드 파일|코드 숨김 응용 프로그램 페이지를 포함합니다. 이 파일에 이벤트를 처리 하는 코드를 추가 합니다.|
|응용 프로그램 페이지 디자이너 코드 파일|디자이너에서 생성 되는 코드를 포함 합니다. 이 파일을 직접 편집 하지 마십시오.|

## <a name="design-and-debug-an-application-page"></a>디자인 및 디버깅 응용 프로그램 페이지
 Visual Studio에서 디자이너 뷰를 사용 하 여 응용 프로그램 페이지의 콘텐츠를 디자인 합니다. 이 디자이너는 프로젝트에서 응용 프로그램 페이지를 열면 나타납니다 (두 번 클릭 하거나 바로 가기 메뉴를 열고 다음 **엽니다**)를 선택 합니다 **디자인** 아래쪽의 단추 편집기입니다.

> [!NOTE]
> 페이지를 디자인할 수에 합니다 **원본** 디자이너의 뷰. 합니다 **디자인** 응용 프로그램 페이지 디자이너의 뷰를 사용할 수 없게 됩니다.

 Visual Studio의 다른 SharePoint 프로젝트 항목을 디버그할 때 처럼 응용 프로그램 페이지를 디버깅할 수 있습니다. Visual Studio 디버거를 시작 하면 Visual Studio에 SharePoint 사이트가 열립니다.

 응용 프로그램 페이지를 보려면 응용 프로그램 페이지의 위치로 이동 수동으로 해야 합니다 (예: http://<em>Server_Name</em>/_layouts/*Project_Name*/ApplicationPage1.aspx).

 SharePoint 프로젝트를 디버깅 하는 방법에 대 한 자세한 내용은 참조 하십시오 [문제를 해결 하는 SharePoint 솔루션](../sharepoint/troubleshooting-sharepoint-solutions.md)합니다.

## <a name="choose-a-master-page"></a>마스터 페이지를 선택 합니다.
 기본적으로 **응용 프로그램 페이지** 항목 프로젝트를 디버깅 하는 데 사용 하는 사이트의 마스터 페이지를 참조 합니다. 페이지 이름이 v4.master 하에 나열 된 찾을 수 있습니다 합니다 **마스터 페이지 갤러리** SharePoint 사이트의.

 설정 하 여 응용 프로그램 페이지에서 사용 되는 마스터 페이지를 명시적으로 변경할 수는 `MasterPageFile` 응용 프로그램의 특성 `Page` 요소입니다. (예: `MasterPageFile="~/_layouts/applicationv4.master"`). 사실 동적 마스터 페이지는 SharePoint 서버에서 사용할 수 없는 경우이 특성을 설정 해야 합니다. SharePoint의 마스터 페이지에 대 한 자세한 내용은 참조 하세요. [마스터 페이지](http://go.microsoft.com/fwlink/?LinkID=169281)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint Foundation 개발 심층 정보](http://go.microsoft.com/fwlink/?LinkID=182103)
- [ASP.NET 개요](/aspnet/overview)
- [ASP.NET 웹 페이지 2](/aspnet/web-pages/index)
