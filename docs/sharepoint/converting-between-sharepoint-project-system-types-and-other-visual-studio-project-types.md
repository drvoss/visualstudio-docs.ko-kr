---
title: 변환 합니다. 다른 형식에서 SharePoint 프로젝트 시스템 형식
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
ms.openlocfilehash: 40ea60a8df5bc0bcd033c60a83d742ed3249cc53
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835993"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>SharePoint 프로젝트 시스템 형식과 기타 Visual Studio 프로젝트 형식 간의 변환
  일부 경우에는 개체 SharePoint 프로젝트 시스템에 있을 수 있습니다 및 Visual Studio 자동화 개체 모델 또는 통합 개체 모델에서 해당 개체의 기능을 사용 하려는 또는 그 반대의 경우도 마찬가지입니다. 이러한 경우에 사용할 수는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 다른 개체 모델에 개체를 변환 하 여 SharePoint 프로젝트 서비스의 메서드.

 예를 들어 있을 수 있습니다는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 에 사용할 수 있는 메서드는 데 사용할 수 있지만 개체를 <xref:EnvDTE.Project> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> 개체입니다. 이 경우 사용할 수 있습니다는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 변환할 메서드를 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 에 <xref:EnvDTE.Project> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.

 Visual Studio 자동화 개체 모델 및 Visual Studio 통합 개체 모델에 대 한 자세한 내용은 참조 하세요. [SharePoint의 프로그래밍 모델 개요 도구 확장](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)합니다.

## <a name="types-of-conversions"></a>형식 변환
 다음 표에서이 메서드는 SharePoint 프로젝트 시스템 및 다른 Visual Studio 개체 모델 간의 변환 될 수 있는 형식을 나열 합니다.

|SharePoint 프로젝트 시스템 형식|자동화 및 통합 개체 모델의 해당 형식|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> 또는<br /><br /> 프로젝트에 대 한 기본 COM 개체에 의해 구현 되는 Visual Studio 통합 개체 모델에서 모든 인터페이스입니다. 이러한 인터페이스를 포함 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (또는 파생 된 인터페이스) 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>합니다. 프로젝트에서 구현 되는 기본 인터페이스의 목록을 참조 하세요 [프로젝트 모델 핵심 구성 요소](../extensibility/internals/project-model-core-components.md)합니다.|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> 또는<br /><br /> <xref:System.UInt32> 에서 프로젝트 멤버를 식별 하는 VSITEMID 라고도 하는 값은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 해당 항목을 포함 합니다. 이 값을 전달할 수는 *itemid* 일부 매개 변수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 메서드.|

## <a name="example"></a>예제
 다음 코드 예제에 사용 하는 방법을 보여 줍니다.는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 변환할 메서드는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 개체를 <xref:EnvDTE.Project>합니다.

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 이 예제에는 다음 사항이 필요합니다.

- 에 대 한 참조가 있는 SharePoint 프로젝트 시스템의 확장을 *EnvDTE.dll* 어셈블리입니다. 자세한 내용은 [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)합니다.

- 등록 하는 코드를 `projectService_ProjectAdded` 처리 하는 메서드를 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> 의 이벤트는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 개체입니다. 예는 [방법: SharePoint 프로젝트 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)합니다.

## <a name="see-also"></a>참고자료

- [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)
- [방법: SharePoint 프로젝트 서비스 검색](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [SharePoint의 프로그래밍 모델 개요 도구 확장](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
