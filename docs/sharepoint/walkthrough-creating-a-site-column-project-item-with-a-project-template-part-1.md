---
title: 프로젝트 템플릿, 1 부를 사용 하 여 사이트 열 프로젝트 항목 만들기
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 60e4f4e035b381b8bfda8e14ee705471b0fad2b8
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177551"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>연습: 1 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기
  SharePoint 프로젝트는 하나 이상의 SharePoint 프로젝트 항목에 대 한 컨테이너입니다. SharePoint 프로젝트 항목 형식을 사용자를 만들고 프로젝트 템플릿을 사용 하 여 연결 하 여 Visual Studio에서 SharePoint 프로젝트 시스템을 확장할 수 있습니다. 이 연습에서는 사이트 열을 만들기 위한 프로젝트 항목 형식을 정의 하 고 사이트 열 프로젝트 항목을 포함 하는 새 프로젝트를 만드는 데 사용할 수 있는 프로젝트 템플릿을 만듭니다.

 이 연습에서는 다음 작업을 수행합니다.

- 사이트 열에 대 한 SharePoint 프로젝트 항목의 새 형식을 정의 하는 Visual Studio 확장을 만들 합니다. 프로젝트 항목 형식에 표시 되는 간단한 사용자 지정 속성을 포함 합니다 **속성** 창입니다.

- 만들기는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 프로젝트 항목에 대 한 프로젝트 템플릿.

- 빌드는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 확장 (VSIX) 패키지 프로젝트 템플릿 및 확장 프로그램 어셈블리를 배포 합니다.

- 디버깅 및 프로젝트 항목을 테스트 합니다.

  독립 실행형 연습입니다. 이 연습을 완료 한 후에 프로젝트 템플릿에 마법사를 추가 하 여 프로젝트 항목을 개선할 수 있습니다. 자세한 내용은 [연습: 2 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)합니다.

> [!NOTE]
> 샘플 워크플로의 계열에 대 한 참조 [SharePoint workflow 샘플](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples)합니다.

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료 하려면 개발 컴퓨터의 다음 구성 요소가 필요 합니다.

- 지원 되는 Microsoft Windows, SharePoint 버전 및 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] 이 연습에서는 합니다 **VSIX 프로젝트** 템플릿 프로젝트 항목을 배포 하려면 VSIX 패키지를 만들려면 sdk에서. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)합니다.

  다음 개념에 대 한 지식이 도움이 되지만 필수적이 지 않거나 연습을 완료 하는:

- SharePoint에서 사이트 열입니다. 자세한 내용은 [열](http://go.microsoft.com/fwlink/?LinkId=183547)합니다.

- Visual Studio에서 프로젝트 템플릿입니다. 자세한 내용은 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)를 참조하세요.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 세 개의 프로젝트를 만들려면:

- VSIX 프로젝트입니다. 이 프로젝트에는 사이트 열 프로젝트 항목 및 프로젝트 템플릿을 배포 하려면 VSIX 패키지를 만듭니다.

- 프로젝트 템플릿 프로젝트입니다. 이 프로젝트에는 사이트 열 프로젝트 항목을 포함 하는 새 SharePoint 프로젝트를 만드는 데 사용할 수 있는 프로젝트 템플릿을 만듭니다.

- 클래스 라이브러리 프로젝트입니다. 사이트 열 프로젝트 항목의 동작을 정의 하는 Visual Studio 확장을 구현 하는이 프로젝트입니다.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. 맨 위에 있는 **새 프로젝트** 대화 상자에서 확인 **.NET Framework 4.5** 버전의.NET Framework의 목록에서 선택 됩니다.

4. 확장 된 **Visual Basic** 또는 **Visual C#** 노드를 선택한 후는 **확장성** 노드.

    > [!NOTE]
    > 합니다 **확장성** 노드는 Visual Studio SDK를 설치 하는 경우에 사용할 수 있습니다. 자세한 내용은이 항목 앞부분의 전제 조건 섹션을 참조 하세요.

5. 프로젝트 템플릿 목록에서 선택 **VSIX 프로젝트**합니다.

6. 에 **이름** 상자에 입력 합니다 **SiteColumnProjectItem**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **SiteColumnProjectItem** 프로젝트가 **솔루션 탐색기**합니다.

#### <a name="to-create-the-project-template-project"></a>프로젝트 템플릿 프로젝트를 만들려면

1. **솔루션 탐색기**솔루션 노드의 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 프로젝트**합니다.

2. 맨 위에 있는 **새 프로젝트** 대화 상자에서 확인 **.NET Framework 4.5** 버전의.NET Framework의 목록에서 선택 됩니다.

