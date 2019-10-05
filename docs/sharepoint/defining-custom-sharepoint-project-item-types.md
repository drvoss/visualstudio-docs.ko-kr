---
title: 사용자 지정 SharePoint 프로젝트 항목 형식 정의 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e5f32abba4c4cbdeab59ed66e38019d913e704e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62580786"
---
# <a name="define-custom-sharepoint-project-item-types"></a>사용자 지정 SharePoint 프로젝트 항목 형식 정의
  SharePoint 프로젝트 항목의 새 종류를 하려는 경우 새 SharePoint 프로젝트 항목 형식을 정의 합니다. 예를 들어, Visual Studio는 추가 필드 또는 SharePoint 사이트에 사용자 지정 작업에 대 한 SharePoint 프로젝트 항목을 포함 되지 않습니다. 필드, 사용자 지정 작업 또는 다른 유형의 SharePoint 구성 요소를 만들기 위한 SharePoint 프로젝트 항목의 고유한 형식을 정의할 수 있습니다.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>SharePoint 프로젝트 항목 형식 정의 대 한 작업
 사용자 지정 프로젝트 항목 형식 정의 구현 하는 Visual Studio 확장 프로그램 어셈블리를 빌드는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 인터페이스입니다. 자세한 내용은 [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)합니다.

 사용자 지정 프로젝트 항목 형식을 정의 하는 경우 프로젝트 항목에도 다음과 같은 기능을 추가할 수 있습니다.

- 프로젝트 항목에 바로 가기 메뉴 항목을 추가 합니다. 메뉴 항목에서 해당 프로젝트 항목에 대 한 바로 가기 메뉴를 열면 나타납니다 **솔루션 탐색기** 프로젝트 항목을 마우스 오른쪽 단추로 클릭 하거나 선택한 다음,이 선택 합니다 **Shift** +  **F10** 키입니다. 자세한 내용은 [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 바로 가기 메뉴 항목 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)합니다.

- 프로젝트 항목에 사용자 지정 속성을 추가 합니다. 속성에 표시 된 **속성** 창에서 프로젝트 항목을 선택 하면 **솔루션 탐색기**합니다. 자세한 내용은 [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 속성 추가](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)합니다.

  다른 개발자가 Visual Studio에서 프로젝트 항목을 사용할 수 있도록.spdata 파일 만들기 및 항목 템플릿 또는 프로젝트 항목에 연관 된 프로젝트 템플릿을 만듭니다. 자세한 내용은 [항목 템플릿 및 SharePoint 프로젝트 항목에 대 한 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)합니다.

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>프로젝트 항목 형식 및 프로젝트 항목 인스턴스 간의 관계를 이해
 SharePoint 프로젝트 항목 형식을 정의 하는 경우 연결 된 형식의 프로젝트 항목을 SharePoint 프로젝트에 추가 되 면 Visual Studio 확장을 로드 합니다. 예를 들어 새 정의한 **사용자 지정 동작** 프로젝트 항목 형식, 사용자를 추가 하는 경우 Visual Studio 확장을 로드를 **사용자 지정 작업** 프로젝트에 프로젝트 항목입니다. Visual Studio 연결 된 프로젝트 항목 형식의 모든 인스턴스에 대 한 확장 프로그램의 동일한 인스턴스를 사용합니다. 이전 예제에서는 사용자가 두 번째 추가 하는 경우 **사용자 지정 작업** 프로젝트에 프로젝트 항목, 확장 프로그램의 동일한 인스턴스에 두 번째 프로젝트 항목을 사용 합니다.

 프로젝트 항목 형식의 특정 인스턴스에 액세스 하려면 중 하나를 처리 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 의 이벤트를 *projectItemTypeDefinition* 구현에서 매개 변수는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 메서드. 예를 들어, 사용자 지정 형식의 프로젝트 항목을 프로젝트에 추가 하는 경우를 확인 하려면 처리는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 이벤트입니다. 자세한 내용은 [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)합니다.

## <a name="see-also"></a>참고자료
- [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 속성 추가](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 바로 가기 메뉴 항목 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [SharePoint 프로젝트 항목에 대 한 프로젝트 템플릿과 항목 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [연습: 항목 템플릿, 1 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [연습: 1 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [연습: 항목 템플릿, 2 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [연습: 2 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
