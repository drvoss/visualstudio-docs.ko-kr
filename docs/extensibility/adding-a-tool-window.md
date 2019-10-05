---
title: 도구 창 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f438297a51e5b091ea8b80cf587586919d00798
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352419"
---
# <a name="add-a-tool-window"></a>도구 창 추가
이 연습에서 도구 창을 만들고 다음과 같은 방법으로 Visual Studio에 통합 하는 방법을 배웁니다.

- 도구 창으로 컨트롤을 추가 합니다.

- 도구 창에 도구 모음을 추가 합니다.

- 도구 모음에는 명령을 추가 합니다.

- 명령을 구현 합니다.

- 도구 창에 대 한 기본 위치를 설정 합니다.

## <a name="prerequisites"></a>전제 조건
Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="create-a-tool-window"></a>도구 창을 만들려면

1. 라는 프로젝트를 만듭니다 **FirstToolWin** 라는 사용자 지정 도구 창 항목 템플릿을 VSIX 템플릿을 사용 하 여 추가한 **FirstToolWindow**합니다.

    > [!NOTE]
    > 도구 창을 사용 하 여 확장을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [도구 창으로 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-a-tool-window.md)합니다.

## <a name="add-a-control-to-the-tool-window"></a>도구 창에 컨트롤 추가

1. 기본 컨트롤을 제거 합니다. 오픈 *FirstToolWindowControl.xaml* 삭제 된 **Click Me!** 클릭합니다.

2. 에 **도구 상자**, 확장를 **모든 WPF 컨트롤** 끌어서 섹션를 **미디어 요소** 컨트롤을 **FirstToolWindowControl** 폼입니다. 컨트롤을 선택 및 합니다 **속성** 창에서이 요소의 이름을 **mediaElement1**합니다.

## <a name="add-a-toolbar-to-the-tool-window"></a>도구 창 도구 모음을 추가 합니다.
다음과 같은 방식으로 도구 모음을 더하여 해당 그라데이션 및 색이 IDE의 나머지 부분과 일치 하는지 보장할 수 있습니다.

1. **솔루션 탐색기**오픈 *FirstToolWindowPackage.vsct*합니다. 합니다 *.vsct* 파일은 XML을 사용 하 여 도구 창에 그래픽 사용자 인터페이스 (GUI) 요소를 정의 합니다.

2. 에 `<Symbols>` 섹션을 찾습니다 합니다 `<GuidSymbol>` 노드입니다 `name` 특성은 `guidFirstToolWindowPackageCmdSet`합니다. 다음 두 개의 추가 `<IDSymbol>` 목록에 요소 `<IDSymbol>` 이 노드에 도구 모음 및 도구 모음 그룹을 정의 하는 요소입니다.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. 바로 위에 합니다 `<Buttons>` 섹션을 만듭니다는 `<Menus>` 이 유사한 섹션:

    ```xml
    <Menus>
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
            <Strings>
                <ButtonText>Tool Window Toolbar</ButtonText>
                <CommandName>Tool Window Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

    메뉴에는 여러 가지가입니다. 이 메뉴는 도구 창에서 도구 모음에서 정의 된 해당 `type` 특성입니다. 합니다 `guid` 및 `id` 설정 도구 모음의 정규화 된 ID를 확인 합니다. 일반적으로 `<Parent>` 메뉴의 포함 된 그룹입니다. 그러나 도구 모음 자체 부모로 정의 됩니다. 동일한 식별자가 사용 되므로 합니다 `<Menu>` 고 `<Parent>` 요소입니다. `priority` 특성은 바로 ' 0'입니다.

4. 도구 모음에는 여러 가지 방법으로 메뉴와 유사합니다. 예를 들어 메뉴 명령 그룹이 될 수 있습니다, 처럼 도구 모음 그룹이 있을 수도 있습니다. (메뉴, 명령 그룹으로 구분 됩니다 가로 줄. 도구 모음, 그룹 구분 되지 않은 visual 구분선.)

    추가 된 `<Groups>` 포함 하는 섹션을 `<Group>` 요소입니다. 그룹에 선언 된 ID를 정의 하는이 `<Symbols>` 섹션입니다. 추가 된 `<Groups>` 직후 섹션는 `<Menus>` 섹션입니다.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    을 설정 하면 부모 GUID 및 ID GUID 및 ID 도구 모음의 도구 모음에 그룹을 추가 합니다.

## <a name="add-a-command-to-the-toolbar"></a>도구 모음에 명령 추가
 도구 모음 단추로 표시 되는 명령을 추가 합니다.

1. 에 `<Symbols>` 섹션 그룹 선언 바로 뒤에 도구 모음 및 도구 모음 다음 IDSymbol 요소를 선언 합니다.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. 단추 요소 안에 추가 `<Buttons>` 섹션입니다. 이 요소와 도구 창의 도구 모음에 표시 됩니다는 **검색** 아이콘 (돋보기) 합니다.

    ```xml
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>
        <Icon guid="guidImages" id="bmpPicSearch" />
        <Strings>
            <CommandName>cmdidWindowsMediaOpen</CommandName>
            <ButtonText>Load File</ButtonText>
        </Strings>
    </Button>
    ```

3. 오픈 *FirstToolWindowCommand.cs* 를 기존 필드 직후 클래스에 다음 줄을 추가 합니다.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    이렇게 하면 명령의 코드에서 사용할 수 있습니다.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>FirstToolWindowControl MediaPlayer 속성 추가
도구 모음 컨트롤에 대 한 이벤트 처리기에서 코드 FirstToolWindowControl 클래스의 자식인 Media Player 컨트롤에 액세스할 수 있어야 합니다.

**솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 *FirstToolWindowControl.xaml*, 클릭 **코드 보기**, FirstToolWindowControl 클래스에 다음 코드를 추가 합니다.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>도구 창 및 도구 모음 인스턴스화
도구 모음 및 메뉴 명령을 호출 하는 추가 합니다 **열려 있는 파일** 대화 하 고 선택한 미디어 파일을 재생 합니다.

1. 오픈 *FirstToolWindow.cs* 추가한 다음 `using` 문입니다.

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. FirstToolWindow 클래스 내 FirstToolWindowControl 컨트롤에 대 한 공용 참조를 추가 합니다.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. 생성자의 끝에서 새로 만든 컨트롤에이 컨트롤 변수를 설정 합니다.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. 생성자 내에서 도구 모음을 인스턴스화하십시오.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. 이 시점에서 FirstToolWindow 생성자는 다음과 같이 표시 됩니다.

    ```csharp
    public FirstToolWindow() : base(null)
    {
        this.Caption = "FirstToolWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
        control = new FirstToolWindowControl();
        base.Content = control;
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.ToolbarID);
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    }
    ```

6. 도구 모음에 메뉴 명령을 추가 합니다. FirstToolWindowCommand.cs 클래스에 추가 된 다음 문을 사용 하 여

    ```csharp
    using System.Windows.Forms;
    ```

7. FirstToolWindowCommand 클래스에서 ShowToolWindow() 메서드의 끝에 다음 코드를 추가 합니다. ButtonHandler 명령은 다음 섹션에서 구현 됩니다.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>도구 창에서 메뉴 명령을 구현 하려면

1. FirstToolWindowCommand 클래스에서 호출 하는 ButtonHandler 메서드를 추가 합니다 **열려 있는 파일** 대화 합니다. 파일을 선택 하면 미디어 파일을 재생 됩니다.

2. FirstToolWindowCommand 클래스에서 FindToolWindow() 메서드에서 생성 되는 FirstToolWindow 창에 대 한 개인 참조를 추가 합니다.

    ```csharp
    private FirstToolWindow window;
    ```

3. (있도록 ButtonHandler 명령 처리기는 창 컨트롤에는 액세스할 수 있습니다 위에 정의 된 기간을 설정 하려면 ShowToolWindow() 메서드 변경. 전체 ShowToolWindow() 메서드는 다음과 같습니다.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create tool window");
        }

        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.cmdidWindowsMediaOpen);
        var menuItem = new MenuCommand(new EventHandler(
            ButtonHandler), toolbarbtnCmdID);
        mcs.AddCommand(menuItem);
    }
    ```

