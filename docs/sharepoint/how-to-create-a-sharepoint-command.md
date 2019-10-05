---
title: '방법: SharePoint 명령 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d804acd19d585bf9517ce9b8d771290a1f1c214a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435462"
---
# <a name="how-to-create-a-sharepoint-command"></a>방법: SharePoint 명령 만들기
  사용자 지정 SharePoint 도구 확장에서 서버 개체 모델을 사용 하려는 경우 만들어야 *SharePoint 명령을* API를 호출 합니다. 서버 개체 모델을 직접 호출할 수 있는 어셈블리는 SharePoint 명령을 정의 합니다.

 SharePoint 명령의 목적에 대 한 자세한 내용은 참조 하세요. [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)합니다.

### <a name="to-create-a-sharepoint-command"></a>SharePoint 명령 만들기를

1. 다음 구성을 포함 하는 클래스 라이브러리 프로젝트를 만듭니다.

    - .NET Framework 3.5를 대상 으로합니다. 대상 프레임 워크를 선택 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: 한 버전의 .NET Framework를 대상으로 지정](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

    - AnyCPU 또는 x64를 대상으로 플랫폼입니다. 기본적으로 클래스 라이브러리 프로젝트의 대상 플랫폼은 AnyCPU입니다. 대상 플랫폼을 선택 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: 플랫폼을 대상으로 한 프로젝트 구성](../ide/how-to-configure-projects-to-target-platforms.md)을 참조하세요.

    > [!NOTE]
    > SharePoint 명령은.NET Framework 3.5 및 SharePoint 도구 확장 대상으로 대상이 되므로 SharePoint 도구 확장을 정의 하는 동일한 프로젝트에 SharePoint 명령을 구현할 수 없습니다는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]합니다. 별도 프로젝트에서 확장에 의해 사용 되는 모든 SharePoint 명령 정의 해야 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구의 확장을 배포할](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

2. 다음 어셈블리에 대한 참조를 추가합니다.

    - Microsoft.VisualStudio.SharePoint.Commands

    - Microsoft.SharePoint

3. 프로젝트의 클래스에서 SharePoint 명령을 정의 하는 메서드를 만듭니다. 메서드는 다음 지침을 따라야 합니다.

    - 이 하나 또는 두 개의 매개 변수를 가질 수 있습니다.

         첫째 매개 변수는 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 개체입니다. 이 개체는 Microsoft.SharePoint.SPSite 또는 명령이 실행 되는 Microsoft.SharePoint.SPWeb를 제공 합니다. 또한 제공을 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> 메시지를 쓰는 데 사용할 수 있는 개체를 **출력** 창 또는 **오류 목록** Visual Studio의 창.

         두 번째 매개 변수는 선택한 형식이 될 수 있지만이 매개 변수는 선택 사항입니다. 명령에 SharePoint 도구 확장 프로그램에서 데이터를 전달 하는 경우 사용자의 SharePoint 명령에이 매개 변수를 추가할 수 있습니다.

    - 반환 값을 가질 수 있습니다 하지만 선택 사항입니다.

    - 두 번째 매개 변수 및 반환 값에는 Windows Communication Foundation (WCF)으로 serialize 할 수 있는 형식 이어야 합니다. 자세한 내용은 [Types Supported by the Data Contract Serializer](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) 하 고 [XmlSerializer 클래스를 사용 하 여](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class)입니다.

    - 메서드는 모든 볼 수 있습니다 (**공개**를 **내부**, 또는 **개인**), 정적 또는 비정적 수 있습니다.

4. 적용 된 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> 방법입니다. 이 특성; 명령에 대 한 고유 식별자를 지정합니다. 이 식별자 메서드 이름과 일치 하지 않아도 됩니다.

     SharePoint 도구 확장에서 명령을 호출 하는 경우에 동일한 고유 식별자를 지정 해야 합니다. 자세한 내용은 [방법: SharePoint 명령 실행](../sharepoint/how-to-execute-a-sharepoint-command.md)합니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 식별자를 가진 SharePoint 명령을 `Contoso.Commands.UpgradeSolution`합니다. 이 명령은 서버 개체 모델에서 Api를 사용 하 여 배포 된 솔루션으로 업그레이드 합니다.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 암시적 첫 번째 외에도 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 매개 변수를이 명령 또한에 SharePoint 사이트에 업그레이드 되는.wsp 파일의 전체 경로 포함 하는 사용자 지정 문자열 매개 변수입니다. 더 큰 예제의의 컨텍스트에서이 코드를 보려면 [연습: SharePoint 프로젝트용 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)합니다.

## <a name="compiling-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요합니다.

- Microsoft.VisualStudio.SharePoint.Commands

- Microsoft.SharePoint

## <a name="deploying-the-command"></a>이 명령은 배포
 명령에 배포 하려면 동일한 명령을 어셈블리를 포함 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 확장명 (*vsix*) 명령을 사용 하는 확장 어셈블리를 사용 하 여 패키지 있습니다. 또한 extension.vsixmanifest 파일에서 명령 어셈블리에 대 한 항목을 추가 해야 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구의 확장을 배포할](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [방법: SharePoint 명령 실행](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [연습: 웹 파트를 표시 하려면 서버 탐색기 확장](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