3. 확장 된 **Visual C#** 또는 **Visual Basic** 노드를 선택한 후는 **확장성** 노드.

4. 프로젝트 템플릿 목록에서 선택 합니다 **C# 프로젝트 템플릿에** 또는 **Visual Basic 프로젝트 템플릿을** 템플릿.

5. 에 **이름** 상자에 입력 합니다 **SiteColumnProjectTemplate**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **SiteColumnProjectTemplate** 프로젝트를 솔루션입니다.

6. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

7. Visual Basic 프로젝트를 만든 경우 프로젝트에서 다음 파일 삭제:

    - *MyApplication.Designer.vb*

    - MyApplication.myapp

    - *Resources.Designer.vb*

    - *Resources.resx*

    - *Settings.Designer.vb*

    - Settings.settings

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**솔루션 노드의 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 프로젝트**합니다.

2. 맨 위에 있는 **새 프로젝트** 대화 상자에서 확인 **.NET Framework 4.5** 버전의.NET Framework의 목록에서 선택 됩니다.

3. 확장을 **Visual C#** 또는 **Visual Basic** 노드를 선택 합니다 **Windows** 노드를 선택한 후는 **클래스 라이브러리** 템플릿.

4. 에 **이름** 상자에 입력 합니다 **ProjectItemTypeDefinition** 를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **ProjectItemTypeDefinition** 솔루션에 프로젝트를 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-extension-project"></a>확장 프로젝트를 구성 합니다.
 코드 파일 및 확장 프로젝트 구성에 대 한 어셈블리 참조를 추가 합니다.

#### <a name="to-configure-the-project"></a>프로젝트를 구성 하려면

1. ProjectItemTypeDefinition 프로젝트에서 명명 된 코드 파일을 추가 **SiteColumnProjectItemTypeProvider**합니다.

2. 메뉴 모음에서 **프로젝트** > **참조 추가**를 선택합니다.

3. 에 **참조 관리자-ProjectItemTypeDefinition** 대화 상자에서 **어셈블리** 노드를 선택 합니다 **프레임 워크** 노드를 선택한 후는 System.ComponentModel.Composition 확인란입니다.

4. 선택 합니다 **확장** 노드를 Microsoft.VisualStudio.SharePoint 어셈블리 옆의 확인란을 선택 하 고 선택한 합니다 **확인** 단추입니다.

## <a name="define-the-new-sharepoint-project-item-type"></a>새 SharePoint 프로젝트 항목 형식 정의
 구현 하는 클래스를 만들기는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 새 프로젝트 항목 형식의 동작을 정의 하는 인터페이스입니다. 새 프로젝트 항목 형식의 정의 하려는 경우이 인터페이스를 구현 합니다.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>새 SharePoint 프로젝트 항목 형식 정의

1. 에 **SiteColumnProjectItemTypeProvider** 코드 파일 기본 코드를 다음 코드로 바꾸고 파일을 저장 합니다.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]

## <a name="create-a-visual-studio-project-template"></a>Visual Studio 프로젝트 템플릿 만들기
 프로젝트 템플릿 만들기, 다른 개발자 사이트 열 프로젝트 항목을 포함 하는 SharePoint 프로젝트를 만들 수 있습니다. 와 같은 Visual Studio에서 모든 프로젝트에 필요한 파일을 포함 하는 SharePoint 프로젝트 템플릿으로 *.csproj* 또는 *.vbproj* 하 고 *.vstemplate* 파일 및 파일을 SharePoint 프로젝트에 적용 됩니다. 자세한 내용은 [항목 템플릿 및 SharePoint 프로젝트 항목에 대 한 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)합니다.

 이 절차에서는 SharePoint 프로젝트에 관련 된 파일을 생성 하려면 빈 SharePoint 프로젝트를 만들 수 있습니다. 그런 다음 추가한 이러한 파일 SiteColumnProjectTemplate 프로젝트에이 프로젝트에서 생성 되는 서식 파일에 포함 되도록 합니다. SiteColumnProjectTemplate 프로젝트 파일에서 프로젝트 템플릿 위치 지정을 구성할 수도 합니다 **새 프로젝트** 대화 상자.

#### <a name="to-create-the-files-for-the-project-template"></a>프로젝트 템플릿에 대 한 파일을 만들려면

1. 두 번째 인스턴스를 시작 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 관리 자격 증명을 사용 합니다.

