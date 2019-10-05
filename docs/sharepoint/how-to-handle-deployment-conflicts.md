---
title: '방법: 배포 충돌 처리 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62e7740915d341eee1bbf5e112c4f09297c98be1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813801"
---
# <a name="how-to-handle-deployment-conflicts"></a>방법: 배포 충돌 처리
  SharePoint 프로젝트 항목에 대 한 배포 충돌을 처리 하는 사용자 고유의 코드를 제공할 수 있습니다. 예를 들어, 현재 프로젝트 항목의 모든 파일 배포 위치에 이미 존재 하 고 현재 프로젝트 항목을 배포 하기 전에 다음 배포 된 파일을 삭제 하는지 여부를 확인할 수 있습니다. 배포 충돌에 대 한 자세한 내용은 참조 하십시오 [확장 SharePoint 패키징 및 배포](../sharepoint/extending-sharepoint-packaging-and-deployment.md)합니다.

### <a name="to-handle-a-deployment-conflict"></a>배포 충돌을 처리 하려면

1. 프로젝트 항목 확장, 프로젝트 확장명을 또는 새 프로젝트 항목 형식의 정의 만듭니다. 자세한 내용은 다음 항목을 참조하세요.

    - [방법: SharePoint 프로젝트 항목 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [방법: SharePoint 프로젝트 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. 확장을 처리 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 의 이벤트는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 개체 (프로젝트 항목 확장 또는 프로젝트 확장명) 또는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 개체 (새 프로젝트 항목 형식 정의).

3. 이벤트 처리기에서 배포 되는 프로젝트 항목 및 시나리오에 적용 되는 조건에 따라 SharePoint 사이트에서 배포 된 솔루션 사이 충돌이 있는지 여부를 확인 합니다. 사용할 수는 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> 속성 이벤트 인수 매개 변수를 배포 하는 프로젝트 항목을 분석 하 고이 위해 정의 하는 SharePoint 명령을 호출 하 여 배포 위치에서 파일을 분석할 수 있습니다.

     다양 한 유형의 충돌을 먼저 하려는 확인 배포 단계를 실행 하는 합니다. 사용 하 여이 수행할 수는 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> 이벤트 인수 매개 변수의 속성입니다. 기본 제공 하는 동안 충돌을 감지 하는 것이 일반적으로 있지만 <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> 배포 단계를 확인할 수 있습니다 충돌에 대 한 배포 단계 실행 중입니다.

4. 충돌이 있는 경우 사용 합니다 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> 메서드를 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> 새 이벤트 인수의 속성 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 개체입니다. 이 개체에는 배포 충돌을 나타냅니다. 호출 하 여 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> 메서드를 충돌을 해결 하기 위해 호출 하는 메서드를 지정할 수도 있습니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 목록 정의 프로젝트 항목에 대 한 프로젝트 항목 확장에서 배포 충돌을 처리 하기 위한 기본 프로세스를 보여 줍니다. 다른 형식의 프로젝트 항목에 대 한 배포 충돌을 처리 하려면 다른 문자열을 전달 하 여 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>입니다. 자세한 내용은 [확장 SharePoint 프로젝트 항목](../sharepoint/extending-sharepoint-project-items.md)합니다.

 간단히 하기 위해 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 이 예제의 이벤트 처리기 배포 충돌이 있다고 가정 (즉, 항상 추가 새 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 개체), 및 `Resolve` 메서드는 반환 **true** 나타내는 충돌이 해결 되었습니다. 실제 시나리오에서 사용자 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 이벤트 처리기는 먼저 현재 프로젝트 항목에서 파일과 배포 위치에 파일 간에 충돌이 있는 경우를 확인 한 다음 추가 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> 충돌이 있는 경우에 개체입니다. 예를 들어 사용할 수 있습니다는 `e.ProjectItem.Files` 프로젝트 항목에 파일을 분석 하는 이벤트 처리기의 속성에는 배포 위치에서 파일을 분석 하는 SharePoint 명령을 호출할 수 있습니다. 실제 시나리오에서는 마찬가지로 `Resolve` 메서드는 SharePoint 사이트에서 충돌을 해결 하는 SharePoint 명령을 호출할 수 있습니다. SharePoint 명령 만들기에 대 한 자세한 내용은 참조 하세요. [방법: SharePoint 명령 만들기](../sharepoint/how-to-create-a-sharepoint-command.md)합니다.

 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요합니다.

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 확장 배포를 만들려면를 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 파일에 대 한 패키지 (VSIX) 확장 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구의 확장을 배포할](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)
- [방법: 배포 단계를 실행할 때 코드를 실행 합니다.](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [방법: SharePoint 명령 만들기](../sharepoint/how-to-create-a-sharepoint-command.md)
