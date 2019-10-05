---
title: 항목 템플릿, 2 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6fa4915b9621789c68ed994440de3a1ef544c40c
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401170"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>연습: 항목 템플릿, 2 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기
  사용자 지정 형식의 SharePoint 프로젝트 항목을 정의 하 고 Visual Studio에서 항목 템플릿을 사용 하 여 연결 후 템플릿에 대 한 마법사를 제공 하려면 수도 있습니다. 서식 파일 프로젝트에 프로젝트 항목의 새 인스턴스를 추가 하는 데 사용할 사용자 로부터 정보를 수집 하는 마법사를 사용할 수 있습니다. 정보를 수집 하는 프로젝트 항목을 초기화에 사용할 수 있습니다.

 이 연습에서는 사용자 지정 작업 프로젝트 항목에 설명 된 마법사를 추가 합니다 [연습: 항목 템플릿, 1 부를 사용 하 여 사용자 지정 작업 프로젝트 항목을 만들어](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)합니다. 사용자가 사용자 지정 작업 프로젝트 항목을 SharePoint 프로젝트에 추가 하는 경우 마법사는 사용자 지정 작업 (예: 위치 및 최종 사용자가이 선택할 때 탐색할 URL)에 대 한 정보를 수집 하는이 정보를 추가 하 고는 *Elements.xml* 새 프로젝트 항목에는 파일입니다.

 이 연습에서는 다음 작업을 수행합니다.

- 항목 템플릿과 사용 하 여 연결 된 사용자 지정 SharePoint 프로젝트 항목 형식 위한 마법사를 만드는 중입니다.

- 사용자 지정 마법사 Visual Studio에서 SharePoint 프로젝트 항목에 대 한 기본 제공 마법사 유사한 UI를 정의 합니다.

- 대체 가능 매개 변수를 사용 하 여 마법사에서 수집 하는 데이터를 사용 하 여 SharePoint 프로젝트 파일을 초기화 합니다.

- 디버깅 하 고 마법사를 테스트 합니다.

> [!NOTE]
> 샘플을 다운로드할 수 있습니다 [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) 워크플로에 대 한 사용자 지정 활동을 만드는 방법을 보여 주는 합니다.

## <a name="prerequisites"></a>전제 조건
 이 연습을 수행 하려면 먼저 만들어야 CustomActionProjectItem 솔루션 완료 하 여 [연습: 항목 템플릿, 1 부를 사용 하 여 사용자 지정 작업 프로젝트 항목을 만들어](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)합니다.

 또한이 연습을 완료 하려면 개발 컴퓨터의 다음 구성 요소가 필요 합니다.

- Windows, SharePoint 및 Visual Studio의 버전을 지원 합니다.

- Visual Studio SDK입니다. 이 연습에서는 합니다 **VSIX 프로젝트** 템플릿 프로젝트 항목을 배포 하려면 VSIX 패키지를 만들려면 sdk에서. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)합니다.

  다음 개념을 이해에 도움이 필요 하지는 않지만, 연습을 완료 하는:

- Visual Studio에서 프로젝트 및 항목 템플릿에 대 한 마법사를 제공 합니다. 자세한 내용은 [방법: 프로젝트 템플릿에 마법사 사용](../extensibility/how-to-use-wizards-with-project-templates.md) 하며 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 인터페이스입니다.

