---
title: '방법: SharePoint 프로젝트 서비스 검색 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 75caa29d90b41dc696ce586d50928b2adb0875f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813431"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>방법: SharePoint 프로젝트 서비스 검색
  SharePoint 프로젝트 서비스는 다음 형식의 솔루션에 액세스할 수 있습니다.

- SharePoint 프로젝트 시스템 확장 프로젝트, 프로젝트 항목 확장 프로젝트 항목 형식 정의 등의 확장입니다. 이러한 유형의 확장에 대 한 자세한 내용은 참조 하세요. [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)합니다.

- 확장 된 **SharePoint 연결** 노드에서 **서버 탐색기**합니다. 이러한 유형의 확장에 대 한 자세한 내용은 참조 하세요. [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)합니다.

- Visual Studio 확장 기능, VSPackage 등의 다른 형식입니다.

## <a name="retrieve-the-service-in-project-system-extensions"></a>프로젝트 시스템 확장에서 서비스 검색
 SharePoint 프로젝트 시스템의 모든 확장에서 사용 하 여 프로젝트 서비스에 액세스할 수 있습니다 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> 의 속성을 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 개체입니다.

 또한 다음 절차를 사용 하 여 프로젝트 서비스를 검색할 수 있습니다.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>프로젝트 확장에서 서비스를 검색

1. 구현에는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 인터페이스를 찾습니다는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> 메서드.

2. 사용 된 *projectService* 매개 변수를 서비스에 액세스 합니다.

     다음 코드 예제에서는 프로젝트 서비스를 사용 하 여 메시지를 쓸 하는 방법에 설명 합니다 **출력** 창 및 **오류 목록** 간단한 프로젝트 확장에는 창입니다.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]

     프로젝트 확장을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [방법: SharePoint 프로젝트 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)합니다.

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>프로젝트 항목 확장에서 서비스를 검색

1. 구현에는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 인터페이스를 찾습니다는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> 메서드.

2. 사용 하 여는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> 의 속성을 *projectItemType* 매개 변수는 서비스를 검색 합니다.

     다음 코드 예제에서는 프로젝트 서비스를 사용 하 여 메시지를 쓸 하는 방법에 설명 합니다 **출력** 창 및 **오류 목록** 의 간단한 확장에는 창은 **목록 정의** 프로젝트 항목입니다.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]

     프로젝트 항목 확장을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [방법: SharePoint 프로젝트 항목 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)합니다.

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>프로젝트 항목 형식 정의에서 서비스를 검색 하려면

1. 구현에는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 인터페이스를 찾습니다는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 메서드.

2. 사용 하 여는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> 의 속성을 *typeDefinition* 매개 변수는 서비스를 검색 합니다.

     다음 코드 예제에서는 프로젝트 서비스를 사용 하 여 메시지를 쓸 하는 방법에 설명 합니다 **출력** 창 및 **오류 목록** 간단한 프로젝트 항목 형식 정의에 창.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]

     프로젝트 항목 형식 정의 대 한 자세한 내용은 참조 하세요. [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)합니다.

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>서버 탐색기 확장에서 서비스 검색
 확장에는 **SharePoint 연결** 에서 노드 **서버 탐색기**를 사용 하 여 프로젝트 서비스에 액세스할 수 있습니다를 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> 속성은 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> 개체입니다.

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>서버 탐색기 확장에서 서비스를 검색 하려면

1. 가져오기는 <xref:System.IServiceProvider> 에서 개체를 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> 의 속성을 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> 확장의 개체입니다.

2. 사용 하 여는 <xref:System.IServiceProvider.GetService%2A> 요청 하는 메서드는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 개체입니다.

     다음 코드 예제에서는 프로젝트 서비스를 사용 하 여 메시지를 쓸 하는 방법에 설명 합니다 **출력** 창 및 **오류 목록** 의목록노드를확장을추가하는바로가기메뉴에서창**서버 탐색기**합니다.

     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]

     확장에 대 한 자세한 내용은 합니다 **SharePoint 연결** 에서 노드 **서버 탐색기**를 참조 [방법: 서버 탐색기에서 SharePoint 노드 확장](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)합니다.

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>다른 Visual Studio 확장에서 서비스 검색
 프로젝트 서비스, VSPackage 또는 액세스할 수 있는 모든 Visual Studio 확장을 검색할 수 있습니다는 <xref:EnvDTE80.DTE2> 자동화 개체 모델을 구현 하는 프로젝트 템플릿 마법사와 같은 개체를 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 인터페이스입니다.

 Vspackage를 요청할 수 있습니다는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 다음 방법 중 하나를 사용 하 여 개체:

- 합니다 <xref:System.IServiceProvider.GetService%2A> 에서 파생 되는 관리 되는 VSPackage의 메서드는 <xref:Microsoft.VisualStudio.Shell.Package> 클래스입니다. 자세한 내용은 [방법: 서비스 가져오기](../extensibility/how-to-get-a-service.md)합니다.

- 정적 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 메서드. 자세한 내용은 [사용 하 여 GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice)합니다.

  액세스할 수 있는 Visual Studio 확장에서를 <xref:EnvDTE80.DTE2> 개체를 요청할 수 있습니다는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 사용 하 여 개체를 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 메서드의 <xref:Microsoft.VisualStudio.Shell.ServiceProvider> 개체입니다. 자세한 내용은 [DTE 개체에서 서비스를 가져오는](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)
- [방법: 서비스 가져오기](../extensibility/how-to-get-a-service.md)
- [방법: 프로젝트 템플릿에 마법사 사용](../extensibility/how-to-use-wizards-with-project-templates.md)
