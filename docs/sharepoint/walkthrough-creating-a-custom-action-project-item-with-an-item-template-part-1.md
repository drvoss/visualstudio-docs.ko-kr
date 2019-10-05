---
title: 항목 템플릿, 1 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3e00d87079fe4986dc378540c1456508c2afa0b7
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401122"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>연습: 항목 템플릿, 1 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기
  고유한 프로젝트 항목 형식을 생성 하 여 Visual Studio에서 SharePoint 프로젝트 시스템을 확장할 수 있습니다. 이 연습에서는 SharePoint 사이트에서 사용자 지정 작업을 만들려면 SharePoint 프로젝트에 추가할 수 있는 프로젝트 항목을 만들게 됩니다. 사용자 지정 작업에 메뉴 항목을 추가 합니다 **사이트 작업** SharePoint 사이트의 메뉴.

 이 연습에서는 다음 작업을 수행합니다.

- 사용자 지정 작업에 대 한 SharePoint 프로젝트 항목의 새 형식을 정의 하는 Visual Studio 확장을 만들 합니다. 새 프로젝트 항목 형식과 여러 가지 사용자 지정 기능을 구현합니다.

  - Visual Studio에서 사용자 지정 작업에 대 한 디자이너를 표시 하는 등 프로젝트 항목을 관련 된 추가 작업에 대 한 시작 점으로 사용 되는 바로 가기 메뉴입니다.

  - 개발자는 프로젝트 항목 및 포함 하는 프로젝트의 특정 속성을 변경할 때 실행 되는 코드입니다.

  - 프로젝트 항목 옆에 나타나는 사용자 지정 아이콘 **솔루션 탐색기**합니다.

- 프로젝트 항목에 대 한 Visual Studio 항목 템플릿 만들기.

- 프로젝트 항목 템플릿 및 확장 프로그램 어셈블리를 배포 하는 Visual Studio 확장 (VSIX) 패키지를 빌드합니다.

- 디버깅 및 프로젝트 항목을 테스트 합니다.

  독립 실행형 연습입니다. 이 연습을 완료 한 후 마법사 항목 템플릿을 추가 하 여 프로젝트 항목을 개선할 수 있습니다. 자세한 내용은 [연습: 항목 템플릿, 2 부를 사용 하 여 사용자 지정 작업 프로젝트 항목을 만들어](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)합니다.

> [!NOTE]
> 샘플을 다운로드할 수 있습니다 [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) 워크플로에 대 한 사용자 지정 활동을 만드는 방법을 보여 주는 합니다.

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료 하려면 개발 컴퓨터의 다음 구성 요소가 필요 합니다.

- Microsoft Windows, SharePoint, Visual Studio의 버전을 지원 합니다.

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] 이 연습에서는 합니다 **VSIX 프로젝트** 템플릿 프로젝트 항목을 배포 하려면 VSIX 패키지를 만들려면 sdk에서. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)합니다.

  다음 개념을 이해에 도움이 필요 하지는 않지만, 연습을 완료 하는:

- SharePoint에서 사용자 지정 동작입니다. 자세한 내용은 [사용자 지정 동작](http://go.microsoft.com/fwlink/?LinkId=177800)합니다.

- Visual Studio에서 항목 템플릿입니다. 자세한 내용은 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)를 참조하세요.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 세 개의 프로젝트를 만들려면:

- VSIX 프로젝트입니다. 이 프로젝트에는 SharePoint 프로젝트 항목을 배포 하려면 VSIX 패키지를 만듭니다.

- 항목 템플릿 프로젝트입니다. 이 프로젝트는 SharePoint 프로젝트에 SharePoint 프로젝트 항목을 추가할 수 있는 항목 템플릿을 만듭니다.

- 클래스 라이브러리 프로젝트입니다. 이 프로젝트는 SharePoint 프로젝트 항목의 동작을 정의 하는 Visual Studio 확장을 구현 합니다.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. 맨 위에 있는 목록에는 **새 프로젝트** 대화 상자에서 확인 **.NET Framework 4.5** 선택.

4. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 노드를 선택한 후 합니다 **확장성** 노드.

    > [!NOTE]
    > 합니다 **확장성** 노드는 Visual Studio SDK를 설치 하는 경우에 사용할 수 있습니다. 자세한 내용은이 항목 앞부분의 전제 조건 섹션을 참조 하세요.

5. 선택 된 **VSIX 프로젝트** 템플릿.