2. 이라고 하는 SharePoint 2010 프로젝트를 만듭니다 **BaseSharePointProject**합니다.

   > [!IMPORTANT]
   > 에 **SharePoint 사용자 지정 마법사**를 선택 하지는 **팜 솔루션으로 배포** 옵션 단추입니다.

3. 프로젝트에 빈 요소 항목을 추가 하 고 다음 항목의 이름을 **Field1**합니다.

4. 프로젝트를 저장 하 고 다음의 두 번째 인스턴스를 닫습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

5. 인스턴스의 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SiteColumnProjectItem 솔루션 열기를에 있는 **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SiteColumnProjectTemplate** 프로젝트 노드를 선택할  **추가**를 선택한 후 **기존 항목**합니다.

6. 에 **기존 항목 추가** 대화 상자에서 파일 확장명의 목록 상자를 열고 선택한 **모든 파일 (\*.\*)** .

7. BaseSharePointProject 프로젝트가 포함 된 디렉터리에서 key.snk 파일을 선택한 다음를 선택 합니다 **추가** 단추입니다.

   > [!NOTE]
   > 이 연습에서는 프로젝트 템플릿을 만든 템플릿을 사용 하 여 만든 각 프로젝트에 서명 하는 동일한 key.snk 파일을 사용 합니다. 각 프로젝트 인스턴스에 대 한 다른 key.snk 파일을 만들려면이 샘플을 확장 하는 방법에 알아보려면 참조 [연습: 2 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)합니다.

8. BaseSharePointProject 디렉터리에서 지정 된 하위 폴더에서 다음 파일을 추가 하려면 5-8 단계를 반복 합니다.

   - *\Field1\Elements.xml*

   - *\Field1\SharePointProjectItem.spdata*

   - *\Features\Feature1\Feature1.feature*

   - *\Features\Feature1\Feature1.Template.xml*

   - *\Package\Package.package*

   - *\Package\Package.Template.xml*

     이러한 파일을 직접 SiteColumnProjectTemplate 프로젝트 추가 Field1, 기능 또는 패키지 하위 폴더에에서 있는 프로젝트를 다시 없는 합니다. 이러한 파일에 대 한 자세한 내용은 참조 하세요. [항목 템플릿 및 SharePoint 프로젝트 항목에 대 한 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)합니다.

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>개발자가 새 프로젝트 대화 상자에서 프로젝트 템플릿을 검색 하는 방법을 구성 하려면

1. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SiteColumnProjectTemplate** 프로젝트 노드를 선택한 후 **프로젝트 언로드**합니다. 모든 파일 변경 내용을 저장 하 라는 메시지가 나타나면 선택 합니다 **예** 단추입니다.

2. 바로 가기 메뉴를 열고 합니다 **SiteColumnProjectTemplate** 노드를 다시 선택한 후 **편집 SiteColumnProjectTemplate.csproj** 또는 **편집 SiteColumnProjectTemplate.vbproj**.

