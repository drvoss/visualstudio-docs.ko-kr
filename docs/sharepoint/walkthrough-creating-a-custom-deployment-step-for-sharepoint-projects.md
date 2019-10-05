---
title: SharePoint 프로젝트용 사용자 지정 배포 단계 만들기
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4b209fad02cdcb3da230143a2c13ff4eaa648d76
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825629"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>연습: SharePoint 프로젝트용 사용자 지정 배포 단계 만들기
  SharePoint 프로젝트를 배포할 때 Visual Studio는 특정 순서로 일련의 배포 단계를 실행 합니다. Visual Studio는 많은 기본 제공 배포 단계를 포함 하지만 만들 수도 있습니다 고유한.

 이 연습에서는 SharePoint를 실행 하는 서버에서 솔루션을 업그레이드 하는 사용자 지정 배포 단계에 만들어집니다. Visual Studio는 다양 한 작업, 이러한 취소 또는 솔루션을 추가 하기 위한 기본 제공 배포 단계를 포함 하지만 솔루션 업그레이드에 대 한 배포 단계를 포함 하지 않습니다. 기본적으로 SharePoint 솔루션을 배포할 때 Visual Studio 먼저 취소 솔루션 (것을 이미 배포한 경우) 및 전체 솔루션 다시 배포 합니다. 기본 제공 배포 단계에 대 한 자세한 내용은 참조 하세요. [배포를 게시 하 고 SharePoint 솔루션 패키지를 업그레이드](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)합니다.

 이 연습에서는 다음 작업을 수행합니다.

- Visual Studio 확장을 만드는 두 가지 주요 작업을 수행 합니다.

  - SharePoint 솔루션을 업그레이드 하는 사용자 지정 배포 단계를 정의 하는 확장 합니다.

  - 확장 집합이 지정된 된 프로젝트에 대 한 실행 되는 배포 단계는 새 배포 구성에 정의 하는 프로젝트 확장을 만듭니다. 새 배포 구성에 사용자 지정 배포 단계 및 몇 가지 기본 제공 배포 단계가 포함 됩니다.

- 확장 프로그램 어셈블리를 호출 하는 두 개의 사용자 지정 SharePoint 명령을 만듭니다. SharePoint 명령은 Api를 사용 하는 서버 개체 모델에서 SharePoint 용 확장 프로그램 어셈블리에서 호출할 수 있는 메서드입니다. 자세한 내용은 [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)합니다.

- 두 어셈블리를 배포 하는 Visual Studio 확장 (VSIX) 패키지를 빌드합니다.

- 새 배포 단계를 테스트 합니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료 하려면 개발 컴퓨터의 다음 구성 요소가 필요 합니다.

- Windows, SharePoint 및 Visual Studio의 버전을 지원 합니다.

- Visual Studio SDK입니다. 이 연습에서는 합니다 **VSIX 프로젝트** sdk 확장을 배포 하려면 VSIX 패키지를 만드는 템플릿. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)합니다.

  다음 개념을 이해에 도움이 필요 하지는 않지만, 연습을 완료 하는:

- SharePoint에 대 한 서버 개체 모델을 사용합니다. 자세한 내용은 [SharePoint Foundation Server 쪽 개체 모델을 사용 하 여](http://go.microsoft.com/fwlink/?LinkId=177796)입니다.

- SharePoint 솔루션입니다. 자세한 내용은 [솔루션 개요](http://go.microsoft.com/fwlink/?LinkId=169422)합니다.

- SharePoint 솔루션을 업그레이드 합니다. 자세한 내용은 [솔루션을 업그레이드](http://go.microsoft.com/fwlink/?LinkId=177802)합니다.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 세 개의 프로젝트를 만들어야 합니다.

- 확장을 배포 하려면 VSIX 패키지를 만들려면 VSIX 프로젝트입니다.

- 확장을 구현 하는 클래스 라이브러리 프로젝트. 이 프로젝트는.NET Framework 4.5를 대상으로 해야 합니다.

- 사용자 지정 SharePoint 명령을 정의 하는 클래스 라이브러리 프로젝트. 이 프로젝트는.NET Framework 3.5를 대상으로 해야 합니다.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 노드를 선택한 후 합니다 **확장성** 노드.

    > [!NOTE]
    > 합니다 **확장성** 노드는 Visual Studio SDK를 설치 하는 경우에 사용할 수 있습니다. 자세한 내용은이 항목 앞부분의 전제 조건 섹션을 참조 하세요.

4. 선택 대화 상자 맨 **.NET Framework 4.5** 버전의.NET Framework의 목록에서입니다.

5. 선택 합니다 **VSIX 프로젝트** 서식 파일을 프로젝트의 이름 **UpgradeDeploymentStep**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **UpgradeDeploymentStep** 프로젝트가 **솔루션 탐색기**합니다.

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**UpgradeDeploymentStep 솔루션 노드의 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 프로젝트**합니다.

2. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 노드를 선택한 후 합니다 **Windows** 노드.

3. 선택 대화 상자 맨 **.NET Framework 4.5** 버전의.NET Framework의 목록에서입니다.

4. 선택 합니다 **클래스 라이브러리** 템플릿 프로젝트에서 프로젝트의 이름을 **DeploymentStepExtension**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **DeploymentStepExtension** 솔루션에 프로젝트를 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

#### <a name="to-create-the-sharepoint-command-project"></a>SharePoint 명령은 프로젝트를 만들려면

1. **솔루션 탐색기**UpgradeDeploymentStep 솔루션 노드의 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 프로젝트**합니다.

2. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic**를 선택한 후 합니다 **Windows** 노드.

3. 선택 대화 상자 맨 **.NET Framework 3.5** 버전의.NET Framework의 목록에서입니다.

4. 선택 합니다 **클래스 라이브러리** 템플릿 프로젝트에서 프로젝트의 이름을 **SharePointCommands**를 선택한 후는 **확인** 단추입니다.

     Visual Studio에 추가 합니다 **SharePointCommands** 솔루션에 프로젝트를 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-projects"></a>프로젝트 구성
 사용자 지정 배포 단계를 만드는 코드를 작성 하기 전에 코드 파일 및 어셈블리 참조를 추가 해야 하며 프로젝트를 구성 해야 합니다.

#### <a name="to-configure-the-deploymentstepextension-project"></a>DeploymentStepExtension 프로젝트를 구성 하려면

1. 에 **DeploymentStepExtension** 프로젝트에 다음 이름을 포함 하는 코드 파일을 두 개를 추가 합니다.

    - UpgradeStep

    - DeploymentConfigurationExtension

2. DeploymentStepExtension 프로젝트 바로 가기 메뉴를 열고 선택한 **참조 추가**합니다.

3. 에 **Framework** 탭에서 System.ComponentModel.Composition 어셈블리에 대 한 확인란을 선택 합니다.

4. 에 **확장** 탭 Microsoft.VisualStudio.SharePoint 어셈블리에 대 한 확인란을 선택 하 고 다음을 선택 합니다 **확인** 단추.

#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointCommands 프로젝트를 구성 하려면

1. 에 **SharePointCommands** 프로젝트, 명령 이라고 하는 코드 파일을 추가 합니다.

2. **솔루션 탐색기**에서 바로 가기 메뉴를 열고 합니다 **SharePointCommands** 프로젝트 노드를 선택한 후 **참조 추가**합니다.

3. 에 **확장** 탭에서 다음 어셈블리에 대 한 확인란을 선택 합니다. 선택한 후 클릭 합니다 **확인** 단추

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

## <a name="define-the-custom-deployment-step"></a>사용자 지정 배포 단계를 정의 합니다.
 업그레이드 배포 단계를 정의 하는 클래스를 만듭니다. 배포 단계를 구현 하는 클래스를 정의 하는 <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> 인터페이스입니다. 사용자 지정 배포 단계를 정의 하려고 할 때마다이 인터페이스를 구현 합니다.

#### <a name="to-define-the-custom-deployment-step"></a>사용자 지정 배포 단계를 정의 하려면

1. 에 **DeploymentStepExtension** 프로젝트 UpgradeStep 코드 파일을 열고 다음 다음 코드를 붙여 넣습니다.

    > [!NOTE]
    > 이 코드를 추가, 프로젝트를 컴파일 오류가 발생 해야 합니다. 해당 위치로 이동 후 추가 하면 코드 이후 단계에서.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>사용자 지정 배포 단계를 포함 하는 배포 구성 만들기
 여러 기본 제공 배포 단계 및 새 업그레이드 배포 단계를 포함 하는 새 배포 구성에 대 한 프로젝트 확장을 만듭니다. 이 확장을 만들어 SharePoint 프로젝트의 업그레이드 배포 단계를 사용 하 여 SharePoint 개발자를 수 있습니다.

 클래스를 구현 하는 배포 구성을 만들려면는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 인터페이스입니다. SharePoint 프로젝트 확장명 만들기를 원할 때마다이 인터페이스를 구현 합니다.

#### <a name="to-create-the-deployment-configuration"></a>배포 구성을 만들려면

1. 에 **DeploymentStepExtension** 프로젝트 DeploymentConfigurationExtension 코드 파일을 열고 다음 다음 코드를 붙여 넣습니다.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]

## <a name="create-the-custom-sharepoint-commands"></a>사용자 지정 SharePoint 명령 만들기
 SharePoint에 대 한 서버 개체 모델을 호출 하는 두 개의 사용자 지정 명령을 만듭니다. 하나의 명령 결정 하는 솔루션 배포 되는지 여부를 이미; 다른 명령에 솔루션을 업그레이드합니다.

#### <a name="to-define-the-sharepoint-commands"></a>SharePoint를 정의 하는 명령

1. 에 **SharePointCommands** 프로젝트 명령 코드 파일을 열고 다음 다음 코드를 붙여 넣습니다.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]

## <a name="checkpoint"></a>검사점
 이 연습에서는 사용자 지정 배포 단계 및 SharePoint 명령에 대 한 모든 코드 프로젝트에 포함 됩니다. 빌드 오류 없이 컴파일됩니다 있는지 확인 합니다.

#### <a name="to-build-the-projects"></a>프로젝트를 빌드하려면

1. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **DeploymentStepExtension** 프로젝트를 선택한 후 **빌드**합니다.

2. 바로 가기 메뉴를 열고 합니다 **SharePointCommands** 프로젝트를 선택한 후 **빌드**합니다.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>확장을 배포 하는 VSIX 패키지 만들기
 확장을 배포 하려면 솔루션에서 VSIX 프로젝트를 사용 하 여 VSIX 패키지를 만듭니다. VSIX 프로젝트에서 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 먼저 구성 합니다. 그런 다음 솔루션을 구축 하 여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX 패키지를 만들고 구성 하려면

1. **솔루션 탐색기**아래에서 **UpgradeDeploymentStep** 에 대 한 바로 가기 메뉴를 열고, 프로젝트를 **source.extension.vsixmanifest** 파일을 선택한 후  **열기**합니다.

     Visual Studio 매니페스트 편집기에서 파일을 엽니다. Source.extension.vsixmanifest 파일에는 모든 VSIX 패키지 해야 하는 extension.vsixmanifest 파일에 대 한 기반이 됩니다. 이 파일에 대 한 자세한 내용은 참조 하세요. [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)합니다.

2. 에 **Product Name** 상자에 입력 합니다 **SharePoint 프로젝트에 대 한 배포 단계 업그레이드**합니다.

3. 에 **작성자** 상자에 입력 합니다 **Contoso**합니다.

4. 에 **설명을** 상자에 입력 합니다 **SharePoint 프로젝트에서 사용할 수 있는 사용자 지정 업그레이드 배포 단계를 제공**합니다.

5. 에 **자산** 탭 편집기의 선택 된 **새로 만들기** 단추.

     합니다 **새 자산 추가** 대화 상자가 나타납니다.

6. 에 **형식** 목록에서 선택 **Microsoft.VisualStudio.MefComponent**합니다.

    > [!NOTE]
    > 이 값에 해당 하는 `MefComponent` extension.vsixmanifest 파일의 요소입니다. 이 요소는 VSIX 패키지 확장 어셈블리의 이름을 지정합니다. 자세한 내용은 [MEFComponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))합니다.