- SharePoint에서 사용자 지정 동작입니다. 자세한 내용은 [사용자 지정 동작](http://go.microsoft.com/fwlink/?LinkId=177800)합니다.

## <a name="create-the-wizard-project"></a>마법사 프로젝트를 만들려면
 만든 CustomActionProjectItem 솔루션에 프로젝트를 추가 해야 하는이 연습을 완료 하려면 [연습: 항목 템플릿, 1 부를 사용 하 여 사용자 지정 작업 프로젝트 항목을 만들어](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)합니다. 구현 합니다 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 인터페이스 및이 프로젝트에서 마법사 UI를 정의 합니다.

#### <a name="to-create-the-wizard-project"></a>마법사 프로젝트를 만들려면

1. Visual Studio에서 CustomActionProjectItem 솔루션을 엽니다

2. **솔루션 탐색기**솔루션 노드의 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 프로젝트**합니다.

3. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 노드를 선택한 후 합니다 **Windows** 노드.

4. 맨 위에 있는 **새 프로젝트** 대화 상자에서 확인 **.NET Framework 4.5** 버전의.NET Framework의 목록에서 선택 됩니다.

5. 선택 합니다 **WPF 사용자 정의 컨트롤 라이브러리** 템플릿 프로젝트에서 프로젝트의 이름을 **ItemTemplateWizard**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **ItemTemplateWizard** 프로젝트를 솔루션입니다.

6. 프로젝트에서 UserControl1 항목을 삭제 합니다.

## <a name="configure-the-wizard-project"></a>마법사 프로젝트를 구성 합니다.
 마법사를 만들기 전에 Windows Presentation Foundation (WPF) 창, 코드 파일 및 어셈블리 참조를 프로젝트에 추가 해야 합니다.

#### <a name="to-configure-the-wizard-project"></a>마법사 프로젝트를 구성 하려면

1. **솔루션 탐색기**에서 바로 가기 메뉴를 열고 합니다 **ItemTemplateWizard** 프로젝트 노드를 선택한 후 **속성**합니다.

2. 에 **프로젝트 디자이너**, 대상 프레임 워크가.NET Framework 4.5로 설정 되어 있는지 확인 합니다.

     Visual C# 프로젝트의 경우에이 값을 설정할 수 있습니다 합니다 **응용 프로그램** 탭 합니다. Visual Basic 프로젝트에서이 값을 설정할 수 있습니다 합니다 **컴파일** 탭 합니다. 자세한 내용은 [방법: 한 버전의 .NET Framework를 대상으로 지정](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

3. 에 **ItemTemplateWizard** 프로젝트를 추가 **창 (WPF)** 프로젝트에 항목 및 다음 항목의 이름을 **WizardWindow**합니다.

4. CustomActionWizard 문자열과 이름이 지정 된 코드 파일을 두 개를 추가 합니다.

5. 바로 가기 메뉴를 열고 합니다 **ItemTemplateWizard** 프로젝트를 선택한 후 **참조 추가**합니다.

6. 에 **참조 관리자-ItemTemplateWizard** 대화 상자의 **어셈블리** 노드를 선택 합니다 **확장** 노드.

7. 선택한 후 다음 어셈블리 옆의 확인란을 선택 합니다 **확인** 단추:

    - EnvDTE

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

8. **솔루션 탐색기**를 **참조** ItemTemplateWizard 프로젝트 폴더를 선택 합니다 **EnvDTE** 참조 합니다.

9. 에 **속성** 창에서의 값을 변경 합니다 **Interop 형식 포함** 속성을 **False**.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>기본 위치 및 사용자 지정 작업에 대 한 ID 문자열을 정의 합니다.
 위치 및 ID에 지정 된 모든 사용자 지정 작업에는 `GroupID` 및 `Location` 의 특성을 `CustomAction` 요소에는 *Elements.xml* 파일입니다. 이 단계에서는 일부 ItemTemplateWizard 프로젝트에서 이러한 특성에 대 한 유효한 문자열을 정의합니다. 이 연습을 완료 하는 경우 이러한 문자열에 기록 됩니다 합니다 *Elements.xml* 마법사에서 위치 및 ID를 지정 하는 사용자가 사용자 지정 작업 프로젝트 항목에는 파일입니다.

 편의상이 샘플에 사용 가능한 기본 위치 및 Id의 하위 집합만을 지원합니다. 전체 목록을 참조 하세요 [기본 사용자 지정 작업 위치 및 Id](http://go.microsoft.com/fwlink/?LinkId=181964)합니다.

#### <a name="to-define-the-default-location-and-id-strings"></a>기본 위치 및 ID 문자열을 정의 하려면

1. 엽니다.

2. 에 **ItemTemplateWizard** 프로젝트, 문자열 코드 파일의 코드를 다음 코드로 바꿉니다.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]

## <a name="create-the-wizard-ui"></a>마법사 UI 만들기
 마법사의 UI를 정의 하는 XAML을 추가 하 고 바인딩할 일부 컨트롤이 마법사에서 ID 문자열을 일부 코드를 추가 합니다. 사용자가 만든 마법사에는 Visual Studio에서 SharePoint 프로젝트에 대 한 기본 제공 마법사와 유사 합니다.

#### <a name="to-create-the-wizard-ui"></a>마법사 UI를 만들려면

1. 에 **ItemTemplateWizard** 프로젝트를 바로 가기 메뉴를 열고는 **WizardWindow.xaml** 파일을 선택한 후 **엽니다** 디자이너에서 창을 열려면 합니다.

2. XAML 보기에서 다음 XAML을 사용 하 여 현재 XAML을 대체 합니다. XAML 창의 맨 아래에 있는 탐색 단추 확인 하 고 사용자 지정 작업의 동작을 지정 하기 위한 컨트롤, 머리글을 포함 하는 UI를 정의 합니다.

    > [!NOTE]
    > 프로젝트는이 코드를 추가 하면 컴파일 오류가 발생 해야 합니다. 이러한 오류가 사라집니다 이후 단계에서 코드를 추가 합니다.

     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]

    > [!NOTE]
    > 이 XAML에서 만든 창에서 파생 되는 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 기본 클래스입니다. Visual Studio를 사용자 지정 WPF 대화 상자를 추가 하면 Visual Studio의 다른 대화 상자와 일관성 있는 스타일을 모달 대화 상자를 사용 하 여 발생할 수 있는 문제를 방지 하려면이 클래스에서 대화 상자를 파생 하는 것이 좋습니다. 자세한 내용은 [만들고 모달 대화 상자 관리](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes)합니다.