3. 프로젝트 파일에서 다음을 찾습니다 `VSTemplate` 요소입니다.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4. 다음 XML을 사용 하 여이 요소를 대체 합니다.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` 요소 프로젝트를 빌드할 때 프로젝트 템플릿은 생성 되는 경로에 추가 폴더를 지정 합니다. 여기에 지정 된 폴더는 고객에 게 열면 프로젝트 템플릿을 사용할 수 있게 합니다 **새 프로젝트** 대화 상자에서 합니다 **SharePoint** 노드를 선택한 후는 **2010**  노드.

5. 파일을 저장한 후 닫습니다.

6. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SiteColumnProjectTemplate** 프로젝트를 선택한 후 **프로젝트 다시 로드**합니다.

## <a name="edit-the-project-template-files"></a>프로젝트 템플릿 파일을 편집 합니다.
 SiteColumnProjectTemplate 프로젝트에 프로젝트 템플릿의 동작을 정의 하는 다음 파일을 편집 합니다.

- *AssemblyInfo.cs* 또는 *AssemblyInfo.vb*

- *Elements.xml*

- *SharePointProjectItem.spdata*

- *Feature1.feature*

- *Package.package*

- *SiteColumnProjectTemplate.vstemplate*

- *ProjectTemplate.csproj* 또는 *ProjectTemplate.vbproj*

  다음 절차에서는 이러한 파일 중 일부에 대 한 대체 가능 매개 변수를 추가 합니다. 대체 가능 매개 변수는 시작 하는 달러 기호 ($) 문자로 끝나는 토큰입니다. 사용자에서는이 프로젝트 템플릿은 프로젝트를 만들 때 Visual Studio는 자동으로 새 프로젝트에서 이러한 매개 변수에 특정 값으로 바꿉니다. 자세한 내용은 [대체 가능 매개 변수](../sharepoint/replaceable-parameters.md)합니다.

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>AssemblyInfo.cs 또는 AssemblyInfo.vb 파일을 편집 하려면

1. SiteColumnProjectTemplate 프로젝트에서 엽니다는 *AssemblyInfo.cs* 또는 *AssemblyInfo.vb* 파일을 선택한 다음의 맨 위에 다음 문을 추가 합니다.

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     경우는 **샌드박스 솔루션** SharePoint 프로젝트의 속성이로 설정 되어 **True**, Visual Studio 추가 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> AssemblyInfo 코드 파일. 그러나 프로젝트 템플릿에서 AssemblyInfo 코드 파일을 가져오지 않는 <xref:System.Security> 기본적으로 네임 스페이스입니다. 이 추가 해야 합니다 **를 사용 하 여** 또는 **Imports** 문을 방지 하기 위해 컴파일 오류가 발생 합니다.

2. 파일을 저장한 후 닫습니다.

#### <a name="to-edit-the-elementsxml-file"></a>Elements.xml 파일을 편집 하려면

1. SiteColumnProjectTemplate 프로젝트에서의 내용을 대체 합니다 *Elements.xml* 다음 XML 사용 하 여 파일입니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
          Name="$safeprojectname$"
          DisplayName="$projectname$"
          Type="Text"
          Group="Custom Columns">
      </Field>
    </Elements>
    ```

     새 XML 추가 `Field` 사이트 열, 해당 기본 형식 및 갤러리에서 사이트 열을 나열 하는 그룹의 이름을 정의 하는 요소입니다. 이 파일의 콘텐츠에 대 한 자세한 내용은 참조 [필드 정의 스키마](http://go.microsoft.com/fwlink/?LinkId=184290)합니다.

2. 파일을 저장한 후 닫습니다.

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>SharePointProjectItem.spdata 파일을 편집 하려면

1. SiteColumnProjectTemplate 프로젝트에서의 내용을 대체 합니다 *SharePointProjectItem.spdata* 다음 XML 사용 하 여 파일입니다.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
     <Files>
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />
     </Files>
   </ProjectItem>
   ```

    새 XML 파일에 다음 내용을 변경 합니다.

   - 변경 내용을 `Type` 특성을 `ProjectItem` 요소에 전달 되는 동일한 문자열에는 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 프로젝트 항목 정의 대 (를 `SiteColumnProjectItemTypeProvider` 이 연습의 앞부분에서 만든 클래스).

   - 제거는 `SupportedTrustLevels` 하 고 `SupportedDeploymentScopes` 에서 특성을 `ProjectItem` 요소. 신뢰 수준 및 배포 범위에 지정 된 특성 값이 필요 하지 않습니다는 `SiteColumnProjectItemTypeProvider` ProjectItemTypeDefinition 프로젝트의 클래스입니다.

     내용에 대 한 자세한 내용은 *.spdata* 파일을 참조 하십시오 [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)합니다.

2. 파일을 저장한 후 닫습니다.

#### <a name="to-edit-the-feature1feature-file"></a>Feature1.feature 파일을 편집 하려면

1. SiteColumnProjectTemplate 프로젝트에서의 내용을 대체 합니다 *Feature1.feature* 다음 XML 사용 하 여 파일입니다.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"
            imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""
            deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">
     <projectItems>
       <projectItemReference itemId="$guid2$" />
     </projectItems>
   </feature>
   ```

    새 XML 파일에 다음 내용을 변경 합니다.

   - 값을 변경 합니다 `Id` 및 `featureId` 의 특성을 `feature` 요소를 `$guid4$`입니다.

   - 값을 변경 합니다 `itemId` 특성을 `projectItemReference` 요소를 `$guid2$`입니다.

     에 대 한 자세한 내용은 *.feature* 파일을 참조 하십시오 [항목 템플릿 및 SharePoint 프로젝트 항목에 대 한 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)합니다.

2. 파일을 저장한 후 닫습니다.

#### <a name="to-edit-the-packagepackage-file"></a>패키지 파일을 편집 하려면

1. SiteColumnProjectTemplate 프로젝트에서의 내용을 대체 합니다 *Package.package* 다음 XML 사용 하 여 파일.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"
            Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">
     <features>
       <featureReference itemId="$guid4$" />
     </features>
   </package>
   ```

    새 XML 파일에 다음 내용을 변경 합니다.

   - 값을 변경 합니다 `Id` 및 `solutionId` 의 특성을 `package` 요소를 `$guid3$`입니다.

   - 값을 변경 합니다 `itemId` 특성을 `featureReference` 요소를 `$guid4$`입니다.

     에 대 한 자세한 내용은 *.package* 파일을 참조 하십시오 [항목 템플릿 및 SharePoint 프로젝트 항목에 대 한 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)합니다.

2. 파일을 저장한 후 닫습니다.

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Sitecolumnprojecttemplate.vstemplate 파일을 편집 하려면

1. SiteColumnProjectTemplate 프로젝트에서 XML의 다음 섹션 중 하나를 사용 하 여 SiteColumnProjectTemplate.vstemplate 파일의 내용을 대체 합니다.

   - Visual C# 프로젝트 서식 파일을 만들 경우 다음 XML을 사용 합니다.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">
     <TemplateData>
       <Name>Site Column</Name>
       <Description>Creates a new site column in SharePoint</Description>
       <FrameworkVersion>3.5</FrameworkVersion>
       <ProjectType>CSharp</ProjectType>
       <CreateNewFolder>true</CreateNewFolder>
       <CreateInPlace>true</CreateInPlace>
       <ProvideDefaultName>true</ProvideDefaultName>
       <DefaultName>SiteColumn</DefaultName>
       <LocationField>Enabled</LocationField>
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
       <Icon>SiteColumnProjectTemplate.ico</Icon>
       <SortOrder>1000</SortOrder>
     </TemplateData>
     <TemplateContent>
       <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">
         <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
       </Project>
     </TemplateContent>
   </VSTemplate>
   ```

   - Visual Basic 프로젝트 템플릿을 만들 때, 다음 XML을 사용 합니다.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">
     <TemplateData>
       <Name>Site Column</Name>
       <Description>Creates a new site column in SharePoint</Description>
       <FrameworkVersion>3.5</FrameworkVersion>
       <ProjectType>VisualBasic</ProjectType>
       <CreateNewFolder>true</CreateNewFolder>
       <CreateInPlace>true</CreateInPlace>
       <ProvideDefaultName>true</ProvideDefaultName>
       <DefaultName>SiteColumn</DefaultName>
       <LocationField>Enabled</LocationField>
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
       <Icon>SiteColumnProjectTemplate.ico</Icon>
       <SortOrder>1000</SortOrder>
     </TemplateData>
     <TemplateContent>
       <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">
         <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
       </Project>
     </TemplateContent>
   </VSTemplate>
   ```

    새 XML 파일에 다음 내용을 변경 합니다.

   - 집합의 `Name` 요소 값으로 **사이트 열**합니다. (이 이름이 나타나는 합니다 **새 프로젝트** 대화 상자).

   - 추가 `ProjectItem` 채우려는 각 요소의 인스턴스마다 프로젝트에에서 포함 합니다.

   - 네임 스페이스를 사용 하 여 "<http://schemas.microsoft.com/developer/vstemplate/2005>"입니다. 이 솔루션 사용의 다른 프로젝트 파일을 "<http://schemas.microsoft.com/developer/msbuild/2003>" 네임 스페이스입니다. 따라서 XML 스키마 경고 메시지가 생성 됩니다 있지만이 연습에서 무시할 수 있습니다.

     내용에 대 한 자세한 내용은 *.vstemplate* 파일을 참조 하십시오 [Visual Studio 템플릿 스키마 참조](/visualstudio/extensibility/visual-studio-template-schema-reference)합니다.

2. 파일을 저장한 후 닫습니다.

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Projecttemplate.csproj 또는 projecttemplate.vbproj 파일을 편집 하려면

1. SiteColumnProjectTemplate 프로젝트에서의 내용을 대체 합니다 *ProjectTemplate.csproj* 파일 또는 *ProjectTemplate.vbproj* XML의 다음 섹션 중 하나를 사용 하 여 파일입니다.

    - Visual C# 프로젝트 서식 파일을 만들 경우 다음 XML을 사용 합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid>{$guid1$}</ProjectGuid>
        <OutputType>Library</OutputType>
        <AppDesignerFolder>Properties</AppDesignerFolder>
        <RootNamespace>$safeprojectname$</RootNamespace>
        <AssemblyName>$safeprojectname$</AssemblyName>
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
        <FileAlignment>512</FileAlignment>
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineConstants>DEBUG;TRACE</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <DebugType>pdbonly</DebugType>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <DefineConstants>TRACE</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
      <PropertyGroup>
        <SignAssembly>true</SignAssembly>
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="System" />
        <Reference Include="System.Core" />
        <Reference Include="System.Data" />
        <Reference Include="System.Data.DataSetExtensions" />
        <Reference Include="System.Web" />
        <Reference Include="System.Xml" />
        <Reference Include="System.Xml.Linq" />
        <Reference Include="Microsoft.SharePoint" />
        <Reference Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="Properties\AssemblyInfo.cs" />
      </ItemGroup>
      <ItemGroup>
        <None Include="Field1\SharePointProjectItem.spdata">
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>
        </None>
        <None Include="Field1\Elements.xml" />
      </ItemGroup>
      <ItemGroup>
        <None Include="key.snk" />
        <None Include="Package\Package.package">
          <PackageId>{$guid3$}</PackageId>
        </None>
        <None Include="Package\Package.Template.xml">
          <DependentUpon>Package.package</DependentUpon>
        </None>
        <None Include="Features\Feature1\Feature1.feature">
          <FeatureId>{$guid4$}</FeatureId>
        </None>
        <None Include="Features\Feature1\Feature1.Template.xml">
          <DependentUpon>Feature1.feature</DependentUpon>
        </None>
      </ItemGroup>
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />
    </Project>
    ```

    1. Visual Basic 프로젝트 템플릿을 만들 때, 다음 XML을 사용 합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
        <ProductVersion>
        </ProductVersion>
        <SchemaVersion>
        </SchemaVersion>
        <ProjectGuid>{$guid1$}</ProjectGuid>
        <OutputType>Library</OutputType>
        <RootNamespace>$safeprojectname$</RootNamespace>
        <AssemblyName>$safeprojectname$</AssemblyName>
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
        <FileAlignment>512</FileAlignment>
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        <OptionExplicit>On</OptionExplicit>
        <OptionCompare>Binary</OptionCompare>
        <OptionStrict>Off</OptionStrict>
        <OptionInfer>On</OptionInfer>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <OutputPath>bin\Debug\</OutputPath>
        <WarningLevel>4</WarningLevel>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <DebugType>pdbonly</DebugType>
        <DefineDebug>false</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup>
        <SignAssembly>true</SignAssembly>
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="System" />
        <Reference Include="System.Core" />
        <Reference Include="System.Data" />
        <Reference Include="System.Data.DataSetExtensions" />
        <Reference Include="System.Xml" />
        <Reference Include="System.Xml.Linq" />
        <Reference Include="Microsoft.SharePoint" />
        <Reference Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Import Include="Microsoft.VisualBasic" />
        <Import Include="System" />
        <Import Include="System.Collections" />
        <Import Include="System.Collections.Generic" />
        <Import Include="System.Data" />
        <Import Include="System.Diagnostics" />
        <Import Include="System.Linq" />
        <Import Include="System.Xml.Linq" />
        <Import Include="Microsoft.SharePoint" />
        <Import Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="My Project\AssemblyInfo.vb" />
      </ItemGroup>
      <ItemGroup>
        <AppDesigner Include="My Project\" />
      </ItemGroup>
      <ItemGroup>
        <None Include="Features\Feature1\Feature1.feature">
          <FeatureId>{$guid4$}</FeatureId>
        </None>
        <None Include="Field1\SharePointProjectItem.spdata">
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>
        </None>
        <None Include="key.snk" />
        <None Include="Package\Package.package">
          <PackageId>{$guid3$}</PackageId>
        </None>
        <None Include="Package\Package.Template.xml">
          <DependentUpon>Package.package</DependentUpon>
        </None>
      </ItemGroup>
      <ItemGroup>
        <None Include="Features\Feature1\Feature1.Template.xml">
          <DependentUpon>Feature1.feature</DependentUpon>
        </None>
        <None Include="Field1\Elements.xml" />
      </ItemGroup>
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />
    </Project>
    ```

     새 XML 파일에 다음 내용을 변경 합니다.

    - 사용 하 여 `TargetFrameworkVersion` 4.5가 아니라.NET Framework 3.5를 지정 하는 요소입니다.

    - 추가 `SignAssembly` 고 `AssemblyOriginatorKeyFile` 요소를 프로젝트 출력을 서명 합니다.

    - 추가 `Reference` 어셈블리에 대 한 요소를 사용 하는 SharePoint 프로젝트 참조 합니다.

    - 와 같은 프로젝트에서 각 기본 파일에 대 한 요소를 추가 *Elements.xml* 하 고 *SharePointProjectItem.spdata*합니다.

2. 파일을 저장한 후 닫습니다.

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>프로젝트 템플릿을 배포 하려면 VSIX 패키지 만들기
 확장을 배포 하려면의 VSIX 프로젝트를 사용 합니다 **SiteColumnProjectItem** VSIX 패키지를 만드는 방법. VSIX 프로젝트에 포함 된 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 먼저 구성 합니다. 그런 다음 솔루션을 구축 하 여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX 패키지를 만들고 구성 하려면

1. **솔루션 탐색기**를 **SiteColumnProjectItem** 프로젝트에서 매니페스트 편집기에서 source.extension.vsixmanifest 파일을 엽니다.

     Source.extension.vsixmanifest 파일에는 모든 VSIX 패키지 해야 하는 extension.vsixmanifest 파일에 대 한 기반이 됩니다. 이 파일에 대 한 자세한 내용은 참조 하세요. [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)합니다.

2. 에 **Product Name** 상자에 입력 합니다 **사이트 열**합니다.

3. 에 **작성자** 상자에 입력 합니다 **Contoso**합니다.

4. 에 **설명을** 상자에 입력 합니다 **사이트 열을 만들기 위한 SharePoint 프로젝트**합니다.

5. 선택 된 **자산** 탭을 선택한 다음는 **새로 만들기** 단추입니다.

     합니다 **새 자산 추가** 대화 상자가 열립니다.

6. 에 **형식** 목록에서 선택 **Microsoft.VisualStudio.ProjectTemplate**합니다.

    > [!NOTE]
    > 이 값에 해당 하는 `ProjectTemplate` extension.vsixmanifest 파일의 요소입니다. 이 요소는 프로젝트 템플릿이 포함 된 VSIX 패키지의 하위 폴더를 식별 합니다. 자세한 내용은 [ProjectTemplate 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\))합니다.

7. 에 **소스** 목록에서 선택 **현재 솔루션의 프로젝트**합니다.

8. 에 **프로젝트** 목록에서 선택한 **SiteColumnProjectTemplate**를 선택한 후는 **확인** 단추.

9. 선택 된 **새로 만들기** 단추를 다시 합니다.

     합니다 **새 자산 추가** 대화 상자가 열립니다.

10. 에 **형식** 목록에서 선택 **Microsoft.VisualStudio.MefComponent**합니다.

    > [!NOTE]
    > 이 값에 해당 하는 `MefComponent` extension.vsixmanifest 파일의 요소입니다. 이 요소는 VSIX 패키지 확장 어셈블리의 이름을 지정합니다. 자세한 내용은 [MEFComponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))합니다.

11. 에 **소스** 목록에서 선택 **현재 솔루션의 프로젝트**합니다.

12. 에 **프로젝트** 목록에서 선택 **ProjectItemTypeDefinition**를 선택한 후는 **확인** 단추입니다.

13. 메뉴 모음에서 선택 **빌드합니다** > **솔루션 빌드**, 프로젝트가 오류 없이 컴파일되는지 확인 한 후 확인 합니다.

## <a name="test-the-project-template"></a>테스트 프로젝트 템플릿
 이제 프로젝트 템플릿을 테스트할 준비가 되었습니다. 먼저 Visual Studio의 실험적 인스턴스에서 SiteColumnProjectItem 솔루션 디버깅을 시작 합니다. 그런 다음 테스트를 **사이트 열** Visual Studio의 실험적 인스턴스에서 프로젝트입니다. 마지막으로, 빌드 및 사이트 열이 예상 대로 작동 하는지 확인 하려면 SharePoint 프로젝트를 실행 합니다.

#### <a name="to-start-debugging-the-solution"></a>솔루션 디버깅을 시작 하려면

1. 관리자 자격 증명을 사용 하 여 Visual Studio를 다시 시작 하 고 SiteColumnProjectItem 솔루션을 엽니다.

2. SiteColumnProjectItemTypeProvider 코드 파일에서 중단점에서 코드의 첫 번째 줄을 추가 합니다 `InitializeType` 메서드를 선택한 후는 **F5** 디버깅을 시작 하는 키입니다.

     Visual Studio %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0에 확장이 설치 되 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에 있는 프로젝트 항목을 테스트 합니다.

#### <a name="to-test-the-project-in-visual-studio"></a>Visual Studio에서 프로젝트를 테스트 하려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **파일** > **새로 만들기** > **프로젝트**합니다.

2. 확장을 **Visual C#** 또는 **Visual Basic** (언어 프로젝트 템플릿을 지)에 따라 노드를 확장 합니다 **SharePoint** 노드를 선택한 후의 **2010** 노드.

3. 프로젝트 템플릿 목록에서 선택 합니다 **사이트 열** 템플릿.

4. 에 **이름** 상자에 입력 합니다 **SiteColumnTest** 를 선택한 후는 **확인** 단추입니다.

     **솔루션 탐색기**, 명명 된 프로젝트 항목을 사용 하 여 새 프로젝트가 나타납니다 **Field1**합니다.

5. 다른 인스턴스의 Visual Studio의 코드에서 이전에 설정한 중단점에서 중지 확인 합니다 `InitializeType` 메서드를 선택한 후 합니다 **F5** 계속 프로젝트를 디버그 하려면 키.

6. **솔루션 탐색기**를 선택 합니다 **Field1** 노드를 선택한 후는 **F4** 키입니다.

     합니다 **속성** 창이 열립니다.

7. 속성 목록 확인 속성 **속성의 예로** 나타납니다.

#### <a name="to-test-the-site-column-in-sharepoint"></a>SharePoint에서 사이트 열을 테스트 하려면

1. **솔루션 탐색기**를 선택 합니다 **SiteColumnTest** 노드.

2. 에 **속성** 창 옆에 있는 텍스트 상자에는 **사이트 URL** 속성인 입력 **http://localhost**합니다.

     이 단계는 디버깅에 사용 하려는 개발 컴퓨터의 로컬 SharePoint 사이트를 지정 합니다.

    > [!NOTE]
    > 합니다 **사이트 URL** 속성 이므로 기본적으로 빈 사이트 열 프로젝트 템플릿에 프로젝트를 만들 때이 값을 수집 하기 위한 마법사를 제공 하지 않습니다. 이 값에 대 한 개발자를 요청 하 고 다음 새 프로젝트에서이 속성을 구성 하는 마법사를 추가 하는 방법에 알아보려면 참조 [연습: 2 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)합니다.

3. **F5** 키를 선택합니다.

     사이트 열 이며 패키지에서 지정 된 SharePoint 사이트에 배포 합니다 **사이트 URL** 프로젝트의 속성입니다. 웹 브라우저에서이 사이트의 기본 페이지로 열립니다.

    > [!NOTE]
    > 경우는 **스크립트 디버깅 사용 안 함** 선택 대화 상자가 나타나면 합니다 **예** 프로젝트 디버그를 계속 하려면 단추입니다.

4. 에 **사이트 작업** 메뉴 선택 **사이트 설정**합니다.

5. 에 **사이트 설정** 페이지의 **갤러리** 목록에서 선택 합니다 **열 사이트** 링크.

6. 사이트 열 목록에 있는지를 확인 한 **사용자 지정 열** 그룹 이라고 하는 열이 포함 되어 **SiteColumnTest**합니다.

7. 웹 브라우저를 닫습니다.

## <a name="clean-up-the-development-computer"></a>개발 컴퓨터 정리
 프로젝트 테스트를 마친 후 프로젝트 템플릿을 Visual Studio의 실험적 인스턴스에서 제거 합니다.

#### <a name="to-clean-up-the-development-computer"></a>개발 컴퓨터를 정리 하려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **도구가** > **확장 및 업데이트**합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장의 목록에서 선택 합니다 **사이트 열** 확장을 선택한 후는 **제거** 단추입니다.

3. 나타나는 대화 상자에서 선택 합니다 **예** 확장을 제거할 것인지 확인 하는 단추입니다.

4. 선택 된 **닫기** 단추 제거를 완료 합니다.

5. Visual Studio (실험적 인스턴스 및 SiteColumnProjectItem 솔루션이 열려 있는 Visual Studio의 인스턴스)의 두 인스턴스를 닫습니다.

## <a name="next-steps"></a>다음 단계
 이 연습을 완료 한 후에 프로젝트 템플릿에 마법사를 추가할 수 있습니다. 사용자가 사이트 열 프로젝트를 만들 때 마법사를 디버깅 하 고 새 솔루션 인지 샌드박스를 사용 하도록 사이트 URL에 대 한 사용자에 게 요청 하 고 마법사를이 정보를 사용 하 여 새 프로젝트를 구성 합니다. 마법사에서도 (예: 기본 형식과 사이트 열 갤러리에 있는 열을 나열 하는 그룹) 열에 대 한 정보를 수집 하 고이 정보를 추가 합니다 *Elements.xml* 새 프로젝트의 파일입니다. 자세한 내용은 [연습: 2 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)합니다.

## <a name="see-also"></a>참고자료

- [연습: 2 부 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint 프로젝트 항목에 대 한 프로젝트 템플릿과 항목 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [SharePoint 프로젝트 시스템의 확장에 데이터를 저장 합니다.](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [SharePoint 도구 확장과 사용자 지정 데이터 연결](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)