4. ButtonHandler 메서드를 추가 합니다. 사용자를 재생 하려면 미디어 파일을 지정 하는 OpenFileDialog를 만들면 다음 선택한 파일을 재생 하 고 있습니다.

    ```csharp
    private void ButtonHandler(object sender, EventArgs arguments)
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();
        DialogResult result = openFileDialog.ShowDialog();
        if (result == DialogResult.OK)
        {
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);
        }
    }
    ```

## <a name="set-the-default-position-for-the-tool-window"></a>도구 창에 대 한 기본 위치를 설정 합니다.
 다음으로, 도구 창에 대 한 IDE에서 기본 위치를 지정 합니다. 도구 창에 대 한 구성 정보를 *FirstToolWindowPackage.cs* 파일입니다.

1. *FirstToolWindowPackage.cs*, 찾을 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 특성을 `FirstToolWindowPackage` FirstToolWindow 형식을 생성자에 전달 하는 클래스입니다. 기본 위치를 지정 하려면 다음 예제에서는 생성자에 매개 변수를 더 추가 해야 합니다.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    첫 번째 명명 된 매개 변수인 `Style` 및 해당 값이 `Tabbed`, 즉, 창 기존 창에 탭이 되도록 합니다. 가 여 도킹 위치를 지정 합니다 `Window` 매개 변수, 여기서 n의 GUID **솔루션 탐색기**합니다.

    > [!NOTE]
    > IDE에서 windows의 유형에 대 한 자세한 내용은 참조 하세요. <xref:EnvDTE.vsWindowType>합니다.

## <a name="test-the-tool-window"></a>테스트 도구 창

1. 키를 눌러 **F5** 를 Visual Studio 실험적 빌드의 새 인스턴스를 엽니다.

2. 에 **뷰** 메뉴에서 **기타 Windows** 클릭 하 고 **첫 번째 도구 창을**합니다.

    와 동일한 위치에서 미디어 플레이어 도구 창을 열어야 **솔루션 탐색기**합니다. 이전과 동일한 위치에 표시 됩니다, 경우에 창 레이아웃 다시 설정 (**창 / 창 레이아웃 다시 설정**).

3. 단추를 클릭 (에 **검색** 아이콘) 도구 창에서. 예를 들어, 지원 되는 사운드 또는 비디오 파일 선택 *C:\windows\media\chimes.wav*, 누릅니다 **오픈**합니다.

    종소리 소리가 들립니다.

## <a name="see-also"></a>참고자료
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