7. 에 **소스** 목록에서 선택 **현재 솔루션의 프로젝트**합니다.

8. 에 **프로젝트** 목록에서 선택 **DeploymentStepExtension**를 선택한 후는 **확인** 단추입니다.

9. 매니페스트 편집기에서 선택 합니다 **새로 만들기** 단추를 다시 합니다.

     합니다 **새 자산 추가** 대화 상자가 나타납니다.

10. 에 **형식** 목록에 입력 **SharePoint.Commands.v4**합니다.

    > [!NOTE]
    > 이 요소는 Visual Studio 확장에 포함 하려는 사용자 지정 확장을 지정 합니다. 자세한 내용은 [자산 요소 (VSX 스키마)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737)합니다.

11. 에 **소스** 목록에서 선택 **현재 솔루션의 프로젝트**합니다.

12. 에 **프로젝트** 목록에서 선택 **SharePointCommands**를 선택한 후는 **확인** 단추입니다.

13. 메뉴 모음에서 **빌드합니다** > **솔루션 빌드**, 솔루션이 오류 없이 컴파일되는지 확인 한 후 확인 합니다.

14. UpgradeDeploymentStep 프로젝트의 빌드 출력 폴더에 이제 UpgradeDeploymentStep.vsix 파일을 포함 해야 합니다.

     빌드 출력 폴더는 기본적으로... 프로젝트 파일이 포함 된 폴더 아래에 있는 \bin\Debug 폴더입니다.

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>업그레이드 배포 단계를 테스트할 준비
 업그레이드 배포 단계를 테스트 하려면 먼저 SharePoint 사이트에 샘플 솔루션을 배포 해야 합니다. Visual Studio의 실험적 인스턴스에서 확장을 디버그 하 여 시작 합니다. 목록 정 및 배포 단계를 테스트 하는 데 목록 인스턴스를 만들고 SharePoint 사이트에 배포 하 합니다. 다음으로 목록 정의와 목록 인스턴스를 수정 하 고 기본 배포 프로세스의 SharePoint 사이트에는 솔루션 덮어씁니다 하는 방법을 보여 줍니다. 다시 배포 합니다.

 이 연습의 뒷부분에서 목록 정의와 목록 인스턴스를 수정 하 고 SharePoint 사이트에 업그레이드 됩니다.

