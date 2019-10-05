---
title: 하위 메뉴에 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32a69a260aff2163deb02a67fb011d50f138c601
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309874"
---
# <a name="add-a-submenu-to-a-menu"></a>메뉴에 하위 메뉴를 추가 합니다.
이 연습에서 데모 기반 [Visual Studio 메뉴 모음에 메뉴를 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 하위 메뉴를 추가 하는 방법을 표시 하 여 합니다 **TestMenu** 메뉴.

 하위 메뉴에는 다른 메뉴에 표시 되는 보조 메뉴입니다. 하위 메뉴 이름 뒤에 오는 화살표로 식별할 수 있습니다. 하위 메뉴 및 명령을 표시할 수 하면 이름을 클릭 합니다.

 이 연습에서는 Visual Studio 메뉴 모음에서 메뉴에 하위 메뉴를 만들고 하위 메뉴에 새 명령을 배치 합니다. 이 연습에서는 새 명령을 구현합니다.

## <a name="prerequisites"></a>전제 조건
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="add-a-submenu-to-a-menu"></a>메뉴에 하위 메뉴를 추가 합니다.

1. 단계를 따릅니다 [Visual Studio 메뉴 모음에 메뉴 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 프로젝트 및 메뉴 항목을 만듭니다. 이 연습의 단계 VSIX 프로젝트 이름은 가정 `TopLevelMenu`합니다.

2. 오픈 *TestCommandPackage.vsct*합니다. 에 `<Symbols>` 섹션에서 추가 `<IDSymbol>` 하위 그룹 및의 모든 명령에 대 한 하위 메뉴에 대 한 요소는 `<GuidSymbol>` "guidTopLevelMenuCmdSet." 라는 노드 이 포함 하는 동일한 노드에 `<IDSymbol>` 최상위 메뉴에 대 한 요소입니다.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. 새로 만든된 하위 메뉴를 추가 합니다 `<Menus>` 섹션입니다.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     부모의 GUID/ID 쌍에서 생성 된 메뉴 그룹을 지정 합니다. [Visual Studio 메뉴 모음에 메뉴 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), 및이 최상위 메뉴의 자식입니다.

4. 2 단계에서 정의 된 메뉴 그룹 추가 `<Groups>` 섹션 및 하위 메뉴의 자식으로 만듭니다.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. 새 `<Button>` 요소는 `<Buttons>` 하위 메뉴 항목으로 2 단계에서 만든 명령을 정의 하는 섹션입니다.

    ```xml
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <Strings>
           <CommandName>cmdidTestSubCommand</CommandName>
           <ButtonText>Test Sub Command</ButtonText>
        </Strings>
    </Button>
    ```

6. 솔루션을 빌드하고 디버깅을 시작합니다. 실험적 인스턴스를 확인 해야 합니다.

7. 클릭 **TestMenu** 라는 새 하위 메뉴를 보려면 **하위 메뉴**합니다. 클릭 **하위 메뉴** 하위 메뉴를 열고 새 명령 참조 **테스트 하위 명령**입니다. 클릭 하면 **하위 명령** 아무 작업도 수행 합니다.

## <a name="add-a-command"></a>명령 추가

1. 오픈 *TestCommand.cs* 기존 명령 id입니다. 후 다음 명령 ID를 추가 하 고

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. 하위 명령을 추가 합니다. 명령 생성자를 찾습니다. 에 대 한 호출 바로 뒤에 다음 줄을 추가 합니다 `AddCommand` 메서드.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    `SubItemCallback` 명령 처리기는 나중에 정의 됩니다. 생성자는 이제 다음과 같이 표시 됩니다.

    ```csharp
    private TestCommand(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            var menuCommandID = new CommandID(CommandSet, CommandId);
            var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);
            commandService.AddCommand(menuItem);

            CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. `SubItemCallback()`를 추가합니다. 이 방법은 하위 메뉴에 새 명령을 클릭할 때 호출 됩니다.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetServiceAsync(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        uiShell.ShowMessageBox(
            0,
            ref clsid,
            "TestCommand",
            string.Format(CultureInfo.CurrentCulture,
            "Inside TestCommand.SubItemCallback()",
            this.ToString()),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result);
    }
    ```

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스에서 표시 됩니다.

5. 에 **TestMenu** 메뉴에서 클릭 **하위 메뉴** 을 클릭 한 다음 **테스트 하위 명령**합니다. 메시지 상자를 표시 하 고 "테스트 명령 내에서 TestCommand.SubItemCallback()" 텍스트를 표시 해야 합니다.

## <a name="see-also"></a>참고자료

- [Visual Studio 메뉴 모음에 메뉴 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
