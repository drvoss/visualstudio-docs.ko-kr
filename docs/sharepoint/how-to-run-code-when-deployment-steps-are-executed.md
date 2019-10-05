---
title: '방법: 실행된 코드 배포 단계가 진행 될 때 실행 됩니다 | Microsoft Docs'
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
ms.openlocfilehash: 581f9c0b9907fd59863f6a468a45ef67d9966475
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813154"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>방법: 배포 단계를 실행할 때 코드를 실행 합니다.
  SharePoint 프로젝트의 배포 단계에 대 한 추가 작업을 수행 하려는 경우에 Visual Studio는 각 배포 단계를 실행 한 후 및 하기 전에 SharePoint 프로젝트 항목에 의해 발생 하는 이벤트를 처리할 수 있습니다. 자세한 내용은 [확장 SharePoint 패키징 및 배포](../sharepoint/extending-sharepoint-packaging-and-deployment.md)합니다.

### <a name="to-run-code-when-deployment-steps-are-executed"></a>배포 단계를 실행할 때 코드를 실행 하려면

1. 프로젝트 항목 확장, 프로젝트 확장명을 또는 새 프로젝트 항목 형식의 정의 만듭니다. 자세한 내용은 다음 항목을 참조하세요.

    - [방법: SharePoint 프로젝트 항목 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [방법: SharePoint 프로젝트 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. 확장을 처리 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 및 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> 의 이벤트는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> 개체 (프로젝트 항목 확장 또는 프로젝트 확장명) 또는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> 개체 (새 프로젝트 항목 형식 정의).

3. 이벤트 처리기를 사용 합니다 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> 및 <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> 배포 단계에 대 한 정보를 가져오려면 매개 변수입니다. 예를 들어, 어떤 배포 단계가 실행 되 고 솔루션 되 고 있는지 여부를 확인할 수 있습니다 배포 되거나 취소 합니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 처리 하는 방법에 설명 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> 및 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> 목록 인스턴스 프로젝트 항목에 대 한 확장에는 이벤트입니다. 이 확장 추가 메시지를 기록 합니다 **출력** 배포 및 솔루션을 제거 하는 동안 응용 프로그램 풀을 재생 하는 Visual Studio 창.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요합니다.

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 확장 배포를 만들려면를 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 파일에 대 한 패키지 (VSIX) 확장 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구의 확장을 배포할](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [연습: SharePoint 프로젝트용 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [방법: SharePoint 프로젝트는 배포 되거나 취소 될 때 코드를 실행 합니다.](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