#### <a name="to-start-debugging-the-extension"></a>디버깅 확장을 시작 하려면

1. 관리자 자격 증명을 사용 하 여 Visual Studio를 다시 시작 하 고 UpgradeDeploymentStep 솔루션을 엽니다.

2. DeploymentStepExtension 프로젝트에서 UpgradeStep 코드 파일을 열고 다음 코드의 첫 번째 줄에 중단점을 추가 합니다 `CanExecute` 고 `Execute` 메서드.

3. 선택 하 여 디버깅을 시작 합니다 **F5** 키 또는 메뉴 모음에서 **디버그** > **디버깅 시작**합니다.

4. Visual Studio SharePoint Projects\1.0에 대 한 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade 배포 단계에 확장이 설치 되 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에서 업그레이드 배포 단계를 테스트할 합니다.

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>목록 정의와 목록 인스턴스를 사용 하 여 SharePoint 프로젝트를 만들려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **파일** > **새로 만들기** > **프로젝트**합니다.

2. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 노드 또는 **Visual Basic** 노드를 확장 합니다 **SharePoint** 노드를 선택한 후 합니다 **2010** 노드.

3. 대화 상자의 맨 위에 있는 했는지 **.NET Framework 3.5** 버전의.NET Framework의 목록에 나타납니다.

    프로젝트에 대 한 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 고 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 이 버전의.NET Framework가 필요 합니다.

4. 프로젝트 템플릿 목록에서 선택 **SharePoint 2010 프로젝트**, 프로젝트 이름을 **EmployeesListDefinition**를 선택한 후는 **확인** 단추입니다.

5. 에 **SharePoint 사용자 지정 마법사**, 디버깅을 위해 사용 하려는 사이트의 URL을 입력 합니다.

6. 아래 **이 SharePoint 솔루션의 신뢰 수준을**를 선택 합니다 **팜 솔루션으로 배포** 옵션 단추입니다.

   > [!NOTE]
   > 업그레이드 배포 단계는 샌드박스 솔루션을 지원 하지 않습니다.