3. Visual Basic 프로젝트를 개발 하는 경우 제거를 `ItemTemplateWizard` 에서 네임 스페이스를 `WizardWindow` 클래스 이름을 `x:Class` 특성을 `Window` 요소. 이 요소는 XAML의 첫 번째 줄에는입니다. 완료 되 면 첫 번째 줄에 다음 코드는 같아야 합니다.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. WizardWindow.xaml 파일에 대 한 코드 숨김 파일에서 현재 코드를 다음 코드로 바꿉니다.

     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]

## <a name="implement-the-wizard"></a>구현 마법사
 마법사의 기능을 구현 하 여 정의 된 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 인터페이스입니다.

#### <a name="to-implement-the-wizard"></a>마법사를 구현 하려면

1. **ItemTemplateWizard** 프로젝트를 엽니다는 **CustomActionWizard** 코드 파일을 한 다음이 파일에서 현재 코드를 다음 코드로 바꿉니다.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]

## <a name="checkpoint"></a>검사점
 이 연습에서는 마법사에 대 한 모든 코드 프로젝트에 포함 되었습니다. 오류 없이 컴파일되는지 확인 하려면 프로젝트를 빌드하십시오.

#### <a name="to-build-your-project"></a>프로젝트를 빌드하려면

1. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

## <a name="associate-the-wizard-with-the-item-template"></a>항목 템플릿을 사용 하 여 연결 된 마법사
 마법사를 구현 했으므로 사용 하 여를 연결 해야 하는 **사용자 지정 작업** 세 가지 주요 단계를 완료 하 여 항목 템플릿을:

1. 강력한 이름의 마법사 어셈블리에 서명 합니다.

2. 마법사 어셈블리에 대 한 공개 키를 토큰을 가져옵니다.

3. .Vstemplate 파일에 마법사 어셈블리에 대 한 참조를 추가 합니다 **사용자 지정 작업** 항목 템플릿.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>강력한 이름의 마법사 어셈블리에 서명 하려면

1. **솔루션 탐색기**에서 바로 가기 메뉴를 열고 합니다 **ItemTemplateWizard** 프로젝트 노드를 선택한 후 **속성**합니다.

