---
title: 도구 모음 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de74961715a82dde4e184509094d05145ad0f79c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184864"
---
# <a name="adding-a-toolbar"></a>도구 모음 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 Visual Studio IDE에 도구 모음을 추가 하는 방법을 보여 줍니다.  
  
 도구 모음 명령에 바인딩된 단추를 포함 하는 가로 또는 세로 줄무늬 됩니다. 해당 구현에 따라 IDE에서 도구 모음 위치가 변경 되 면, 주요 IDE 창의 한쪽에 도킹 하거나 수 다른 창 앞에 유지 하려고 합니다.  
  
 또한 수 도구 모음에 명령 추가 사용자나에서 사용 하 여 제거 합니다 **사용자 지정** 대화 상자. 일반적으로 Vspackage에서 도구 모음은 사용자를 사용자 지정할 수 있습니다. 모든 사용자 지정을 처리 하는 IDE 및 VSPackage 명령에 응답 합니다. VSPackage는 명령은 실제로 위치를 알 필요가 없습니다.  
  
 메뉴에 대 한 자세한 내용은 참조 하세요. [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)합니다.  
  
## <a name="prerequisites"></a>필수 구성 요소  
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
## <a name="creating-an-extension-with-a-toolbar"></a>도구 모음을 사용 하 여 확장 만들기  
 라는 VSIX 프로젝트를 만듭니다 `IDEToolbar`합니다. 명명 된 메뉴 명령 항목 템플릿을 추가 **ToolbarTestCommand**합니다. 이 작업을 수행 하는 방법에 대 한 정보를 참조 하세요 [메뉴 명령을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-a-menu-command.md)합니다.  
  
## <a name="creating-a-toolbar-for-the-ide"></a>IDE에 대 한 도구 모음 만들기  
  
1. ToolbarTestCommandPackage.vsct, Symbols 섹션을 찾습니다. GuidToolbarTestCommandPackageCmdSet 라는 GuidSymbol 요소에서 도구 모음 및 도구 모음 그룹에 대 한 선언을 다음과 같이 추가 합니다.  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2. 명령 섹션의 맨 위에 있는 메뉴 섹션을 만듭니다. 도구 모음을 정의 하려면 메뉴 섹션 메뉴 요소를 추가 합니다.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"  
            type="Toolbar" >  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
          </Menu>  
    </Menus>  
    ```  
  
     하위 메뉴와 같은 도구 모음을 중첩할 수 없습니다. 부모 그룹에 할당할 필요가 없습니다. 또한 필요가 없습니다 우선 순위를 설정 하려면 도구 모음을 이동할 수 있으므로 합니다. 일반적으로 도구 모음의 초기 배치 프로그래밍 방식으로 정의 되었지만 사용자가 후속 변경 내용은 유지 됩니다.  
  
3. 에 [그룹](../extensibility/groups-element.md) 섹션을 기존 그룹 항목을 한 후 정의 [그룹](../extensibility/group-element.md) 도구 모음에 대 한 명령을 포함 하는 요소입니다.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4. 도구 모음에서 표시 단추를 확인 합니다. 단추 섹션에서는 도구 모음 단추에 부모 블록을 대체 합니다. 결과 단추 블록은 다음과 같이 표시 됩니다.  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     기본적으로 도구 모음에 없는 명령이 나타나지 않습니다.  
  
5. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스에서 표시 됩니다.  
  
6. 도구 모음 목록을 가져오려면 Visual Studio 메뉴 모음을 마우스 오른쪽 단추로 클릭 합니다. 선택 **테스트 도구 모음**합니다.  
  
7. 이제 도구 모음에서 찾기 파일 아이콘의 오른쪽에 아이콘으로 표시 됩니다. 했다는 메시지 상자가 표시 아이콘을 클릭 하면 **ToolbarTestCommandPackage 합니다. IDEToolbar.ToolbarTestCommand.MenuItemCallback() 내**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
