---
title: Visual Studio에서 SharePoint 도구의 확장을 배포 합니다. | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53e36d993e72da759c87e7d2d2f908818b3d9024
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62580646"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Visual Studio에서 SharePoint 도구에 대 한 확장 배포

SharePoint 도구 확장을 배포 하려면 만들기를 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 확장 프로그램 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 모든 파일을 포함 하는 확장 (VSIX) 패키지 있습니다. VSIX 패키지는 압축 된 다음에 파일을 OPC Open Packaging Conventions () 표준입니다. VSIX 패키지를 *.vsix* 확장 합니다.

VSIX 패키지를 만든 후 다른 사용자에 게 확장을 설치 하려면.vsix 파일을 실행할 수 있습니다. 파일의 모든 사용자에 확장을 설치 하면 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions 폴더에 설치 됩니다. 확장을 배포 하려면 VSIX 패키지를 업로드할 수 있습니다 합니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트 또는 있습니다 수 패키지 고객에 게 배포할 패키지를 네트워크 공유 또는 다른 일부 웹 호스팅 같은 다른 방법으로 사이트입니다.

VSIX 패키지 만들기 및 배포 하도록 하는 방법에 대 한 자세한 내용은 합니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)를 참조 하세요 [Visual Studio 확장 전달](../extensibility/shipping-visual-studio-extensions.md)합니다.

 사용 하 여 VSIX 패키지를 만들 수 있습니다 합니다 **VSIX 프로젝트** Visual Studio의 템플릿을 VSIX 패키지를 수동으로 만들 수 있습니다.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>VSIX 패키지를 만들려면 VSIX 프로젝트를 사용 합니다.

사용할 수는 **VSIX 프로젝트** SharePoint 도구 확장의 VSIX 패키지를 만들려면 Visual Studio SDK에서 제공 하는 템플릿. VSIX 프로젝트를 사용 하 여 VSIX 패키지를 수동으로 만드는 몇 가지 이점을 제공 합니다.

- Visual Studio 프로젝트를 빌드할 경우 VSIX 패키지를 자동으로 생성 합니다. 배포 파일 패키지에 추가 하 여 패키지에 대 한 [Content_Types].xml 파일을 만드는 등의 작업 수행 됩니다.

- VSIX 패키지에 확장 프로젝트 및 프로젝트 템플릿 및 항목 템플릿 등의 기타 파일의 빌드 출력을 포함 하도록 VSIX 프로젝트를 구성할 수 있습니다.

VSIX 프로젝트를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)합니다.

### <a name="organize-your-projects"></a>프로젝트 구성

기본적으로 VSIX 프로젝트는 VSIX 패키지에 어셈블리 없습니다만 생성합니다. 따라서 일반적으로 구현 하지 않는 SharePoint 도구 확장을 VSIX 프로젝트에서. 일반적으로 두 개 이상의 프로젝트를 사용 하 여 작동 합니다.

- VSIX 프로젝트입니다.

- 확장을 구현 하는 클래스 라이브러리 프로젝트.

작업할 수도 있습니다 추가 프로젝트를 사용 하 여 특정 형식의 확장:

- 확장에 의해 사용 되는 SharePoint 명령을 구현 하는 클래스 라이브러리 프로젝트. 이 시나리오를 보여 주는 연습을 참조 하세요. [연습: 웹 파트를 표시 하려면 서버 탐색기 확장](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)합니다.

- 확장 프로그램에 SharePoint 프로젝트 항목의 새 형식을 정의 하는 경우 항목 템플릿 또는 프로젝트 템플릿을 만드는 프로젝트 템플릿 또는 항목 템플릿을 프로젝트입니다. 이 시나리오를 보여 주는 연습을 참조 하세요. [연습: 항목 템플릿, 1 부를 사용 하 여 사용자 지정 작업 프로젝트 항목을 만들어](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)합니다.

- 확장 프로그램에 템플릿을 포함 하는 경우 항목 템플릿 또는 프로젝트 템플릿을 사용자 지정 마법사를 구현 하는 클래스 라이브러리 프로젝트. 이 시나리오를 보여 주는 연습을 참조 하세요. [연습: 항목 템플릿, 2 부를 사용 하 여 사용자 지정 작업 프로젝트 항목을 만들어](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)합니다.

동일한 Visual Studio 솔루션에서 모든 프로젝트를 포함 하는 경우에 클래스 라이브러리 프로젝트의 빌드 출력을 포함 하려면 VSIX 프로젝트에서 source.extension.vsixmanifest 파일을 수정할 수 있습니다.