2. 에 **서명** 탭을 선택 합니다 **어셈블리에 서명** 확인란 합니다.

3. 에 **강력한 이름 키 파일 선택** 목록에서 선택  **\<새로 만들기... >** 합니다.

4. 에 **강력한 이름 키 만들기** 대화 상자에서 지우기 이름을 입력 합니다 **암호로 내 키 파일 보호** 확인란을 선택한 후를 **확인** 단추.

5. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>마법사 어셈블리에 대 한 공개 키 토큰을 가져오려면

1. Visual Studio 명령 프롬프트 창에서 다음을 실행 명령을 바꾸는 *PathToWizardAssembly* ItemTemplateWizard 프로젝트 개발에 대 한 기본 제공된 ItemTemplateWizard.dll 어셈블리의 전체 경로 사용 하 여 컴퓨터입니다.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     에 대 한 공개 키 토큰을 *ItemTemplateWizard.dll* 어셈블리는 Visual Studio 명령 프롬프트 창에 기록 됩니다.

2. Visual Studio 명령 프롬프트 창을 열어 둡니다. 다음 절차를 완료 하려면 공개 키 토큰을 해야 합니다.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>.Vstemplate 파일에 마법사 어셈블리에 대 한 참조를 추가 하려면

1. **솔루션 탐색기**를 확장 합니다 **ItemTemplate** 프로젝트 노드를 연 다음 합니다 *ItemTemplate.vstemplate* 파일.

