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
ms.openlocfilehash: 99a21a4dd4c39a4cefdf6be30171c503fc2ce005
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187115"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>솔루션 탐색기 도구 모음에 명령 추가
이 연습에서는 **솔루션 탐색기** 도구 모음에 단추를 추가 하는 방법을 보여 줍니다.

 도구 모음 또는 메뉴의 모든 명령을 Visual Studio에서 단추 라고 합니다. 단추를 클릭 하면 명령 처리기의 코드가 실행 됩니다. 일반적으로 관련 명령은 그룹 하나를 구성 하기 위해 함께 그룹화 됩니다. 메뉴 또는 도구 모음은 그룹의 컨테이너 역할을 합니다. 우선 순위 그룹의 개별 명령이 메뉴 또는 도구 모음에 표시 되는 순서를 결정 합니다. 표시 유형을 제어 하 여 단추가 도구 모음 또는 메뉴에 표시 되는 것을 방지할 수 있습니다. *. Vsct* 파일의 `<VisibilityConstraints>` 섹션에 나열 된 명령은 연결 된 컨텍스트에서만 표시 됩니다. 표시 유형을 그룹에 적용할 수 없습니다.

 메뉴, 도구 모음 명령 및. r e r *v* e r 파일에 대 한 자세한 내용은 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)을 참조 하세요.

> [!NOTE]
> 명령 테이블 구성 ( *.ctc*) 파일 대신 XML 명령 테이블 ( *.cvsct*) 파일을 사용 하 여 메뉴와 명령이 vspackage에 표시 되는 방식을 정의 합니다. 자세한 내용은 [Visual Studio 명령 테이블 (를 참조 하세요. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Prerequisites
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-an-extension-with-a-menu-command"></a>메뉴 명령을 사용 하 여 확장 만들기
 `SolutionToolbar`라는 VSIX 프로젝트를 만듭니다. **ToolbarButton**라는 메뉴 명령 항목 템플릿을 추가 합니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>솔루션 탐색기 도구 모음에 단추 추가
 연습의이 섹션에서는 **솔루션 탐색기** 도구 모음에 단추를 추가 하는 방법을 보여 줍니다. 단추를 클릭 하면 콜백 메서드의 코드가 실행 됩니다.

1. 이 경우 *에는 `<Symbols>`* 섹션으로 이동 합니다. `<GuidSymbol>` 노드에는 패키지 템플릿에 의해 생성 된 메뉴 그룹 및 명령이 포함 되어 있습니다. 이 노드에 `<IDSymbol>` 요소를 추가 하 여 명령을 저장 하는 그룹을 선언 합니다.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. `<Groups>` 섹션에서 기존 그룹 항목 뒤에 이전 단계에서 선언한 새 그룹을 정의 합니다.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     부모 GUID: ID 쌍을 `guidSHLMainMenu`로 설정 하 고 `IDM_VS_TOOL_PROJWIN`을 **솔루션 탐색기** 도구 모음에 배치 하 고 높은 우선 순위 값을 설정 하면 해당 그룹이 다른 명령 그룹 뒤에 배치 됩니다.

3. `<Buttons>` 섹션에서 생성 된 `<Button>` 항목의 부모 ID를 변경 하 여 이전 단계에서 정의한 그룹을 반영 합니다. 수정 된 `<Button>` 요소는 다음과 같습니다.

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 나타납니다.

     **솔루션 탐색기** 도구 모음에서 기존 단추 오른쪽에 있는 새 명령 단추를 표시 합니다. 단추 아이콘은 취소선입니다.

5. 새로 만들기 단추를 클릭 합니다.

     **ToolbarButton. MenuItemCallback ()** 가 표시 되어야 하는 메시지 도구 모음 buttonpackage가 있는 대화 상자가 표시 됩니다.

## <a name="control-the-visibility-of-a-button"></a>단추의 표시 여부를 제어 합니다.
 이 연습 단원에서는 도구 모음에서 단추의 표시 여부를 제어 하는 방법을 보여 줍니다. *솔루션 도구 모음의* `<VisibilityConstraints>` 섹션에서 하나 이상의 프로젝트에 대 한 컨텍스트를 설정 하 여 프로젝트 또는 프로젝트가 열려 있는 경우에만 표시 되도록 단추를 제한 합니다.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>하나 이상의 프로젝트를 열 때 단추를 표시 하려면

1. 여러 개의 명령 설명 섹션의 `<Buttons>` 섹션에서 `<Strings>` 및 `<Icons>` 태그 사이에 기존 `<Button>` 요소에 두 개의 명령 플래그를 추가 *합니다.*

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    `<VisibilityConstraints>` 섹션의 항목이 적용 될 수 있도록 `DefaultInvisible` 및 `DynamicVisibility` 플래그를 설정 해야 합니다.

2. 두 개의 `<VisibilityItem>` 항목이 있는 `<VisibilityConstraints>` 섹션을 만듭니다. 닫는 `</Commands>` 태그 바로 뒤에 새 섹션을 배치 합니다.

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

    각 표시 유형 항목은 지정 된 단추가 표시 되는 조건을 나타냅니다. 여러 조건을 적용 하려면 동일한 단추에 대해 여러 항목을 만들어야 합니다.

3. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 나타납니다.

    **솔루션 탐색기** 도구 모음에 취소선 단추가 포함 되어 있지 않습니다.

4. 프로젝트를 포함 하는 솔루션을 엽니다.

    취소선 단추가 기존 단추의 오른쪽에 있는 도구 모음에 나타납니다.

5. **파일** 메뉴에서 **솔루션 닫기**를 클릭 합니다. 단추가 도구 모음에서 사라집니다.

   단추의 표시 유형은 VSPackage이 로드 될 때까지 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에 의해 제어 됩니다. VSPackage를 로드 한 후에는 VSPackage에서 단추의 표시 유형을 제어 합니다.  자세한 내용은 [Menucommands 및 OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)를 참조 하세요.

## <a name="see-also"></a>참조
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)