7. 선택 된 **완료** 단추입니다.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] EmployeesListDefinition 프로젝트를 만듭니다.

8. EmployeesListDefinition 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 항목**합니다.

9. 에 **새 항목 추가-EmployeesListDefinition** 대화 상자에서 합니다 **SharePoint** 노드를 선택한 후는 **2010** 노드.

10. 선택 합니다 **목록** 항목 템플릿, 항목의 이름을 **직원 목록**를 선택한 후는 **추가** 단추입니다.

     SharePoint 사용자 지정 마법사가 나타나고

11. 에 **목록 설정 선택** 페이지에서 다음 설정을 확인 하 고 다음을 선택 합니다 **마침** 단추:

    1. **직원 목록** 에 표시 되는 **이름을 목록에 대해 표시 하 시겠습니까?** 상자입니다.

    2. 합니다 **에 따라 사용자 지정 가능한 목록을 만듭니다:** 옵션 단추를 선택 합니다.

    3. **기본 (비어 있음)** 에서 선택 하는 합니다 **기반으로 사용자 지정 가능한 목록을 만듭니다:** 목록입니다.

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 직책 열과 단일 빈 인스턴스를 사용 하 여 직원 목록 항목을 만들고 목록 디자이너를 엽니다.

12. 목록 디자이너에서에 **열** 탭을 선택 합니다 **기존 또는 새 열 이름을 입력** 행을 추가한 다음에 다음 열을 **열 표시 이름** 목록:

    1. First Name

    2. 회사

    3. 회사 전화

    4. 전자 메일

13. 모든 파일을 저장 하 고 목록 디자이너를 닫습니다.

14. **솔루션 탐색기**를 확장 합니다 **직원 목록** 노드를 펼친 다음를 **직원 목록 인스턴스** 자식 노드.

15. 에 *Elements.xml* 파일에서 다음 XML을 사용 하 여 기본 XML이이 파일을으로 바꿉니다. 이 XML 목록의 이름을 바꾸는 **직원** Jim 중 배 이름이 있는 직원에 대 한 정보를 추가 합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
        <Data>
          <Rows>
            <Row>
              <Field Name="Title">Hance</Field>
              <Field Name="FirstName">Jim</Field>
              <Field Name="Company">Contoso</Field>
              <Field Name="Business Phone">555-555-5555</Field>
              <Field Name="E-Mail">jim@contoso.com</Field>
            </Row>
          </Rows>
        </Data>
      </ListInstance>
    </Elements>
    ```

16. 저장 후 닫기 합니다 *Elements.xml* 파일입니다.

17. EmployeesListDefinition 프로젝트에 대 한 바로 가기 메뉴를 열고 선택한 **엽니다** 하거나 **속성**합니다.

     속성이 디자이너가 열립니다.

18. 에 **SharePoint** 탭을 선택 취소 합니다 **디버깅 후 자동 취소** 확인란을 선택한 다음 속성을 저장 합니다.

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>목록 정의와 목록 인스턴스를 배포 하려면

1. **솔루션 탐색기**를 선택 합니다 **EmployeesListDefinition** 프로젝트 노드.

2. 에 **속성** 창 있는지 확인 합니다 **활성 배포 구성** 속성이로 설정 되어 **기본**.

3. 선택 된 **F5** 키 또는 메뉴 모음에서 **디버그** > **디버깅 시작**합니다.

4. 프로젝트를 성공적으로 빌드되면 웹 브라우저가 열리고 SharePoint 사이트에 있는지 확인 하는 **나열** 새로운 빠른 실행 도구 모음에서 항목에 포함 되어 **직원** 목록에  **직원** 목록 Jim 중 배에 대 한 항목을 포함 합니다.

5. 웹 브라우저를 닫습니다.

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>목록 정의와 목록 인스턴스를 수정 하 고 다시 배포 하려면

1. EmployeesListDefinition 프로젝트에서 엽니다는 *Elements.xml* 의 자식 파일을 **직원 목록 인스턴스** 프로젝트 항목입니다.

2. 제거 된 `Data` 요소 및 해당 자식 중 배 Jim에 대 한 목록에서 항목을 제거 합니다.

     를 완료 하면 다음 XML 파일에 포함 해야 합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
      </ListInstance>
    </Elements>
    ```