6. 에 **이름** 상자에 입력 합니다 **CustomActionProjectItem**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **CustomActionProjectItem** 프로젝트가 **솔루션 탐색기**합니다.

#### <a name="to-create-the-item-template-project"></a>항목 템플릿 프로젝트를 만들려면

1. **솔루션 탐색기**솔루션 노드의 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 프로젝트**합니다.

2. 맨 위에 있는 목록에는 **새 프로젝트** 대화 상자에서 확인 **.NET Framework 4.5** 선택.

3. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 노드를 선택한 후 합니다 **확장성** 노드.

4. 프로젝트 템플릿 목록에서 선택 합니다 **C# 항목 템플릿에** 또는 **Visual Basic 항목 템플릿을** 템플릿.

5. 에 **이름** 상자에 입력 합니다 **ItemTemplate**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **ItemTemplate** 프로젝트를 솔루션입니다.

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**솔루션 노드의 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 프로젝트**합니다.

2. 맨 위에 있는 목록에는 **새 프로젝트** 대화 상자에서 확인 **.NET Framework 4.5** 선택.

3. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 노드를 선택 합니다 **Windows** 노드를를 선택한 다음 합니다  **클래스 라이브러리** 프로젝트 템플릿.

4. 에 **이름** 상자에 입력 합니다 **ProjectItemDefinition**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **ProjectItemDefinition** 솔루션에 프로젝트를 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-extension-project"></a>확장 프로젝트를 구성 합니다.
 SharePoint 프로젝트 항목 형식을 정의 하는 코드를 작성 하기 전에 코드 파일 및 확장 프로젝트에 대 한 어셈블리 참조를 추가 해야 합니다.

#### <a name="to-configure-the-project"></a>프로젝트를 구성 하려면

1. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **ProjectItemDefinition** 프로젝트 **추가**, 선택한 **새 항목**합니다.

2. 프로젝트 항목의 목록에서 선택 **코드 파일**합니다.

3. 에 **이름을** 상자에 이름을 입력 합니다 **CustomAction** 적절 한 파일 이름 확장명을 선택한 후는 **추가** 단추입니다.

4. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **ProjectItemDefinition** 프로젝트를 선택한 후 **참조 추가**합니다.

5. 에 **참조 관리자-ProjectItemDefinition** 대화 상자를 선택 합니다 **어셈블리** 노드를 선택한 후는 **프레임 워크** 노드.

6. 각 다음 어셈블리 옆의 확인란을 선택 합니다.

    - System.ComponentModel.Composition

    - System.Windows.Forms

7. 선택 합니다 **확장** 노드를 Microsoft.VisualStudio.Sharepoint 어셈블리 옆의 확인란을 선택 하 고 선택한 합니다 **확인** 단추입니다.

## <a name="define-the-new-sharepoint-project-item-type"></a>새 SharePoint 프로젝트 항목 형식 정의
 구현 하는 클래스를 만들기는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 새 프로젝트 항목 형식의 동작을 정의 하는 인터페이스입니다. 새 프로젝트 항목 형식의 정의 하려는 경우이 인터페이스를 구현 합니다.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>새 SharePoint 프로젝트 항목 형식 정의

1. ProjectItemDefinition 프로젝트에서 CustomAction 코드 파일을 엽니다.

2. 이 파일의 코드를 다음 코드로 바꿉니다.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>솔루션 탐색기에서 프로젝트 항목에 대 한 아이콘 만들기
 사용자 지정 SharePoint 프로젝트 항목을 만들 때 프로젝트 항목을 사용 하 여 (아이콘 또는 비트맵) 이미지를 연결할 수 있습니다. 이 이미지에서 프로젝트 항목 옆에 나타납니다 **솔루션 탐색기**합니다.

 다음 절차에서는 프로젝트 항목에 대 한 아이콘이 만들고 확장 프로그램 어셈블리에 아이콘을 포함 합니다. 이 아이콘에서 참조 되는 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> 의 `CustomActionProjectItemTypeProvider` 앞에서 만든 클래스.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>프로젝트 항목에 대 한 사용자 지정 아이콘을 만들려면

1. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **ProjectItemDefinition** 프로젝트 **추가**를 선택한 후 **새 항목...** .

2. 프로젝트 항목의 목록에서 선택 합니다 **아이콘 파일** 항목입니다.

    > [!NOTE]
    > Visual Basic 프로젝트에서 선택 해야 합니다 **일반** 표시할 노드를 **아이콘 파일** 항목입니다.