2. 파일의 끝에 다음 추가 `WizardExtension` 사이 요소를 `</TemplateContent>` 및 `</VSTemplate>` 태그입니다. 대체는 *YourToken* 의 값을 `PublicKeyToken` 이전 절차에서 가져온 공개 키 토큰을 사용 하 여 특성입니다.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     에 대 한 자세한 내용은 합니다 `WizardExtension` 요소를 참조 하세요 [WizardExtension 요소 &#40;Visual Studio 템플릿&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates)합니다.

3. 파일을 저장한 후 닫습니다.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>대체 가능 매개 변수를 추가 합니다 *Elements.xml* 항목 템플릿에서 파일
 몇 가지 대체 가능 매개 변수를 추가 합니다 *Elements.xml* ItemTemplate 프로젝트의 파일입니다. 이러한 매개 변수에서 초기화 되는 `PopulateReplacementDictionary` 의 메서드는 `CustomActionWizard` 이전에 정의한 클래스. 사용자가 사용자 지정 작업 프로젝트 항목을 프로젝트에 추가 하는 경우 Visual Studio에서 이러한 매개 변수를 자동으로 대체 합니다 *Elements.xml* 마법사에서 지정한 대로 값을 사용 하 여 새 프로젝트 항목에는 파일입니다.

 대체 가능 매개 변수는 시작 하는 달러 기호 ($) 문자로 끝나는 토큰입니다. 사용자 고유의 대체 가능 매개 변수를 정의 하는 것 외에도 SharePoint 프로젝트 시스템을 정의 하 고 초기화 하는 기본 제공 매개 변수를 사용할 수 있습니다. 자세한 내용은 [대체 가능 매개 변수](../sharepoint/replaceable-parameters.md)합니다.

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>대체 가능 매개 변수를 추가 하는 *Elements.xml* 파일

1. ItemTemplate 프로젝트에서의 내용을 대체 합니다 *Elements.xml* 다음 XML 사용 하 여 파일입니다.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="$IdValue$"
                    GroupId="$GroupIdValue$"
                    Location="$LocationValue$"
                    Sequence="1000"
                    Title="$TitleValue$"
                    Description="$DescriptionValue$" >
        <UrlAction Url="$UrlValue$"/>
      </CustomAction>
    </Elements>
    ```

     값을 변경 하는 새 XML을 `Id`, `GroupId`를 `Location`, `Description`, 및 `Url` 대체 가능 매개 변수 특성입니다.

2. 파일을 저장한 후 닫습니다.

## <a name="add-the-wizard-to-the-vsix-package"></a>VSIX 패키지에 마법사 추가
 VSIX 프로젝트에서 source.extension.vsixmanifest 파일에서 프로젝트 항목을 포함 하는 VSIX 패키지를 사용 하 여 배포 될 수 있도록 마법사 프로젝트에 대 한 참조를 추가 합니다.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>VSIX 패키지에는 마법사를 추가 하려면

1. **솔루션 탐색기**에서 바로 가기 메뉴를 열고 합니다 **source.extension.vsixmanifest** CustomActionProjectItem 프로젝트에서 파일을 선택한 **엽니다** 를 열려면 매니페스트 편집기에서 파일입니다.

2. 매니페스트 편집기에서 선택 합니다 **자산** 탭을 선택한 다음 선택 합니다 **새로 만들기** 단추입니다.

     합니다 **새 자산 추가** 대화 상자가 나타납니다.

3. 에 **형식** 목록에서 선택 **Microsoft.VisualStudio.Assembly**합니다.

4. 에 **소스** 목록에서 선택 **현재 솔루션의 프로젝트**합니다.

5. 에 **프로젝트** 목록에서 선택 **ItemTemplateWizard**를 선택한 후는 **확인** 단추입니다.

6. 메뉴 모음에서 **빌드합니다** > **솔루션 빌드**, 솔루션이 오류 없이 컴파일되는지 확인 한 후 확인 합니다.

## <a name="test-the-wizard"></a>마법사를 테스트 합니다.
 이제 마법사를 테스트할 준비가 되었습니다. 먼저, Visual Studio의 실험적 인스턴스에서 CustomActionProjectItem 솔루션을 디버그를 시작 합니다. 그런 다음 Visual Studio의 실험적 인스턴스에서 SharePoint 프로젝트의 사용자 지정 작업 프로젝트 항목에 대 한 마법사를 테스트 합니다. 마지막으로, 빌드 및 사용자 지정 작업이 예상 대로 작동 하는지 확인 하려면 SharePoint 프로젝트를 실행 합니다.

#### <a name="to-start-to-debug-the-solution"></a>솔루션을 디버그 하려면

1. 관리자 자격 증명을 사용 하 여 Visual Studio를 다시 시작 하 고 CustomActionProjectItem 솔루션을 엽니다.

2. ItemTemplateWizard 프로젝트에서 CustomActionWizard 코드 파일을 열고 다음 코드의 첫 번째 줄에 중단점을 추가 합니다 `RunStarted` 메서드.

3. 메뉴 모음에서 선택 **디버깅할** > **예외**합니다.

4. 에 **예외** 대화 상자에서 확인 합니다 **throw 됨** 및 **사용자가 처리 하지 않은** 에 대 한 확인란 **Common Language Runtime Exceptions**삭제 되 고 다음을 선택 합니다 **확인** 단추입니다.

5. 선택 하 여 디버깅을 시작 합니다 **F5** 키 또는 메뉴 모음에서 **디버그** > **디버깅 시작**합니다.

     Visual Studio 작업 프로젝트 Item\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom에 확장이 설치 되 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에 있는 프로젝트 항목을 테스트할 합니다.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Visual Studio에서 마법사를 테스트 하려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **파일** > **새로 만들기** > **프로젝트**합니다.

2. 확장를 **Visual C#** 또는 **Visual Basic** (언어에 따라 항목 템플릿을 지 원하는), 노드를 확장 합니다 **SharePoint** 노드를 선택한 후의 **2010** 노드.

3. 프로젝트 템플릿 목록에서 선택 **SharePoint 2010 프로젝트**, 프로젝트 이름을 **CustomActionWizardTest**를 선택한 후는 **확인** 단추입니다.

4. 에 **SharePoint 사용자 지정 마법사**, 디버깅을 위해 사용 하려는 사이트의 URL을 입력 하 고 선택한 합니다 **마침** 단추입니다.

5. **솔루션 탐색기**프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 항목**합니다.

6. 에 **새 항목 추가-CustomItemWizardTest** 대화 상자에서 **SharePoint** 노드를 펼친 다음 합니다 **2010** 노드.

7. 프로젝트 항목의 목록에서 선택 합니다 **사용자 지정 동작** 항목을 선택한 다음는 **추가** 단추입니다.

8. Visual Studio의 다른 인스턴스에 코드에서 이전에 설정한 중단점에서 중지 확인을 `RunStarted` 메서드.

9. 프로젝트를 선택 하 여 디버깅을 계속 합니다 **F5** 키 또는 메뉴 모음에서 **디버그** > **계속**합니다.

     SharePoint 사용자 지정 마법사가 나타납니다.

10. 아래 **위치**를 선택 합니다 **목록 편집** 옵션 단추입니다.

11. 에 **그룹 ID** 목록에서 선택 **통신**합니다.

12. 에 **제목** 상자에 입력 합니다 **SharePoint 개발자 센터**합니다.

13. 에 **설명을** 상자에 입력 합니다 **SharePoint 개발자 센터 웹 사이트를 엽니다**합니다.

14. 에 **URL** 상자에 입력 합니다 **https://docs.microsoft.com/sharepoint/dev/** 를 선택한 후는 **마침** 단추.

     이라고 하는 항목을 추가 하는 visual Studio **CustomAction1** 열립니다 프로젝트에는 *Elements.xml* 파일을 편집기에서. 확인 *Elements.xml* 마법사에서 지정한 값을 포함 합니다.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>SharePoint에서 사용자 지정 작업을 테스트 하려면

1. Visual Studio의 실험적 인스턴스를 선택 합니다 **F5** 키 또는 메뉴 모음에서 **디버그** > **디버깅 시작**합니다.

     사용자 지정 작업은 패키지 및 지정 된 SharePoint 사이트에 배포 합니다 **사이트 URL** 프로젝트 및 웹 브라우저의 속성이이 사이트의 기본 페이지로 열립니다.

    > [!NOTE]
    > 경우는 **스크립트 디버깅 사용 안 함** 대화 상자가 나타나면 선택 합니다 **예** 단추입니다.

2. SharePoint 사이트의 목록 영역에서 선택 합니다 **작업** 링크 합니다.

     합니다 **작업-모든 작업** 페이지가 나타납니다.

3. 에 **목록 도구** 탭 리본 메뉴의 선택를 **목록** 탭을 차례로 **설정** 그룹에서 **목록 설정**.

     합니다 **목록 설정** 페이지가 나타납니다.

4. 아래는 **통신** 선택 페이지의 위쪽 머리글를 **SharePoint 개발자 센터** 링크를 브라우저는 웹 사이트 열리는지 확인 https://docs.microsoft.com/sharepoint/dev/, 한 다음 브라우저를 닫습니다.

## <a name="cleaning-up-the-development-computer"></a>개발 컴퓨터 정리
 프로젝트 항목의 테스트를 마친 후에 Visual Studio의 실험적 인스턴스에서 프로젝트 항목 템플릿을 제거 합니다.

#### <a name="to-clean-up-the-development-computer"></a>개발 컴퓨터를 정리 하려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **도구가** > **확장 및 업데이트**합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장의 목록에서 선택 합니다 **사용자 지정 작업 프로젝트 항목** 확장을 선택한 후는 **제거** 단추입니다.

3. 나타나는 대화 상자에서 선택 합니다 **예** 확장을 제거 하 여 선택한 것을 확인 하려면 단추를 **지금 다시 시작** 제거를 완료 하려면 단추입니다.

4. Visual Studio (실험적 인스턴스 및 CustomActionProjectItem 솔루션이 열려 있는 Visual Studio의 인스턴스)의 두 인스턴스를 닫습니다.

## <a name="see-also"></a>참고자료
- [연습: 항목 템플릿, 1 부를 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint 프로젝트 항목에 대 한 프로젝트 템플릿과 항목 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio 템플릿 스키마 참조](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [방법: 프로젝트 템플릿에 마법사 사용](../extensibility/how-to-use-wizards-with-project-templates.md)
- [기본 사용자 지정 작업 위치 및 Id](http://go.microsoft.com/fwlink/?LinkId=181964)
