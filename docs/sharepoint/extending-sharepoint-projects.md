---
title: SharePoint 프로젝트 확장 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6bc92d65ed179c7f2cb2f569a7d254a025887845
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967483"
---
# <a name="extend-sharepoint-projects"></a>SharePoint 프로젝트 확장
  SharePoint 프로젝트의 프로젝트 수준 기능을 사용자 지정 하려는 경우 프로젝트 확장을 만듭니다. 예를 들어, 사용자 지정 프로젝트 속성을 추가할 수도 있고 사용자는 Visual Studio에서 SharePoint 솔루션을 개발 하는 경우 발생 하는 프로젝트 수준 이벤트에 응답할 수 있습니다.

## <a name="create-project-extensions"></a>프로젝트 확장명 만들기
 프로젝트 항목을 확장 하려면 구현 하는 Visual Studio 확장 프로그램 어셈블리를 빌드하는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 인터페이스입니다. 자세한 내용은 [방법: SharePoint 프로젝트 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)합니다.

 프로젝트 확장을 만들 때 SharePoint 프로젝트에도 다음과 같은 기능을 추가할 수 있습니다.

- 바로 가기 메뉴 항목을 추가 합니다. 메뉴 항목에서 SharePoint 프로젝트 노드에 대 한 바로 가기 메뉴를 열면 나타납니다 **솔루션 탐색기** 노드를 마우스 오른쪽 단추로 클릭 하거나 선택 하 고 선택 합니다 **Shift** +  **F10** 키입니다. 자세한 내용은 [방법: 바로 가기 메뉴 항목을 SharePoint 프로젝트에 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)합니다.

- 사용자 지정 속성을 추가 합니다. 속성에 표시 된 **속성** 창에서 SharePoint 프로젝트를 선택 하면 **솔루션 탐색기**합니다. 자세한 내용은 [방법: SharePoint 프로젝트에 속성 추가](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)합니다.

  만들기, 배포 및 프로젝트 확장을 테스트 하는 방법을 보여주는 연습을 참조 하세요. [연습: SharePoint 프로젝트 확장명 만들기](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)합니다.

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>프로젝트 확장 및 프로젝트 인스턴스 간의 관계를 이해
 확장 로드에서 모든 종류의 SharePoint 프로젝트를 열면 프로젝트 확장을 만들면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 목록 정의 콘텐츠 형식 및 이벤트 수신기와 같은 여러 SharePoint 프로젝트 템플릿이 포함 되어 있습니다. 그러나 SharePoint 프로젝트 유형이 하나만 있습니다. 에 표시 되는 프로젝트 형식은 합니다 **새 프로젝트** 대화 상자는 하나 이상의 SharePoint 프로젝트 항목을 묶어 템플릿만 합니다. 하나의 SharePoint 프로젝트 형식에 있기 때문에 하나의 프로젝트에 대해 생성 하는 확장 모든 SharePoint 프로젝트에 적용 됩니다. 예를 들어만 적용 되는 확장을 만들 수는 없습니다는 **Content-type** 프로젝트입니다.

 인스턴스를 특정 프로젝트에 액세스 하려면 중 하나를 처리 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> 의 이벤트를 *projectService* 구현에서 매개 변수는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 메서드. 예를 들어 솔루션에 SharePoint 프로젝트를 추가 하는 경우를 확인 하려면 처리는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> 이벤트입니다. 자세한 내용은 [방법: SharePoint 프로젝트 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)합니다.

## <a name="see-also"></a>참고자료
- [방법: SharePoint 프로젝트 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [방법: 바로 가기 메뉴 항목을 SharePoint 프로젝트에 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [방법: SharePoint 프로젝트에 속성 추가](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [연습: SharePoint 프로젝트 확장명 만들기](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
