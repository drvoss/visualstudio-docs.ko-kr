---
title: 도구 창에 도구 모음 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 49
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c5df1ce1721c63b5c5cfc3c5b94929da088660f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184874"
---
# <a name="adding-a-toolbar-to-a-tool-window"></a>도구 창에 도구 모음 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에는 도구 창에 도구 모음을 추가 하는 방법을 보여 줍니다.  
  
 도구 모음 명령에 바인딩된 단추를 포함 하는 가로 또는 세로 줄무늬 됩니다. 도구 창의 도구 모음의 길이와 너비 또는 높이 도구 창의 도구 모음 도킹 될 위치에 따라 항상 같습니다.  
  
 IDE에서 도구 모음 달리 도구 창의 도구 모음 도킹 될 및 없습니다 이동 이거나 사용자 지정 합니다. VSPackage는 umanaged 코드로 작성 하는 경우 도구 모음 가장자리에 도킹 될 수 있습니다.  
  
 도구 모음을 추가 하는 방법에 대 한 자세한 내용은 참조 하세요. [도구 모음 추가](../extensibility/adding-a-toolbar.md)합니다.  
  
## <a name="prerequisites"></a>전제 조건  
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>도구 창에 대 한 도구 모음 만들기  
  
1. 라는 VSIX 프로젝트를 만듭니다 `TWToolbar` 모두 라는 메뉴 명령이 있는 **TWTestCommand** 라는 도구 창이 **TestToolWindow**합니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-a-menu-command.md) 하 고 [도구 창으로 확장을 만드는](../extensibility/creating-an-extension-with-a-tool-window.md)합니다. 도구 창 서식 파일을 추가 하기 전에 명령 항목 템플릿을 추가 해야 합니다.  
  
2. TWTestCommandPackage.vsct, Symbols 섹션을 찾습니다. GuidTWTestCommandPackageCmdSet GuidSymbol 노드에서 다음과 같이 도구 모음 및 도구 모음 그룹을 선언 합니다.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3. 맨 위에 있는 합니다 `Commands` 섹션에서 만들기를 `Menus` 섹션입니다. 추가 된 `Menu` 도구 모음을 정의 하는 요소입니다.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     하위 메뉴와 같은 도구 모음을 중첩할 수 없습니다. 부모를 할당할 필요가 없습니다. 또한 필요가 없습니다 우선 순위를 설정 하려면 도구 모음을 이동할 수 있으므로 합니다. 일반적으로 도구 모음의 초기 배치 프로그래밍 방식으로 정의 되었지만 사용자가 후속 변경 내용은 유지 됩니다.  
  
4. 그룹 섹션에서 도구 모음에 대 한 명령을 포함 하는 그룹을 정의 합니다.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5. 단추 섹션에서 도구 모음을 표시할 수 있도록 기존 단추 요소의 부모 도구 모음 그룹을 변경 합니다.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     기본적으로 도구 모음에 없는 명령이 나타나지 않습니다.  
  
     새 도구 모음에서 도구 창으로 자동으로 추가 되지 않기 때문에 도구 모음을 명시적으로 추가 합니다. 이에 대해서는 다음 섹션에서 설명합니다.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>도구 창 도구 모음 추가  
  
1. TWTestCommandPackageGuids.cs에 다음 줄을 추가 합니다.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2. TestToolWindow.cs 추가 다음 문을 사용 하 여 합니다.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3. TestToolWindow 생성자에서 다음 줄을 추가 합니다.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>도구 창의 도구 모음에서 테스트  
  
1. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio 실험적 인스턴스를 표시 됩니다.  
  
2. 에 **보기 / 기타 Windows** 메뉴에서 클릭 **테스트 ToolWindow** 도구 창을 표시 하려면.  
  
     제목 바로 아래 도구 창의 왼쪽 맨 위에 있는 (같이 기본 아이콘) 도구 모음 표시 됩니다.  
  
3. 도구 모음에서 메시지를 표시할 아이콘을 클릭 **TWTestCommandPackage 내 TWToolbar.TWTestCommand.MenuItemCallback()** 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [도구 모음 추가](../extensibility/adding-a-toolbar.md)