3. 에 **이름** 상자에 입력 합니다 **CustomAction_SolutionExplorer.ico**를 선택한 후는 **추가** 단추입니다.

     새 아이콘의 엽니다는 **이미지 편집기**합니다.

4. 디자인를 인식 하 고 다음 아이콘 파일을 저장할 수 있도록 버전 16 x 16 아이콘 파일을 편집 합니다.

5. **솔루션 탐색기**, 선택 **CustomAction_SolutionExplorer.ico**합니다.

6. 에 **속성** 창 옆의 화살표를 선택 합니다 **빌드 작업** 속성입니다.

7. 표시 되는 목록에서 선택 **포함 리소스**합니다.

## <a name="checkpoint"></a>검사점
 이 연습에서는 프로젝트 항목에 대 한 모든 코드 프로젝트에 포함 되었습니다. 오류 없이 컴파일되는지 확인 하려면 프로젝트를 빌드하십시오.

#### <a name="to-build-your-project"></a>프로젝트를 빌드하려면

1. 바로 가기 메뉴를 열고 합니다 **ProjectItemDefinition** 프로젝트를 선택 **빌드**합니다.

## <a name="create-a-visual-studio-item-template"></a>Visual Studio 항목 템플릿 만들기
 다른 개발자가 프로젝트 항목을 사용할 수 있도록 프로젝트 템플릿 또는 항목 템플릿을 만들어야 합니다. 새 프로젝트를 만들거나 기존 프로젝트에 항목을 추가 하 여 프로젝트 항목의 인스턴스를 만들려면 Visual Studio에서 이러한 템플릿을 사용 하는 개발자. 이 연습에서는 프로젝트 항목을 구성 하려면 ItemTemplate 프로젝트를 사용 합니다.

#### <a name="to-create-the-item-template"></a>항목 템플릿을 만들려면

1. ItemTemplate 프로젝트에서 Class1 코드 파일을 삭제 합니다.

2. ItemTemplate 프로젝트에서 엽니다는 *ItemTemplate.vstemplate* 파일입니다.

