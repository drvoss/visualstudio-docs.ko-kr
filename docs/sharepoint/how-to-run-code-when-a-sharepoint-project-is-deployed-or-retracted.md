---
title: SharePoint 프로젝트가 배포 되거나 취소 하는 경우 코드를 실행 합니다.
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9e3f46ff9d2e83307f745180288e69839a0d336e
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401769"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>방법: SharePoint 프로젝트는 배포 되거나 취소 될 때 코드를 실행 합니다.
  SharePoint 프로젝트는 배포 되거나 취소 될 때 추가 작업을 수행 하려는 경우에 Visual Studio에서 발생 하는 이벤트를 처리할 수 있습니다. 자세한 내용은 [확장 SharePoint 패키징 및 배포](../sharepoint/extending-sharepoint-packaging-and-deployment.md)합니다.

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>시 SharePoint 프로젝트 코드를 실행 하려면 배포 되거나 취소

1. 프로젝트 항목 확장, 프로젝트 확장명을 또는 새 프로젝트 항목 형식의 정의 만듭니다. 자세한 내용은 다음 항목을 참조하세요.

   - [방법: SharePoint 프로젝트 항목 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [방법: SharePoint 프로젝트 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. 확장에 액세스 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 개체입니다. 자세한 내용은 [방법: SharePoint 프로젝트 서비스 검색](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)합니다.

3. 처리를 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> 고 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> 프로젝트 서비스의 이벤트입니다.

4. 이벤트 처리기를 사용 하 여는 <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> 매개 변수로 현재 배포 세션에 대 한 정보를 가져올 수 있습니다. 예를 들어, 현재 배포 세션에 있는 프로젝트를 및 되 여부를 확인할 수 있습니다 배포 되거나 취소 합니다.

   다음 코드 예제에서는 처리 하는 방법에 설명 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> 및 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> 프로젝트 확장에는 이벤트입니다. 이 확장에 추가 메시지를 씁니다 합니다 **출력** 창 배포가 시작 되 고 SharePoint 프로젝트에 대 한 완료 합니다.

   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요합니다.

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 확장 배포를 만들려면를 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 파일에 대 한 패키지 (VSIX) 확장 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구의 확장을 배포할](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [방법: 배포 단계를 실행할 때 코드를 실행 합니다.](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
