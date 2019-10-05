---
title: WPF 도구 상자 컨트롤 만들기 | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc124c767ac9a84e62c17fb868e1dc114642f884
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349037"
---
# <a name="create-a-wpf-toolbox-control"></a>WPF 도구 상자 컨트롤 만들기

WPF (Windows Presentation Framework) 도구 상자 컨트롤 템플릿을 통해 자동으로 추가 되는 WPF 컨트롤을 만들 수는 **도구 상자** 확장이 설치 되는 경우. 이 연습에서는 템플릿을 사용 하 여 만드는 방법을 보여 줍니다.는 **도구 상자** 컨트롤을 다른 사용자에 게 배포할 수 있습니다.

Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="create-the-toolbox-control"></a>도구 상자 컨트롤 만들기

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>WPF 도구 상자 컨트롤을 사용 하 여 확장 만들기

1. 라는 VSIX 프로젝트를 만듭니다 `MyToolboxControl`합니다. VSIX 프로젝트 템플릿을 찾을 수 있습니다 합니다 **새 프로젝트** "vsix"를 검색 하 여 대화 상자.

2. 프로젝트를 열면 추가 된 **WPF 도구 상자 컨트롤** 이라는 항목 템플릿을 `MyToolboxControl`합니다. 에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **추가** > **새 항목**합니다. 에 **새 항목 추가** 대화 상자에서로 이동 **Visual C#**  > **확장성** 선택한 **WPF 도구 상자 컨트롤**합니다. 에 **이름을** 창의 맨 아래에 있는 필드에 명령 파일 이름을 *MyToolboxControl.cs*합니다.

    솔루션에는 이제, 사용자 지정 컨트롤이 포함 된를 `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> 컨트롤을 추가 하는 합니다 **도구 상자**, 및 **Microsoft.VisualStudio.ToolboxControl** 에 대 한 VSIX 매니페스트의 자산 항목  배포 합니다.

#### <a name="to-create-the-control-ui"></a>UI 컨트롤을 만들려면

1. 오픈 *MyToolboxControl.xaml* 디자이너에서 합니다.

    디자이너에 <xref:System.Windows.Controls.Button> 컨트롤이 포함된 <xref:System.Windows.Controls.Grid> 컨트롤이 표시됩니다.

2. 표 형태 레이아웃을 정렬 합니다. 선택 하는 경우는 <xref:System.Windows.Controls.Grid> 그리드의 왼쪽된 위 가장자리에 표시 하는 파란색 컨트롤 막대를 제어 합니다. 막대를 클릭 하 여 표에 행과 열을 추가할 수 있습니다.

3. 눈금에 자식 컨트롤을 추가 합니다. 자식 컨트롤에서 끌어서 배치할 수 있습니다 합니다 **도구 상자** 설정 하거나, 그리드의 섹션에 해당 `Grid.Row` 및 `Grid.Column` 는 XAML의 특성입니다. 다음 예제에서는 표 및 행의 두 번째 단추 위쪽 행에 두 개의 레이블을 추가합니다.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>컨트롤 이름 바꾸기

 기본적으로 컨트롤에 표시 됩니다는 **도구 상자** 으로 **MyToolboxControl** 이라는 그룹 **MyToolboxControl.MyToolboxControl**합니다. 이러한 이름을 변경할 수 있습니다 합니다 *MyToolboxControl.xaml.cs* 파일입니다.

1. 오픈 *MyToolboxControl.xaml.cs* 코드 보기에서.

2. 찾기는 `MyToolboxControl` 클래스 및 이름을 TestControl로 변경 합니다. (이 작업을 수행 하는 가장 빠른 방법은 클래스의 이름을 바꾸려면는 선택한 **이름 바꾸기** 상황에 맞는 메뉴에서 한 단계를 완료 합니다. (에 대 한 자세한 내용은 합니다 **이름 바꾸기** 명령을 참조 하십시오 [이름 바꾸기 리팩터링 (C#)](../ide/reference/rename.md).)

3. 로 이동 합니다 `ProvideToolboxControl` 특성 및 첫 번째 매개 변수의 값을 변경 **테스트**합니다. 컨트롤을 포함 하는 그룹의 이름 합니다 **도구 상자**합니다.

    결과 코드는 다음과 같습니다.

    ```csharp
    [ProvideToolboxControl("Test", true)]
    public partial class TestControl : UserControl
    {
        public TestControl()
        {
            InitializeComponent();
        }
    }
    ```

## <a name="build-test-and-deployment"></a>빌드, 테스트 및 배포

 프로젝트를 디버깅할 때에 컨트롤을 설치한를 찾아야 합니다 **도구 상자** Visual Studio의 실험적 인스턴스.

### <a name="to-build-and-test-the-control"></a>컨트롤을 빌드하고 테스트하려면

1. 프로젝트를 다시 작성 하 고 디버깅을 시작 합니다.

2. Visual Studio의 새 인스턴스에서 WPF 애플리케이션 프로젝트를 만듭니다. XAML 디자이너가 열려 있는지 확인 합니다.

3. **도구 상자** 에서 컨트롤을 찾아 디자인 화면으로 끕니다.

4. WPF 응용 프로그램 디버깅을 시작 합니다.

5. 컨트롤이 표시 되는지 확인 합니다.

### <a name="to-deploy-the-control"></a>컨트롤을 배포하려면

1. 테스트 프로젝트를 빌드한 후를 찾을 수 있습니다는 *.vsix* 파일에 * \bin\debug\* 프로젝트의 폴더입니다.

2. 두 번 클릭 하 여 로컬 컴퓨터에 설치할 수 있습니다 합니다 *.vsix* 파일 및 설치 절차를 수행 합니다. 컨트롤을 제거 하려면로 이동 **도구가** > **확장 및 업데이트** 컨트롤 확장에 대 한 확인 하 고 클릭 **제거**합니다.

3. 업로드 합니다 *.vsix* 네트워크 또는 웹 사이트에 파일입니다.

    파일을 업로드 하는 경우는 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트를 다른 사용자가 사용할 수 있습니다 **도구** > **확장 및 업데이트** 찾으려면 Visual Studio에는 온라인 제어 하 고 설치 합니다.