### <a name="edit-the-vsix-manifest"></a>VSIX 매니페스트 편집

확장에 포함 하려는 모든 항목에 대 한 항목을 포함 하려면 VSIX 프로젝트에서 source.extension.vsixmanifest 파일을 편집 해야 합니다. 바로 가기 메뉴에서 source.extension.vsixmanifest 파일을 열면 파일을 파일에서 XML을 편집 하기 위한 UI를 제공 하는 디자이너에 표시 됩니다. 자세한 내용은 [VSIX 매니페스트 디자이너](../extensibility/vsix-manifest-designer.md)합니다.

Source.extension.vsixmanifest 파일에 다음 항목에 항목을 추가 해야 합니다.

- 확장 프로그램 어셈블리입니다.

- 확장에 의해 사용 되는 SharePoint 명령을 구현 하는 어셈블리입니다.

- 프로젝트 템플릿 또는 항목 템플릿 확장을 통해 연결 합니다.

- 확장을 통해 연결 된 템플릿에 대 한 사용자 지정 마법사.

다음 절차.vsixmanifest 파일에 이러한 각 항목에 대 한 항목을 추가 하는 방법에 설명 합니다.

#### <a name="to-include-the-extension-assembly"></a>확장 어셈블리를 포함 하려면

1. VSIX 프로젝트에서 source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 열고 선택한 후 **엽니다**합니다.

     파일은 디자이너에서 열립니다.

2. 에 **자산** 탭 편집기의 선택 된 **새로 만들기** 단추입니다.

     합니다 **새 자산 추가** 대화 상자가 열립니다.

3. 에 **형식** 목록에서 선택 **Microsoft.VisualStudio.MefComponent**합니다.

4. 에 **원본** 목록에서 다음 단계 중 하나를 수행 합니다.

    - 확장 어셈블리에서 VSIX 프로젝트와 동일한 솔루션에 있는 프로젝트를 빌드할 경우 선택할 **현재 솔루션의 프로젝트**합니다. 에 **프로젝트** 목록에서 프로젝트의 이름을 선택 합니다.

    - 확장 프로그램 어셈블리를 프로젝트에 파일로 포함 하는 경우 선택할 **파일 시스템의 파일**합니다. 에 **경로** 목록, 확장 프로그램 어셈블리 파일의 전체 경로 입력 하거나 사용 합니다 **찾아보기** 단추를 찾아 어셈블리 파일을 선택 합니다.

5. **확인** 단추를 선택합니다.

#### <a name="to-include-a-sharepoint-command-assembly"></a>SharePoint 명령 어셈블리를 포함 합니다.

1. VSIX 프로젝트에서 source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 열고 선택한 합니다 **엽니다** 단추입니다.

     파일이는 디자이너에서 열립니다.

2. 에 **자산** 섹션 편집기의 선택 된 **새로 만들기** 단추.

     합니다 **새 자산 추가** 대화 상자가 열립니다.

3. 에 **형식** 상자에 입력 합니다 **SharePoint.Commands.v4**합니다.

4. 에 **원본** 목록에서 다음 단계 중 하나를 수행 합니다.

    - 명령을 어셈블리에서 VSIX 프로젝트와 동일한 솔루션에 있는 프로젝트를 빌드할 경우 선택할 **현재 솔루션의 프로젝트**합니다. 에 **프로젝트** 목록에서 프로젝트의 이름을 선택 합니다.

    - 명령을 어셈블리를 프로젝트에 파일로 포함 하는 경우 선택할 **파일 시스템의 파일**합니다. 에 **경로** 목록, 확장 프로그램 어셈블리 파일의 전체 경로 입력 하거나 사용 합니다 **찾아보기** 단추를 찾아 어셈블리 파일을 선택 합니다.

5. **확인** 단추를 선택합니다.

#### <a name="to-include-a-template-that-you-create"></a>사용자가 만든 템플릿을 포함 합니다.

1. VSIX 프로젝트에서 source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 열고 선택한 합니다 **엽니다** 단추입니다.

     파일이는 디자이너에서 열립니다.

2. 에 **자산** 섹션 편집기의 선택 된 **새로 만들기** 단추.

     합니다 **새 자산 추가** 대화 상자가 열립니다.

3. 에 **형식** 목록에서 선택 **Microsoft.VisualStudio.ProjectTemplate** 하거나 **Microsoft.VisualStudio.ItemTemplate**합니다.

4. 에 **소스** 목록에서 선택 **현재 솔루션의 프로젝트**합니다.

5. 에 **프로젝트** 목록, 프로젝트의 이름을 선택 하 고 선택한 합니다 **확인** 단추입니다.