3. 저장 후 닫기 합니다 *Elements.xml* 파일입니다.

4. 바로 가기 메뉴를 열고 합니다 **직원 목록** 프로젝트 항목을 선택한 후 **열려** 또는 **속성**합니다.

5. 목록 디자이너를 선택 합니다 **뷰** 탭 합니다.

6. 에 **선택한 열** 목록에서 선택 **첨부 파일**를 선택한 후는 < 키 열을 이동할를 **사용 가능한 열** 목록.

7. 이동 하려면 이전 단계를 반복 합니다 **회사 전화** 열에서는 **선택한 열** 목록를 **사용 가능한 열** 목록.

     이 작업의 기본 보기에서 이러한 필드를 제거 합니다 **직원** SharePoint 사이트의 목록입니다.

8. 선택 하 여 디버깅을 시작 합니다 **F5** 키 또는 메뉴 모음에서 **디버그** > **디버깅 시작**합니다.

9. 있는지 확인 합니다 **배포 충돌** 대화 상자가 나타납니다.

     이 대화 상자는 해당 솔루션에 이미 배포 된 SharePoint 사이트에 Visual Studio (목록 인스턴스) 솔루션을 배포 하려고 할 때 나타납니다. 이 연습에서 나중에 업그레이드 배포 단계를 실행 하면이 대화 상자 표시 되지 않습니다.

10. 에 **배포 충돌** 대화 상자를 선택 합니다 **자동으로 해결** 옵션 단추입니다.

     Visual Studio SharePoint 사이트에서 목록 인스턴스를 삭제 하 고, 프로젝트에서 목록 항목을 배포, 다음 SharePoint 사이트를 엽니다.

11. 에 **나열** 섹션 빠른 실행 도구 모음을 선택 합니다 **직원** 목록으로 이동한 후 다음 세부 정보를 확인:

    - 합니다 **첨부 파일** 하 고 **집 전화** 열 목록의이 보기에 나타나지 않습니다.

    - 목록이 비어 있습니다. 사용 하는 경우는 **기본** 솔루션을 다시 배포 하려면 배포 구성의 **직원** 목록 프로젝트에서 새로운 빈 목록으로 대체 되었습니다.

## <a name="test-the-deployment-step"></a>배포 단계를 테스트 합니다.
 이제 업그레이드 배포 단계를 테스트할 준비가 되었습니다. SharePoint에서 목록 인스턴스를 먼저 항목을 추가 합니다. 다음 목록 정의와 목록 인스턴스를 변경, SharePoint 사이트에서 업그레이드 하 고 업그레이드 배포 단계는 새 항목을 덮어쓰지는 확인 합니다.

#### <a name="to-manually-add-an-item-to-the-list"></a>목록에 항목을 수동으로 추가 하려면

1. SharePoint 사이트에서 리본 메뉴에서 아래 합니다 **목록 도구** 탭을 선택 합니다 **항목** 탭.

2. 에 **새로 만들기** 그룹에서 **새 항목**합니다.

     선택할 수 있습니다 합니다 **새 항목 추가** 자체 항목 목록에 링크 합니다.

3. 에 **직원-새 항목** 창에서를 **제목** 상자에 입력 합니다 **시설 Manager**합니다.

4. 에 **첫 번째 이름** 상자에 입력 합니다 **Andy**합니다.

5. 에 **회사** 상자에 입력 **Contoso**합니다.

6. 선택 된 **저장할** 단추, 목록에 새 항목이 표시 되는지 확인 하 고 웹 브라우저를 닫습니다.

     이 연습의 뒷부분에서 업그레이드 배포 단계는이 목록의 콘텐츠를 덮어쓰지 않습니다을 확인 하려면이 항목을 사용 합니다.

#### <a name="to-test-the-upgrade-deployment-step"></a>업그레이드 배포 단계를 테스트 하려면

1. Visual Studio의 실험적 인스턴스에서 **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **EmployeesListDefinition** 프로젝트 노드를 선택한 후 **속성**.

    속성 편집기/디자이너가 열립니다.

