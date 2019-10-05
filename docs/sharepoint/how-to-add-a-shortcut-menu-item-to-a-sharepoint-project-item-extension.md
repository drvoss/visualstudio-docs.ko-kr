---
title: SharePoint 프로젝트 항목 확장에 바로 가기 메뉴 항목 추가
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8041f9cbf19d1e1324478b92d2655f1377102b81
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401636"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>방법: SharePoint 프로젝트 항목 확장에 바로 가기 메뉴 항목 추가
  프로젝트 항목 확장을 사용 하 여 기존 SharePoint 프로젝트 항목에 바로 가기 메뉴 항목을 추가할 수 있습니다. 메뉴 항목은 사용자의 프로젝트 항목을 마우스 오른쪽 단추로 클릭 하면 나타납니다 **솔루션 탐색기**합니다.

 다음 단계는 프로젝트 항목 확장을 이미 만들었다고 가정 합니다. 자세한 내용은 [방법: SharePoint 프로젝트 항목 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)합니다.

### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>프로젝트 항목 확장에서 바로 가기 메뉴 항목을 추가 하려면

1. 에 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 메서드의 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 구현, 핸들을 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> 의 이벤트를 *projectItemType* 매개 변수입니다.

2. 에 대 한 이벤트 처리기에서는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> 이벤트를 새 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 개체를 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> 또는 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> 이벤트 인수 매개 변수 컬렉션입니다.

3. 에 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> 새 이벤트 처리기 <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> 개체, 사용자가 바로 가기 메뉴 항목을 클릭할 때 실행 하려는 작업을 수행 합니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 이벤트 수신기 프로젝트 항목에 바로 가기 메뉴 항목을 추가 하는 방법에 설명 합니다. 프로젝트 항목에 단추로 클릭할 때 **솔루션 탐색기** 가 합니다 **출력 창에 메시지 쓰기** 에 메시지를 표시 하는 메뉴 항목을 Visual Studio는 **출력**창.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]

 SharePoint 프로젝트 서비스를 사용 하 여 메시지를 작성 하는이 예제는 **출력** 창입니다. 자세한 내용은 [SharePoint 프로젝트 서비스를 사용 하 여](../sharepoint/using-the-sharepoint-project-service.md)입니다.

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조를 사용 하 여 클래스 라이브러리 프로젝트를 실행 하려면:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 확장 배포를 만들려면를 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 파일에 대 한 패키지 (VSIX) 확장 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구의 확장을 배포할](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="see-also"></a>참고자료
- [방법: SharePoint 프로젝트 항목 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [방법: SharePoint 프로젝트 항목 확장에 속성 추가](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)
- [연습: SharePoint 프로젝트 항목 형식 확장](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
