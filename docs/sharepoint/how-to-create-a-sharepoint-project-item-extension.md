---
title: '방법: SharePoint 프로젝트 항목 확장명 만들기 | Microsoft Docs'
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
ms.openlocfilehash: c46b629227b1b3d73ee4bc6a265c867921937df2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966965"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>방법: SharePoint 프로젝트 항목 확장명 만들기
  Visual Studio에서 이미 설치 되어 있는 SharePoint 프로젝트 항목에 기능을 추가 하려는 경우 프로젝트 항목 확장을 만듭니다. 자세한 내용은 [확장 SharePoint 프로젝트 항목](../sharepoint/extending-sharepoint-project-items.md)합니다.

### <a name="to-create-a-project-item-extension"></a>프로젝트 항목 확장을 만들려면

1. 클래스 라이브러리 프로젝트를 만듭니다.

2. 다음 어셈블리에 대한 참조를 추가합니다.

    - Microsoft.VisualStudio.SharePoint

    - System.ComponentModel.Composition

3. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 인터페이스를 구현하는 클래스를 만듭니다.

4. 클래스에 다음 특성을 추가 합니다.

    - <xref:System.ComponentModel.Composition.ExportAttribute>. 이 특성을 검색 하 고 로드 되도록 Visual Studio를 사용 하면 프로그램 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 구현 합니다. 전달 된 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 특성 생성자에는 형식입니다.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. 프로젝트 항목 확장에서이 특성을 확장 하려면 프로젝트 항목을 식별 합니다. 특성 생성자에 프로젝트 항목의 ID를 전달 합니다. Visual Studio를 사용 하 여 포함 된 프로젝트 항목의 id 목록에 대해서 [확장 SharePoint 프로젝트 항목](../sharepoint/extending-sharepoint-project-items.md)합니다.

5. 구현에서의 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 메서드를 사용 하 여 멤버를 *projectItemType* 확장 프로그램의 동작을 정의 하는 매개 변수입니다. 이 매개 변수는 프로그램 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 에 정의 된 이벤트에 대 한 액세스를 제공 하는 개체를 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 및 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> 인터페이스. 특정 인스턴스를 확장 하는 프로젝트 항목 형식에 액세스 하려면 처리 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> 와 같은 이벤트 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> 고 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>입니다.

## <a name="example"></a>예제
 다음 코드 예제에는 이벤트 수신기 프로젝트 항목에 대 한 간단한 확장 프로그램을 만드는 방법을 보여 줍니다. 될 때마다 SharePoint 프로젝트에 이벤트 수신기 프로젝트 항목을 추가 하는 사용자를이 확장 기록에 메시지를 **출력** 창 및 **오류 목록** 창입니다.

 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]

 SharePoint 프로젝트 서비스를 사용 하 여 메시지를 작성 하는이 예제는 **출력** 창 및 **오류 목록** 창입니다. 자세한 내용은 [SharePoint 프로젝트 서비스를 사용 하 여](../sharepoint/using-the-sharepoint-project-service.md)입니다.

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요합니다.

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 확장 배포를 만들려면를 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 파일에 대 한 패키지 (VSIX) 확장 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)
- [연습: SharePoint 프로젝트 항목 형식 확장](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