2. 에 **SharePoint** 탭, 설정 된 **활성 배포 구성** 속성을 **업그레이드**.

    이 사용자 지정 배포 구성은 새 업그레이드 배포 단계를 포함합니다.

3. 바로 가기 메뉴를 열고 합니다 **직원 목록** 프로젝트 항목을 선택한 후 **속성** 또는 **열기**합니다.

    속성 편집기/디자이너가 열립니다.

4. 에 **뷰** 탭을 선택는 **전자 메일** 열을 선택한 후는 **<** 에서 해당 열을 이동 하는 키를 **선택한 열**목록을 합니다 **사용 가능한 열** 목록입니다.

    이 작업의 기본 보기에서 이러한 필드를 제거 합니다 **직원** SharePoint 사이트의 목록입니다.

5. 선택 하 여 디버깅을 시작 합니다 **F5** 키 또는 메뉴 모음에서 **디버그** > **디버깅 시작**합니다.

6. Visual Studio의 다른 인스턴스에 코드에서 이전에 설정한 중단점에서 중지 확인을 `CanExecute` 메서드.

7. 선택 된 **F5** 다시 키 또는 메뉴 모음에서 **디버그** > **계속**합니다.

8. 코드에서 이전에 설정한 중단점에서 중지 확인을 `Execute` 메서드.

9. 선택 된 **F5** 키 또는 메뉴 모음에서 **디버그** > **계속** 를 마지막으로 합니다.

     웹 브라우저에 SharePoint 사이트가 열립니다.

10. 에 **나열** 섹션 빠른 실행 영역을 선택 합니다 **직원** 목록으로 이동한 후 다음 세부 정보를 확인:

    - 이전 (에 대 한 Andy 설비 관리자)에 수동으로 추가 하는 항목이 여전히 목록에에서 표시 됩니다.

    - 합니다 **회사 전화** 하 고 **전자 메일 주소** 열 목록의이 보기에 나타나지 않습니다.

      합니다 **업그레이드** 기존 배포 구성 수정 **직원** SharePoint 사이트에서 목록 인스턴스. 사용 하는 경우는 **기본** 대신 배포 구성의 **업그레이드** 구성 배포 충돌이 발생 합니다. Visual Studio는 대체 하 여 충돌을 해결 합니다 **직원** 목록과 Andy, 시설 manager에 대 한 항목 삭제 됩니다.

## <a name="clean-up-the-development-computer"></a>개발 컴퓨터 정리
 업그레이드 배포 단계를 테스트를 마친 후 SharePoint 사이트에서 목록 인스턴스와 목록 정의 제거 하 고 Visual Studio에서 배포 단계 확장을 제거 합니다.

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>SharePoint 사이트에서 목록 인스턴스를 제거 하려면

1. 엽니다는 **직원** 목록 열려 있지 않은 경우 SharePoint 사이트에서 목록입니다.

2. SharePoint 사이트에서 리본 메뉴에서 선택 합니다 **목록 도구** 탭을 선택한 다음는 **목록** 탭 합니다.

3. 에 **설정** 그룹에서 선택 합니다 **목록 설정** 항목.

4. 아래 **사용 권한 및 관리**를 선택 합니다 **이 목록을 삭제** 명령을 선택 합니다 **확인** 목록 휴지통을 보내고 웹 닫은 것을 확인 하려면 브라우저.

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>SharePoint 사이트에서 목록 정의 제거 하려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **빌드합니다** > **Retract**합니다.

     Visual Studio는 SharePoint 사이트에서 목록 정의 제거 합니다.

#### <a name="to-uninstall-the-extension"></a>확장을 제거하려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **도구가** > **확장 및 업데이트**합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장의 목록에서 선택 **SharePoint 프로젝트에 대 한 배포 단계 업그레이드**를 선택한 후 합니다 **제거** 명령입니다.

3. 나타나는 대화 상자에서 선택 **예** 확장을 제거한 다음 선택 하려는 것인지 **지금 다시 시작** 제거를 완료 합니다.

4. Visual Studio (실험적 인스턴스 및 UpgradeDeploymentStep 솔루션이 열려 있는 Visual Studio의 인스턴스)의 두 인스턴스를 닫습니다.

## <a name="see-also"></a>참고자료
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