3. 파일의 내용을 다음 XML을 바꿉니다 하 고 저장 한 다음 파일을 닫습니다.

    > [!NOTE]
    > Visual C# 항목 템플릿에 대 한 다음 XML은입니다. Visual Basic 항목 템플릿을 만들려는 경우 대체 값을 `ProjectType` 요소 `VisualBasic`합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
      <TemplateData>
        <DefaultName>CustomAction</DefaultName>
        <Name>Custom Action</Name>
        <Description>SharePoint Custom Action by Contoso</Description>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>1000</SortOrder>
        <Icon>ItemTemplate.ico</Icon>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
      <TemplateContent>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>
      </TemplateContent>
    </VSTemplate>
    ```

     이 파일 내용 및 항목 템플릿의 동작을 정의합니다. 이 파일의 콘텐츠에 대 한 자세한 내용은 참조 [Visual Studio 템플릿 스키마 참조](/visualstudio/extensibility/visual-studio-template-schema-reference)합니다.

4. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **ItemTemplate** 프로젝트를 선택 **추가**를 선택한 후 **새 항목**합니다.

5. 에 **새 항목 추가** 대화 상자를 선택 합니다 **텍스트 파일** 템플릿.

6. 에 **이름** 상자에 입력 합니다 **CustomAction.spdata**를 선택한 후는 **추가** 단추입니다.

7. 다음 XML을 추가 합니다 *CustomAction.spdata* 파일 및 그런 다음 저장 하 고 파일을 닫습니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     이 파일 프로젝트 항목에 포함 된 파일에 대 한 정보를 포함 합니다. `Type` 특성을 `ProjectItem` 요소에 전달 되는 동일한 문자열에 설정 해야 합니다는 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 프로젝트 항목 정의 대 (는 `CustomActionProjectItemTypeProvider` 이 연습의 앞부분에서 만든 클래스). 내용에 대 한 자세한 내용은 *.spdata* 파일을 참조 하십시오 [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)합니다.

8. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **ItemTemplate** 프로젝트를 선택 **추가**를 선택한 후 **새 항목**합니다.

9. 에 **새 항목 추가** 대화 상자를 선택 합니다 **XML 파일** 템플릿.

10. 에 **이름** 상자에 입력 합니다 **Elements.xml**를 선택한 후는 **추가** 단추입니다.

11. 내용을 대체 합니다 *Elements.xml* 다음 XML을 사용 하 여 파일 및 그런 다음 저장 하 고 파일을 닫습니다.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="Replace this with a GUID or some other unique string"
                    GroupId="SiteActions"
                    Location="Microsoft.SharePoint.StandardMenu"
                    Sequence="1000"
                    Title="Replace this with your title"
                    Description="Replace this with your description" >
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>
      </CustomAction>
    </Elements>
    ```

     이 파일에 메뉴 항목을 만드는 기본 사용자 지정 작업을 정의 합니다 **사이트 작업** SharePoint 사이트의 메뉴. URL에 지정 된 메뉴 항목을 선택할 경우는 `UrlAction` 웹 브라우저에서 엽니다. 사용자 지정 동작을 정의 하려면 사용할 수 있는 XML 요소에 대 한 자세한 내용은 참조 하세요. [사용자 지정 작업 정의가](http://go.microsoft.com/fwlink/?LinkId=177801)합니다.

12. 필요에 따라 엽니다는 *ItemTemplate.ico* 파일과 인식할 수 있는 디자인을 수정 합니다. 이 아이콘 옆에 있는 프로젝트 항목에 표시 됩니다는 **새 항목 추가** 대화 상자.

13. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **ItemTemplate** 프로젝트를 선택한 후 **프로젝트 언로드**합니다.

14. 바로 가기 메뉴를 열고 합니다 **ItemTemplate** 다시 프로젝트를 선택한 다음 **편집 ItemTemplate.csproj** 또는 **ItemTemplate.vbproj 편집**합니다.

15. 다음 찾기 `VSTemplate` 프로젝트 파일의 요소입니다.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. 대체 `VSTemplate` 다음 XML 및 다음 저장 및 닫기 파일을 사용 하 여 요소입니다.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` 요소 항목 템플릿을 프로젝트를 빌드할 때 생성 되는 경로에 추가 폴더를 지정 합니다. 여기에 지정 된 폴더는 고객에 게 열면 항목 템플릿을 사용할 수 있게 합니다 **새 항목 추가** 대화 상자에서 합니다 **SharePoint** 노드를 선택한 후는 **2010**  노드.

17. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **ItemTemplate** 프로젝트를 선택한 후 **프로젝트 다시 로드**합니다.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>프로젝트 항목을 배포 하려면 VSIX 패키지 만들기
 확장을 배포 하려면 솔루션에서 VSIX 프로젝트를 사용 하 여 VSIX 패키지를 만듭니다. VSIX 프로젝트에 포함 된 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 먼저 구성 합니다. 그런 다음 솔루션을 구축 하 여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX 패키지를 만들고 구성 하려면

1. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **source.extension.vsixmanifest** CustomActionProjectItem 프로젝트에서 파일을 선택한 **엽니다**합니다.

     Visual Studio 매니페스트 편집기에서 파일을 엽니다. Source.extension.vsixmanifest 파일에는 모든 VSIX 패키지 해야 하는 extension.vsixmanifest 파일에 대 한 기반이 됩니다. 이 파일에 대 한 자세한 내용은 참조 하세요. [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)합니다.

2. 에 **Product Name** 상자에 입력 합니다 **사용자 지정 작업 프로젝트 항목**합니다.

3. 에 **작성자** 상자에 입력 합니다 **Contoso**합니다.

4. 에 **설명을** 상자에 입력 합니다 **SharePoint 프로젝트 항목 사용자 지정 동작을 나타내는**합니다.

5. 에 **자산** 탭을 선택 합니다 **새로 만들기** 단추입니다.

     합니다 **새 자산 추가** 대화 상자가 나타납니다.

6. 에 **형식** 목록에서 선택 **Microsoft.VisualStudio.ItemTemplate**합니다.

    > [!NOTE]
    > 이 값에 해당 하는 `ItemTemplate` extension.vsixmanifest 파일의 요소입니다. 이 요소는 프로젝트 항목 템플릿이 포함 된 VSIX 패키지의 하위 폴더를 식별 합니다. 자세한 내용은 [ItemTemplate 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\))합니다.

7. 에 **소스** 목록에서 선택 **현재 솔루션의 프로젝트**합니다.

8. 에 **프로젝트** 목록에서 선택 **ItemTemplate**를 선택한 후는 **확인** 단추입니다.

9. 에 **자산** 탭을 선택 합니다 **새로 만들기** 단추를 다시 합니다.

     합니다 **새 자산 추가** 대화 상자가 나타납니다.

10. 에 **형식** 목록에서 선택 **Microsoft.VisualStudio.MefComponent**합니다.

    > [!NOTE]
    > 이 값에 해당 하는 `MefComponent` extension.vsixmanifest 파일의 요소입니다. 이 요소는 VSIX 패키지 확장 어셈블리의 이름을 지정합니다. 자세한 내용은 [MEFComponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))합니다.

11. 에 **소스** 목록에서 선택 **현재 솔루션의 프로젝트**합니다.

12. 에 **프로젝트** 목록에서 선택 **ProjectItemDefinition**합니다.

13. **확인** 단추를 선택합니다.

14. 메뉴 모음에서 선택 **빌드합니다** > **솔루션 빌드**, 프로젝트가 오류 없이 컴파일되는지 확인 한 후 확인 합니다.

15. CustomActionProjectItem 프로젝트의 빌드 출력 폴더 CustomActionProjectItem.vsix 파일이 있는지 확인 합니다.

     빌드 출력 폴더는 기본적으로... CustomActionProjectItem 프로젝트가 포함 된 폴더 아래에 있는 \bin\Debug 폴더입니다.

## <a name="test-the-project-item"></a>프로젝트 항목 테스트
 프로젝트 항목을 테스트할 준비가 되었습니다. 먼저 Visual Studio의 실험적 인스턴스에서 CustomActionProjectItem 솔루션 디버깅을 시작 합니다. 그런 다음 테스트를 **사용자 지정 작업** 실험적 인스턴스의 Visual Studio에서 SharePoint 프로젝트의 프로젝트 항목입니다. 마지막으로, 빌드 및 사용자 지정 작업이 예상 대로 작동 하는지 확인 하려면 SharePoint 프로젝트를 실행 합니다.

#### <a name="to-start-debugging-the-solution"></a>솔루션 디버깅을 시작 하려면

1. 관리자 자격 증명을 사용 하 여 Visual Studio를 다시 시작 하 고 CustomActionProjectItem 솔루션을 엽니다.

2. CustomAction 코드 파일을 열고 다음 코드의 첫 번째 줄에 중단점을 추가 합니다 `InitializeType` 메서드.

3. 선택 된 **F5** 디버깅을 시작 하는 키입니다.

     Visual Studio 작업 프로젝트 Item\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom에 확장이 설치 되 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에 있는 프로젝트 항목을 테스트할 합니다.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Visual Studio에서 프로젝트 항목을 테스트 하려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **파일** > **새로 만들기** > **프로젝트**합니다.

2. 확장 **Visual C#** 또는 **Visual Basic** (언어에 따라 항목 템플릿을 지 원하는)을 확장 하 고 **SharePoint**를 선택한 후는 **2010**  노드.

3. 프로젝트 템플릿 목록에서 선택 **SharePoint 2010 프로젝트**합니다.

4. 에 **이름** 상자에 입력 합니다 **CustomActionTest**를 선택한 후는 **확인** 단추입니다.

5. 에 **SharePoint 사용자 지정 마법사**, 디버깅을 위해 사용 하려는 사이트의 URL을 입력 하 고 선택한 합니다 **마침** 단추입니다.

6. **솔루션 탐색기**프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 항목**합니다.

7. 에 **새 항목 추가** 대화 상자를 선택 합니다 **2010** 노드에서 **SharePoint** 노드.

     있는지 확인 합니다 **사용자 지정 작업** 항목 프로젝트 항목의 목록에 나타납니다.

8. 선택 된 **사용자 지정 동작** 항목을 선택한 후는 **추가** 단추입니다.

     이라고 하는 항목을 추가 하는 visual Studio **CustomAction1** 열립니다 프로젝트에는 *Elements.xml* 파일을 편집기에서.

9. Visual Studio의 다른 인스턴스에 코드에서 이전에 설정한 중단점에서 중지 확인을 `InitializeType` 메서드.

10. 선택 합니다 **F5** 키를 계속 프로젝트를 디버깅 합니다.

11. Visual Studio의 실험적 인스턴스에서 **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **CustomAction1** 노드를 선택한 후 **뷰 사용자 지정 작업 디자이너**.

12. 메시지 상자가 나타나는지 확인 한 다음를 선택 합니다 **확인** 단추입니다.

     사용자 지정 작업에 대 한 디자이너를 표시 하는 등 개발자를 위한 추가 옵션 또는 명령을 수 있도록이 바로 가기 메뉴를 사용할 수 있습니다.

13. 메뉴 모음에서 선택 **뷰** > **출력**합니다.

     합니다 **출력** 창이 열립니다.

14. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **CustomAction1** 항목을 선택한 다음 해당 이름을 변경 **MyCustomAction**합니다.

     에 **출력** 창에서 확인 메시지가 나타납니다. 이 메시지는 기록 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> 에 정의 된 이벤트 처리기는 `CustomActionProjectItemTypeProvider` 클래스입니다. 이 이벤트와 개발자는 프로젝트 항목을 수정할 때 사용자 지정 동작을 구현 하려면 다른 프로젝트 항목 이벤트를 처리할 수 있습니다.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>SharePoint에서 사용자 지정 작업을 테스트 하려면

1. Visual Studio의 실험적 인스턴스를 엽니다는 *Elements.xml* 의 자식 파일을 **MyCustomAction** 프로젝트 항목입니다.

2. 에 *Elements.xml* 파일 다음과 같이 변경 하 고 파일을 저장 합니다.

    - 에 `CustomAction` 요소를 설정 합니다 `Id` GUID 또는 다른 고유 문자열에 다음 예제와 같이 특성:

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - 에 `CustomAction` 요소를 설정 합니다 `Title` 다음 예제와 같이 특성:

        ```xml
        Title="SharePoint Developer Center"
        ```

    - 에 `CustomAction` 요소를 설정 합니다 `Description` 다음 예제와 같이 특성:

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - 에 `UrlAction` 요소를 설정 합니다 `Url` 다음 예제와 같이 특성:

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. **F5** 키를 선택합니다.

     사용자 지정 작업 이며 패키지에서 지정 된 SharePoint 사이트에 배포 합니다 **사이트 URL** 프로젝트의 속성입니다. 웹 브라우저에서이 사이트의 기본 페이지로 열립니다.

    > [!NOTE]
    > 경우는 **스크립트 디버깅 사용 안 함** 선택 대화 상자가 나타나면 합니다 **예** 프로젝트 디버그를 계속 하려면 단추입니다.

4. 에 **사이트 작업** 메뉴 선택 **SharePoint 개발자 센터**, 브라우저가 열리고 웹 사이트를 확인 https://docs.microsoft.com/sharepoint/dev/, 한 다음 웹 브라우저를 닫습니다.

## <a name="clean-up-the-development-computer"></a>개발 컴퓨터 정리
 프로젝트 항목의 테스트를 마친 후에 Visual Studio의 실험적 인스턴스에서 프로젝트 항목 템플릿을 제거 합니다.

#### <a name="to-clean-up-the-development-computer"></a>개발 컴퓨터를 정리 하려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **도구가** > **확장 및 업데이트**합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장의 목록에서 선택 **사용자 지정 작업 프로젝트 항목**를 선택 합니다 **제거** 단추입니다.

3. 나타나는 대화 상자에서 선택 합니다 **예** 확장을 제거할 것인지 확인 하는 단추입니다.

4. 선택 된 **지금 다시 시작** 단추 제거를 완료 합니다.

5. Visual Studio의 실험적 인스턴스 및 CustomActionProjectItem 솔루션 열기의 인스턴스를 모두 닫습니다.

## <a name="next-steps"></a>다음 단계
 이 연습을 완료 한 후에 항목 템플릿에 마법사를 추가할 수 있습니다. 사용자가 사용자 지정 작업 프로젝트 항목을 SharePoint 프로젝트에 추가 마법사 (예: 위치 및 동작을 선택할 때 탐색할 URL) 작업에 대 한 정보를 수집 하 고이 정보를 추가 합니다 *Elements.xml*새 프로젝트 항목에는 파일입니다. 자세한 내용은 [연습: 항목 템플릿, 2 부를 사용 하 여 사용자 지정 작업 프로젝트 항목을 만들어](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)합니다.

## <a name="see-also"></a>참고자료

- [연습: 항목 템플릿, 2 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint 프로젝트 항목에 대 한 프로젝트 템플릿과 항목 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)
- [Visual Studio 템플릿 스키마 참조](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [아이콘에 대한 이미지 편집기](/cpp/windows/image-editor-for-icons)
- [아이콘 또는 다른 이미지 만들기 &#40;아이콘에 대 한 이미지 편집기&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)