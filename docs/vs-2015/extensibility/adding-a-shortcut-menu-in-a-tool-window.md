---
title: 도구 창의 바로 가기 메뉴를 추가 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
caps.latest.revision: 38
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 60ac63be54c235187e66a85c541f925e1e34cafd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689860"
---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>도구 창의 바로 가기 메뉴 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 도구 창의 바로 가기 메뉴를 배치합니다. 바로 가기 메뉴에 단추, 텍스트 상자 또는 창 배경 단추로 클릭할 때 표시 되는 메뉴가입니다. 바로 가기 메뉴에서 명령을 다른 메뉴 또는 도구 모음에서 명령과 동일 하 게 동작 합니다. 바로 가기 메뉴를 지원 하려면.vsct 파일에서 지정 하 고 마우스 오른쪽 단추 클릭에 대 한 응답에 표시 합니다.  
  
 사용자 지정 도구 창 클래스에서 상속 되는 WPF 사용자 컨트롤의 도구 창으로 구성 됩니다 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>합니다.  
  
 이 연습에.vsct 파일에서 메뉴 항목을 선언 하 고 다음 관리 되는 패키지 프레임 워크를 사용 하 여 도구 창을 정의 하는 클래스에 구현 하 여 Visual Studio 메뉴와 바로 가기 메뉴를 만드는 방법을 보여 줍니다. 이 방법은 Visual Studio 명령, UI 요소 및 자동화 개체 모델에 대 한 액세스를 지원합니다.  
  
 또는 바로 가기 메뉴는 Visual Studio 기능에 액세스 하지 하는 경우 사용할 수는 <xref:System.Windows.FrameworkElement.ContextMenu%2A> 사용자 정의 컨트롤에 있는 XAML 요소의 속성입니다. 자세한 내용은 [ContextMenu](https://msdn.microsoft.com/library/2f40b2bb-b702-4706-9fc4-10bcfd7cc35d)합니다.  
  
## <a name="prerequisites"></a>전제 조건  
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>도구 창 바로 가기 메뉴 패키지 만들기  
  
1. 라는 VSIX 프로젝트를 만듭니다 `TWShortcutMenu` 라는 도구 창 서식 파일을 추가한 **ShortCutMenu** 되도록 합니다. 도구 창을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [도구 창으로 확장을 만드는](../extensibility/creating-an-extension-with-a-tool-window.md)합니다.  
  
## <a name="specifying-the-shortcut-menu"></a>바로 가기 메뉴를 지정합니다.  
 이 연습에 나와 있는 사용자 수와 같은 바로 가기 메뉴에서 도구 창의 배경을 채우는 데 사용 되는 색 목록을 선택 합니다.  
  
1. ShortcutMenuPackage.vsct, guidShortcutMenuPackageCmdSet, GuidSymbol 요소에서 찾아 바로 가기 메뉴, 바로 가기 메뉴 그룹 및 메뉴 옵션을 선언 합니다. GuidSymbol 요소 이제 다음과 같이 표시 됩니다.  
  
    ```xml  
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here  
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />  
        <IDSymbol name="ColorMenu" value="0x1000"/>  
        <IDSymbol name="ColorGroup" value="0x1100"/>  
        <IDSymbol name="cmdidRed" value="0x102"/>  
        <IDSymbol name="cmdidYellow" value="0x103"/>  
        <IDSymbol name="cmdidBlue" value="0x104"/>  
    </GuidSymbol>  
    ```  
  
2. Buttons 요소 직전 메뉴 요소를 만들고에 바로 가기 메뉴를 정의 합니다.  
  
    ```vb  
    <Menus>  
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">  
        <Strings>  
          <ButtonText>Color change</ButtonText>  
          <CommandName>ColorChange</CommandName>  
        </Strings>  
      </Menu>  
    </Menus>  
    ```  
  
     바로 가기 메뉴는 메뉴 또는 도구 모음의 일부 이기 때문에 부모가 없는지 않습니다.  
  
3. 바로 가기 메뉴 항목을 포함 하는 그룹 요소를 사용 하 여 그룹 요소를 만들고 바로 가기 메뉴를 사용 하 여 그룹을 연결 합니다.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4. 단추 요소에서 바로 가기 메뉴에서 표시 되는 개별 명령을 정의 합니다. Buttons 요소는 다음과 같습니다.  
  
    ```xml  
    <Buttons>  
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">  
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
            <Icon guid="guidImages" id="bmpPic1" />  
            <Strings>  
                <ButtonText>ShortcutMenu</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Red</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Yellow</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Blue</ButtonText>  
            </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
5. ShortcutMenuPackageGuids.cs, GUID, 바로 가기 메뉴 및 메뉴 항목을 설정 하는 명령에 대 한 정의 추가 합니다.  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     이들은 ShortcutMenuPackage.vsct 파일의 Symbols 섹션에 정의 된 동일한 명령 Id입니다. 상황에 맞는 그룹 포함 되지 않습니다 여기서는.vsct 파일에만 필요 하므로.  
  
## <a name="implementing-the-shortcut-menu"></a>바로 가기 메뉴를 구현합니다.  
 이 섹션에서는 바로 가기 메뉴 및 명령을 구현합니다.  
  
1. ShortcutMenu.cs, 도구 창 메뉴 명령 서비스를 가져올 수 있지만 포함 된 컨트롤 수 없습니다. 다음 단계에는 사용자 컨트롤에서 사용 가능한 메뉴 명령 서비스를 만드는 방법을 보여 줍니다.  
  
2. ShortcutMenu.cs, 추가 다음 문을 사용 하 여:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3. 메뉴 명령 서비스 메뉴 명령 서비스는 생성자에 전달 하는 컨트롤을 추가 하는 도구 창의 initialize () 메서드를 재정의 합니다.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4. ShortcutMenu 도구 창의 생성자에서 컨트롤을 추가 하는 줄을 제거 합니다. 생성자는 이제 다음과 같이 표시 됩니다.  
  
    ```csharp  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5. ShortcutMenuControl.xaml.cs, 메뉴 명령 서비스에 대 한 private 필드를 추가 하 고 메뉴 명령 서비스 되려면 컨트롤 생성자를 변경 합니다. 다음 메뉴 명령 서비스를 사용 하 여 상황에 맞는 메뉴 명령을 추가 합니다. ShortcutMenuControl 생성자는 이제 다음 코드 처럼 보여야 합니다. 명령 처리기는 나중에 정의 됩니다.  
  
    ```csharp  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuPackageGuids.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuPackageGuids.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuPackageGuids.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6. ShortcutMenuControl.xaml, 추가 <xref:System.Windows.UIElement.MouseRightButtonDown> 최상위 이벤트 <xref:System.Windows.Controls.UserControl> 요소입니다. 이제 XAML 파일을 다음과 같이 표시 됩니다.  
  
    ```vb  
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            Background="{DynamicResource VsBrush.Window}"  
            Foreground="{DynamicResource VsBrush.WindowText}"  
            mc:Ignorable="d"  
            d:DesignHeight="300" d:DesignWidth="300"  
            Name="MyToolWindow"  
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">  
        <Grid>  
            <StackPanel Orientation="Vertical">  
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>  
            </StackPanel>  
        </Grid>  
    </UserControl>  
    ```  
  
7. 이벤트 처리기에 대 한 스텁을 ShortcutMenuControl.xaml.cs를 추가 합니다.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8. 다음 추가 문을 사용 하 여 동일한 파일에:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. 구현 된 `MyToolWindowMouseRightButtonDown` 다음과 같은 이벤트입니다.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
        if (null != commandService)  
        {  
            CommandID menuID = new CommandID(  
                new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuPackageGuids.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     이렇게를 <xref:System.ComponentModel.Design.CommandID> 바로 가기 메뉴에 대 한 개체의 마우스 클릭의 위치를 식별 하 고 사용 하 여 해당 위치에 바로 가기 메뉴를 열고는 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> 메서드.  
  
10. 명령 처리기를 구현 합니다.  
  
    ```csharp  
    private void ChangeColor(object sender, EventArgs e)  
    {  
        var mc = sender as MenuCommand;  
  
        switch (mc.CommandID.ID)  
        {  
            case ShortcutMenuPackageGuids.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuPackageGuids.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuPackageGuids.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     단 하나의 메서드를 식별 하 여 모든 메뉴 항목에 대 한 이벤트를 처리 하는 경우는 <xref:System.ComponentModel.Design.CommandID> 및 배경색을 적절 하 게 설정 합니다. 메뉴 항목을 했습니다 관련 되지 않은 명령을 포함 하는 경우 각 명령에 대 한 별도 이벤트 처리기를 만들었습니다 됩니다.  
  
## <a name="testing-the-tool-window-features"></a>테스트 도구 창의 기능  
  
1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 됩니다.  
  
2. 실험적 인스턴스를 클릭 **보기 / 기타 Windows**를 클릭 하 고 **ShortcutMenu**합니다. 이렇게 하면 도구 창을 표시 됩니다.  
  
3. 도구 창의 본문을 마우스 오른쪽 단추로 클릭 합니다. 색 목록이 있는 바로 가기 메뉴가 표시 됩니다.  
  
4. 바로 가기 메뉴의 색을 클릭 합니다. 도구 창 배경 색상은 선택한 색으로 변경 되어야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)   
 [서비스 사용 및 제공](../extensibility/using-and-providing-services.md)