6. **솔루션 탐색기**, 프로젝트 템플릿 또는 항목 템플릿을 프로젝트에 대 한 바로 가기 메뉴를 열고 선택한 후 **프로젝트 언로드**합니다.

7. 프로젝트 노드에 대 한 바로 가기 메뉴를 다시 열고 선택한 **편집할**_YourTemplateProjectName_**.csproj** 하거나 **편집**  _YourTemplateProjectName_**.vbproj**합니다.

8. 다음 찾기 `VSTemplate` 프로젝트 파일의 요소입니다.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. 다음 XML을 사용 하 여이 요소를 대체 합니다.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` 요소 프로젝트를 빌드할 때 프로젝트 템플릿은 생성 되는 경로에 추가 폴더를 지정 합니다. 여기에 지정 된 폴더는 고객에 게 열면 항목 템플릿을 사용할 수 있게 합니다 **새 프로젝트 추가** 대화 상자에서 합니다 **SharePoint** 노드를 선택한 후는 **2010**  노드.

10. 파일을 저장한 후 닫습니다.

11. **솔루션 탐색기**, 프로젝트 템플릿 또는 항목 템플릿을 프로젝트에 대 한 바로 가기 메뉴를 열고 선택한 후 **프로젝트 다시 로드**합니다.

#### <a name="to-include-a-template-that-you-create-manually"></a>수동으로 만든 서식 파일을 포함 하려면

1. VSIX 프로젝트에서 템플릿에 포함할 프로젝트에 새 폴더를 추가 합니다.

2. 이 새 폴더 아래에 있는 다음 하위 폴더를 만들고 다음 템플릿 (.zip) 파일을 추가 합니다 *로캘 ID* 폴더입니다.

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *로캘 ID*

     *YourTemplateName*.zip

     예를 들어 영어 (미국) 로캘을 지 ContosoCustomAction.zip 라는 항목 템플릿을 경우 전체 경로일 수 있습니다 *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*합니다.

3. **솔루션 탐색기**를 템플릿 파일 선택 (*YourTemplateName*.zip).

4. 에 **속성** 창에서 설정 합니다 **빌드 작업** 속성을 **콘텐츠**합니다.

5. Source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 열고 선택한 **열려**합니다.

     파일이는 디자이너에서 열립니다.

6. 에 **자산** 섹션 편집기의 선택 된 **새로 만들기** 단추.

     합니다 **새 자산 추가** 대화 상자가 열립니다.

7. 에 **형식** 목록에서 선택 **Microsoft.VisualStudio.ItemTemplate** 하거나 **Microsoft.VisualStudio.ProjectTemplate**합니다.

8. 에 **소스** 목록에서 선택 **파일 시스템의 파일**합니다.

9. 에 **경로** 필드 어셈블리에 전체 경로 입력 합니다 (예를 들어 *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*를 사용할지를 **찾아보기**단추를 어셈블리를 찾아서 선택한 후는 **확인** 단추입니다.

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>프로젝트 템플릿 또는 항목 템플릿의 마법사를 포함 합니다.

1. VSIX 프로젝트에서 source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 열고 선택한 후 **엽니다**합니다.

     파일이는 디자이너에서 열립니다.

2. 에 **자산** 섹션 편집기의 선택 된 **새로 만들기** 단추.

     합니다 **새 자산 추가** 대화 상자가 열립니다.

3. 에 **형식** 목록에서 선택 **Microsoft.VisualStudio.Assembly**합니다.

4. 에 **원본** 목록에서 다음 단계 중 하나를 수행 합니다.

    - 마법사 어셈블리에서 VSIX 프로젝트와 동일한 솔루션에 있는 프로젝트를 빌드할 경우 선택할 **현재 솔루션의 프로젝트**합니다. 에 **프로젝트** 목록에서 프로젝트의 이름을 선택 합니다.

    - 마법사 어셈블리를 프로젝트에 파일로 포함 하는 경우 선택할 **파일 시스템의 파일**합니다. 에 **경로** 필드, 어셈블리 파일의 전체 경로 입력 하거나 사용 합니다 **찾아보기** 단추를 찾아 어셈블리를 선택 합니다.

5. **확인** 단추를 선택합니다.

### <a name="related-walkthroughs"></a>관련된 연습

다음 표에서 VSIX 프로젝트를 사용 하 여 다양 한 유형의 SharePoint 도구 확장을 배포 하는 방법을 보여주는 연습을 보여 줍니다.

|확장 형식|관련된 연습|
|--------------------|--------------------------|
|확장 프로그램 어셈블리에만 포함 하는 확장|[연습: SharePoint 프로젝트 항목 형식 확장](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [연습: SharePoint 프로젝트 확장명 만들기](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [연습: 서버 탐색기 확장의 SharePoint 클라이언트 개체 모델 호출](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|SharePoint 명령을 포함 하는 확장|[연습: SharePoint 프로젝트용 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [연습: 웹 파트를 표시 하려면 서버 탐색기 확장](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [연습: 2 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Visual Studio 템플릿을 포함 하는 확장|[연습: 항목 템플릿, 1 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [연습: 1 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|템플릿 마법사를 포함 하는 확장|[연습: 항목 템플릿, 2 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [연습: 2 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>VSIX 패키지를 수동으로 만들기

SharePoint 도구 확장 프로그램에 대해 VSIX 패키지를 수동으로 만들려면 하려는 경우 다음 단계를 수행 합니다.

1. 새 폴더에 extension.vsixmanifest 파일 및 [Content_Types].xml 파일을 만듭니다. 자세한 내용은 [VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)합니다.

2. Windows 탐색기에서 두 개의 XML 파일이 포함 된 폴더를 마우스 오른쪽 단추로 클릭, 보내기를 클릭 하 고 압축 (zip) 폴더를 클릭 합니다. 결과.zip 파일을 Filename.vsix, 여기서 Filename은 패키지를 설치 하는 재배포 가능 파일의 이름의을 바꿉니다.

3. VSIX 패키지에 확장 프로그램 어셈블리를 추가 합니다. 확장에서 SharePoint 명령에 포함 된 경우 VSIX 패키지에는 SharePoint 명령을 구현 하는 어셈블리를 추가할 수도 있습니다.

4. Extension.vsixmanifest 파일을 수정 합니다.

    - 추가 된 `Microsoft.VisualStudio.MefComponent` 요소 아래에 있는 `Assets` 요소 및 VSIX 패키지에서 확장을 구현 하는 어셈블리의 상대 경로를 새 요소의 값을 설정 합니다. 자세한 내용은 [MEFComponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))합니다.

    - 확장에서 SharePoint에 대 한 서버 개체 모델을 호출 하는 SharePoint 명령에 포함 된 경우 추가 된 `Microsoft.VisualStudio.Assembly` 요소 아래에 있는 `Assets` 요소. VSIX 패키지에는 SharePoint 명령을 구현 하는 어셈블리의 상대 경로를 새 요소의 값을 설정 합니다. 자세한 내용은 [자산 요소 (VSX 스키마)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737)합니다.

    - 확장 프로그램 프로젝트 템플릿 또는 항목 템플릿을 포함 하는 경우 추가 된 `ProjectTemplate` 또는 `ItemTemplate` 요소 아래에 있는 `Assets` 요소. VSIX 패키지에 대 한 템플릿이 포함 된 폴더의 상대 경로를 새 요소의 값을 설정 합니다. 자세한 내용은 [ProjectTemplate 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) 하 고 [ItemTemplate 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\))합니다.

    - 확장 프로그램 프로젝트 템플릿 또는 항목 템플릿 사용자 지정 마법사가 포함 된 경우 추가 `Assembly` 요소 아래에 있는 `Assets` 요소입니다. VSIX 패키지에 어셈블리의 상대 경로를 새 요소의 값을 설정 하 고 설정한는 `AssemblyName` 특성을 전체 어셈블리 이름 (버전, 문화권 및 공개 키 토큰 포함). 자세한 내용은 [Dependency 요소 (VSX 스키마)](https://msdn.microsoft.com/1f63f60a-98ad-48ec-8e44-4eba383d3e37)합니다.

### <a name="example"></a>예제

다음 예제에서는 SharePoint 도구 확장에 대 한 extension.vsixmanifest 파일의 내용을 보여 줍니다. 확장은 Contoso.ProjectExtension.dll 이라고 하는 어셈블리에서 구현 됩니다. 확장 Contoso.ExtensionCommands.dll 및 명명 된 폴더 아래에 있는 항목 템플릿을 이라고 하는 SharePoint 명령을 어셈블리가 포함 **Itemtemplate** VSIX 패키지에 있습니다. 이 예제에서는 동일한 VSIX 패키지에 extension.vsixmanifest 파일 폴더에 두 어셈블리가 모두 가정 합니다.

```xml
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />
    <DisplayName>CustomActionProjectItem</DisplayName>
    <Description>Empty VSIX Project.</Description>
  </Metadata>
  <Installation>
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>참고자료

- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
- [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Visual Studio에서 SharePoint 도구에 대 한 확장명 디버깅](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
