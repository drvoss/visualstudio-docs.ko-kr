---
title: '방법: SharePoint 명령 실행 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6f5c285e71179c5dd59fad0357dbf71ee4b32f9d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813891"
---
# <a name="how-to-execute-a-sharepoint-command"></a>방법: SharePoint 명령 실행
  사용자 지정 SharePoint 도구 확장에서 서버 개체 모델을 사용 하려는 경우 만들어야 *SharePoint 명령을* API를 호출 합니다. 명령을 정의 하 고 SharePoint 도구 확장을 통해 배포한 후 확장 프로그램에 SharePoint 서버 개체 모델을 호출 하는 명령을 실행할 수 있습니다. 명령을 실행 하려면의 ExecuteCommand 메서드 중 하나를 사용는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 개체입니다.

 SharePoint 명령의 목적에 대 한 자세한 내용은 참조 하세요. [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)합니다.

### <a name="to-execute-a-sharepoint-command"></a>SharePoint 명령을 실행 하려면

1. SharePoint 도구 확장 프로그램에 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 개체입니다. 가져오는 방법은 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 개체 만들면 확장의 형식에 따라 달라 집니다.

    - SharePoint 프로젝트 시스템의 확장을 사용 하 여는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> 속성입니다.

         프로젝트 시스템 확장에 대 한 자세한 내용은 참조 하세요. [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)합니다.

    - 확장에는 **SharePoint 연결** 노드에서 **서버 탐색기**를 사용 하 여는 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> 속성. 가져올는 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> 개체는 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> 속성입니다.

         에 대 한 자세한 내용은 **서버 탐색기** 확장을 참조 하십시오 [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)합니다.

    - 프로젝트 템플릿 마법사를 사용 하는 등의 SharePoint 도구 확장에 포함 하지 않은 코드에 사용 된 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> 속성입니다.

         프로젝트 서비스 검색에 대 한 자세한 내용은 참조 하세요. [SharePoint 프로젝트 서비스를 사용 하 여](../sharepoint/using-the-sharepoint-project-service.md)입니다.

2. ExecuteCommand 메서드 중 하나를 호출 하 여 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 개체입니다. ExecuteCommand 메서드의 첫 번째 인수를 실행 하려는 명령의 이름을 전달 하세요. 명령 사용자 지정 매개 변수가 있으면 ExecuteCommand 메서드의 두 번째 인수는 매개 변수를 전달 합니다.

     각 지원 되는 명령 서명에 대 한 다른 ExecuteCommand 오버 로드를 있습니다. 다음 표에서 지원 되는 서명 및 각 서명에 사용 하는 오버 로드를 나열 합니다.

    |서명 명령|ExecuteCommand 오버 로드를 사용 하 여|
    |-----------------------|------------------------------------|
    |명령에 기본값만 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 매개 변수 및 반환 값이 없습니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |명령에 기본값만 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 매개 변수 및 반환 값입니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |명령에 두 개의 매개 변수 (기본 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 매개 변수 및 사용자 지정 매개 변수) 및 반환 값이 없습니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |이 명령은 두 개의 매개 변수 및 반환 값에 있습니다.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>예제
 다음 코드 예제를 사용 하는 방법에 설명 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> 오버 로드를 호출 하는 `Contoso.Commands.UpgradeSolution` 에 설명 된 명령을 [하는 방법: SharePoint 명령 만들기](../sharepoint/how-to-create-a-sharepoint-command.md)합니다.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 `Execute` 이 예제에 표시 된 메서드는의 구현 합니다 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> 메서드를 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> 인터페이스 사용자 지정 배포 단계에서. 더 큰 예제의의 컨텍스트에서이 코드를 보려면 [연습: SharePoint 프로젝트용 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)합니다.

 에 대 한 호출에 대 한 다음 세부 정보를 확인 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> 메서드:

- 첫 번째 매개 변수를 호출 하려는 하는 명령을 식별 합니다. 이 문자열에 전달 하는 값과 일치 합니다 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> 명령 정의 합니다.

- 두 번째 매개 변수는 명령의 두 번째 사용자 지정 매개 변수를 전달 하려는 값입니다. 전체 경로 것이 경우에 *.wsp* SharePoint 사이트에 업그레이드 되는 파일입니다.

- 코드를 암시적 통과 하지 못한 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 매개 변수를 명령입니다. 이 매개 변수는 전달 된 명령에 자동으로 SharePoint 프로젝트 시스템의 확장 또는 확장에서 명령을 호출 하는 경우는 **SharePoint 연결** 노드에서 **서버 탐색기**. 솔루션을 구현 하는 프로젝트 템플릿 마법사와 같이 다른 유형의 합니다 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 인터페이스는이 매개 변수는 **null**합니다.

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에서는 Microsoft.VisualStudio.SharePoint 어셈블리에 대 한 필요합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [방법: SharePoint 명령 만들기](../sharepoint/how-to-create-a-sharepoint-command.md)
- [연습: 웹 파트를 표시 하려면 서버 탐색기 확장](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
