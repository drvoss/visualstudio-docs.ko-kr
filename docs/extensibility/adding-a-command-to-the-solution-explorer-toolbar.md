---
title: 솔루션 탐색기 도구 모음에 명령 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cb5c0a8aac049b7d5ff0e79843724b87e4999e4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313536"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>솔루션 탐색기 도구 모음에 명령 추가
이 연습에서는 단추를 추가 하는 방법을 보여 줍니다.는 **솔루션 탐색기** 도구 모음입니다.

 Visual Studio 도구 모음 또는 메뉴에 있는 모든 명령은 단추를 호출 됩니다. 단추를 클릭할 때 명령 처리기의 코드가 실행 됩니다. 일반적으로 한 그룹을 형성 하려면 관련된 명령은 함께 그룹화 됩니다. 메뉴 또는 도구 모음에는 그룹에 대 한 컨테이너로 작동합니다. 우선 순위 그룹의 개별 명령을 표시 메뉴 또는 도구 모음 순서를 결정 합니다. 표시 유형을 제어 하 여 도구 모음 또는 메뉴에 표시 되는 단추를 방지할 수 있습니다. 에 나열 된 명령을 `<VisibilityConstraints>` 의 섹션을 *.vsct* 파일 컨텍스트 연결된에 표시 됩니다. 표시 여부는 그룹에 적용할 수 없습니다.

 메뉴, 도구 모음 명령에 대 한 자세한 내용은 및 *.vsct* 파일을 참조 하십시오 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)합니다.

> [!NOTE]
> XML 명령 테이블을 사용 하 여 ( *.vsct*) 대신 명령 테이블 구성 파일 ( *.ctc*)에 Vspackage의 메뉴 및 명령을 표시 하는 방법을 정의 하는 파일입니다. 자세한 내용은 참조 하세요. [Visual Studio 명령 테이블 (합니다. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)합니다.

## <a name="prerequisites"></a>전제 조건
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="create-an-extension-with-a-menu-command"></a>메뉴 명령을 사용 하 여 확장 만들기
 라는 VSIX 프로젝트를 만듭니다 `SolutionToolbar`합니다. 명명 된 메뉴 명령 항목 템플릿을 추가 **ToolbarButton**합니다. 이 작업을 수행 하는 방법에 대 한 정보를 참조 하세요 [메뉴 명령을 사용 하 여 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-a-menu-command.md)합니다.

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>솔루션 탐색기 도구 모음 단추 추가
 연습의이 섹션에는 단추를 추가 하는 방법을 보여 줍니다 합니다 **솔루션 탐색기** 도구 모음입니다. 단추를 클릭 하면 콜백 메서드에서 코드에에서 실행 됩니다.

1. 에 *ToolbarButtonPackage.vsct* 파일을 이동 합니다 `<Symbols>` 섹션입니다. `<GuidSymbol>` 메뉴 그룹 및 명령이 패키지 템플릿에 의해 생성 된 노드를 포함 합니다. 추가 `<IDSymbol>` 이 노드에 명령을 포함 하는 그룹을 선언 하는 요소입니다.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. 에 `<Groups>` 섹션에서는 기존 그룹 항목을 한 후 새 그룹 정의 선언 된 이전 단계에서 합니다.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     부모 guid: id 쌍 설정 `guidSHLMainMenu` 및 `IDM_VS_TOOL_PROJWIN` 이 그룹에 배치 합니다 **솔루션 탐색기** 도구 모음 및 우선 순위가 높은 값을 설정 후 다른 명령 그룹 배치 합니다.

3. 에 `<Buttons>` 섹션에서 생성 된 부모 ID를 변경 `<Button>` 항목 이전 단계에서 정의한 그룹을 반영 하도록 합니다. 수정 된 `<Button>` 요소는 다음과 같습니다.

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 됩니다.

     합니다 **솔루션 탐색기** 기존 단추의 오른쪽 도구 모음 새 명령 단추를 표시 합니다. 단추 아이콘은 취소선.

5. 새로 만들기 단추를 클릭 합니다.

     메시지가 있는 대화 상자가 **ToolbarButtonPackage 내 SolutionToolbar.ToolbarButton.MenuItemCallback()** 표시 합니다.

## <a name="control-the-visibility-of-a-button"></a>단추의 표시 여부를 제어 합니다.
 연습의이 섹션에서는 도구 모음 단추의 표시 여부를 제어 하는 방법을 보여 줍니다. 하나 이상의 프로젝트에는 컨텍스트를 설정 하 여는 `<VisibilityConstraints>` 의 섹션을 *SolutionToolbar.vsct* 가 경우에 프로젝트 또는 프로젝트 열기를 표시 하는 단추를 제한할 파일.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>하나 이상의 프로젝트가 열려 있는 경우 한 단추를 표시 하려면

1. 에 `<Buttons>` 의 섹션 *ToolbarButtonPackage.vsct*, 두 명령 플래그를 추가 하는 기존 `<Button>` 요소 사이의 `<Strings>` 및 `<Icons>` 태그 합니다.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    `DefaultInvisible` 및 `DynamicVisibility` 플래그 설정 해야 하므로 해당 항목에는 `<VisibilityConstraints>` 섹션 영향을 받을 수.

2. 만들기는 `<VisibilityConstraints>` 섹션에는 두 개는 `<VisibilityItem>` 항목입니다. 새 섹션 닫는 바로 뒤 저장 `</Commands>` 태그입니다.

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasSingleProject" />
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasMultipleProjects" />
   </VisibilityConstraints>
   ```

    각 표시 유형 항목에는 지정한 단추 표시 되는 조건을 나타냅니다. 여러 조건에 적용 하려면 같은 단추에 대 한 여러 항목을 만들어야 합니다.

3. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 표시 됩니다.

    합니다 **솔루션 탐색기** 취소선 단추 도구 모음에 없습니다.

4. 프로젝트가 포함 된 모든 솔루션을 엽니다.

    취소선 단추 기존 단추의 오른쪽 도구 모음에 표시 됩니다.

5. **파일** 메뉴에서 **솔루션 닫기**를 클릭합니다. 단추가 도구 모음에서 사라집니다.

   단추의 표시 여부에 의해 제어 됩니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage가 로드 될 때까지 합니다. VSPackage를 로드 한 다음 단추의 표시 여부는 VSPackage에서 제어 됩니다.  자세한 내용은 참조 하세요. [menucommand 합니다. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)합니다.

## <a name="see-also"></a>참고자료
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)