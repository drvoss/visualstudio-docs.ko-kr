---
title: Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1109d6aecf2bc89f72377b282be0182c1e677ed0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311947"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법
VSPackage 예제에서는, 메뉴, 도구 모음에 대 한 사용자 인터페이스 (UI) 요소를 추가 하 고 windows를 이용 하 여 Visual Studio 도구를 *.vsct* 파일입니다.

 UI 요소에 대 한 디자인 지침을 찾을 수 있습니다 [Visual Studio 사용자 환경 지침](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)합니다.

## <a name="the-visual-studio-command-table-architecture"></a>Visual Studio 명령 테이블 아키텍처
 언급 했 듯이 명령 테이블 아키텍처는 앞서 언급 한 아키텍처 원칙을 지원 합니다. 뒤에 추상화, 데이터 구조 및 명령 테이블 구조의 도구 개념은 다음과 같습니다.

- 세 가지 기본적인 종류의 항목: 메뉴, 명령 및 그룹입니다. 메뉴는 메뉴, 하위 메뉴, 도구 모음 또는 도구 창으로 UI에 노출할 수 있습니다. 주석은 사용자가 IDE에서 실행할 수 있습니다 및 메뉴 항목, 단추, 목록 상자 또는 다른 컨트롤에 노출 될 수 있으므로 프로시저를 있습니다. 그룹은 메뉴 및 명령을 둘 다에 대 한 컨테이너입니다.

- 각 항목은 항목을 해당 우선 순위를 다른 항목 및 해당 동작을 수정 하는 플래그를 설명 하는 정의 의해 지정 됩니다.

- 각 항목에는 항목의 부모를 설명 하는 배치 합니다. 항목이 UI의 여러 위치에서 사용 될 수 있도록 여러 부모가 있을 수 있습니다.

     모든 명령 그룹이 있어야 해당 부모와 해당 그룹의 유일한 자식인 경우에 합니다. 모든 표준 메뉴에는 상위 그룹이 있어야 합니다. 도구 모음 및 도구 창 자체 부모로 작동합니다. 그룹은 부모 주 Visual Studio 메뉴 모음에서 메뉴, 도구 모음 또는 도구 창으로 있을 수 있습니다.

### <a name="how-items-are-defined"></a>항목을 정의 하는 방법
 A *.vsct* 파일 형식은 XML입니다. 패키지에 대 한 UI 요소를 정의 하 고 해당 요소는 IDE에서 표시 되는 위치를 결정 합니다. 모든 메뉴, 그룹 또는 명령 패키지에는 처음 할당 된 GUID 및 ID는 `Symbols` 섹션입니다. 나머지 부분을 *.vsct* 파일, 각 메뉴, 명령 및 그룹의 GUID 및 ID 조합으로 식별 됩니다. 다음 예제에서는 일반적인 `Symbols` Visual Studio 패키지 템플릿은 생성 된 섹션 경우는 **메뉴 명령을** 템플릿에서 선택 합니다.

```xml
<Symbols>
  <!-- This is the package guid. -->
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />

  <!-- This is the guid used to group the menu commands together -->
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">

    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
  </GuidSymbol>

  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >
    <IDSymbol name="bmpPic1" value="1" />
    <IDSymbol name="bmpPic2" value="2" />
    <IDSymbol name="bmpPicSearch" value="3" />
    <IDSymbol name="bmpPicX" value="4" />
    <IDSymbol name="bmpPicArrows" value="5" />
  </GuidSymbol>
</Symbols>
```

 최상위 요소는 `Symbols` 섹션은 합니다 [GuidSymbol 요소](../../extensibility/guidsymbol-element.md)합니다. `GuidSymbol` 요소 이름을 IDE에서 패키지 및 해당 구성 요소 파트를 식별 하는 데 사용 되는 Guid에 매핑됩니다.

> [!NOTE]
> Guid는 Visual Studio 패키지 템플릿을 통해 자동으로 생성 됩니다. 클릭 하 여 고유 GUID를 만들 수도 있습니다 **GUID 만들기** 에 **도구** 메뉴.

 첫 번째 `GuidSymbol` 요소인 `guid<PackageName>Pkg`, 패키지 자체의 GUID입니다. Visual Studio에서 패키지를 로드 하는 데 사용 되는 GUID입니다. 일반적으로 되지 않은 자식 요소입니다.

 규칙에 따라 메뉴 및 명령 아래에 그룹화 된 두 번째 `GuidSymbol` 요소인 `guid<PackageName>CmdSet`, 비트맵은 아래에 있는 세 번째 및 `GuidSymbol` 요소인 `guidImages`합니다. 이 규칙을 따가 필요는 없지만 각 메뉴, 그룹, 명령 및 비트맵의 자식 이어야 합니다는 `GuidSymbol` 요소입니다.

 두 번째에서 `GuidSymbol` 요소를 패키지 명령 집합을 나타내는 일부의 `IDSymbol` 요소입니다. 각 [IDSymbol 요소](../../extensibility/idsymbol-element.md) 숫자 값으로 이름을 매핑하고 메뉴, 그룹 또는 명령 집합의 일부인 명령을 나타낼 수 있습니다. 합니다 `IDSymbol` 세 번째에서 요소 `GuidSymbol` 명령에 대 한 아이콘으로 사용할 수 있는 요소 나타내는 비트맵입니다. GUID/ID 쌍이 동일한 두 명의 자식이 없는 응용 프로그램에서 고유 해야 하므로 `GuidSymbol` 요소에 동일한 값을 가질 수 있습니다.

### <a name="menus-groups-and-commands"></a>메뉴, 그룹 및 명령
 에 있는 경우 메뉴, 그룹 또는 명령 GUID 및 ID를 IDE에 추가할 수 있습니다. 모든 UI 요소에는 다음 작업을 있어야 합니다.

- `guid` 특성의 이름과 일치 하는 `GuidSymbol` UI 요소에서 정의 된 요소입니다.

- `id` 연결 된 이름과 일치 하는 특성 `IDSymbol` 요소입니다.

     함께 `guid` 및 `id` 특성을 구성 합니다 *서명* UI 요소입니다.

- `priority` 해당 부모 메뉴 또는 그룹에 있는 UI 요소의 위치를 결정 하는 특성입니다.

- A [부모 요소](../../extensibility/parent-element.md) 포함 `guid` 및 `id` 부모 메뉴 또는 그룹의 서명을 지정 하는 특성입니다.

#### <a name="menus"></a>메뉴
 로 정의 된 각 메뉴는 [메뉴 요소](../../extensibility/menu-element.md) 에 `Menus` 섹션. 메뉴 있어야 `guid`, `id`, 및 `priority` 특성으로 `Parent` 요소 또한 다음 추가 특성 및 자식:

- `type` 메뉴 도구 모음 또는 메뉴의 일종으로 IDE에 표시될지 여부를 지정 하는 특성입니다.

- [문자열 요소](../../extensibility/strings-element.md) 를 포함 하는 [ButtonText 요소](../../extensibility/buttontext-element.md), IDE의 메뉴의 제목을 지정 하는 및 [CommandName 요소](../../extensibility/commandname-element.md)는 이름을 지정 하는 에 사용 합니다 **명령** 메뉴에 액세스 하는 창입니다.

- 선택적 플래그입니다. A [CommandFlag 요소](../../extensibility/command-flag-element.md) 의 모양이 나 IDE에서 동작을 변경 하려면 메뉴 정의에 나타날 수 있습니다.

  모든 `Menu` 도구 모음 같은 요소를 도킹 가능 하지 않은 요소를 부모로 그룹이 있어야 합니다. 도킹 메뉴는 해당 부모입니다. 메뉴 및 값에 대 한 자세한 내용은 합니다 `type` 특성을 참조 하십시오는 [메뉴 요소](../../extensibility/menu-element.md) 설명서.

  다음 예제에서는 Visual Studio 메뉴 모음에서 옆에 표시 되는 메뉴의 **도구** 메뉴.

```xml
<Menu guid="guidTopLevelMenuCmdSet"
id="TopLevelMenu" priority="0x700" type="Menu">
  <Parent guid="guidSHLMainMenu"
          id="IDG_VS_MM_TOOLSADDINS" />
  <Strings>
    <ButtonText>TestMenu</ButtonText>
    <CommandName>TestMenu</CommandName>
  </Strings>
</Menu>
```

#### <a name="groups"></a>그룹
 그룹에 정의 된 항목은는 `Groups` 의 섹션을 *.vsct* 파일입니다. 그룹은 단순히 컨테이너입니다. 이러한 나타나지 제외 하 고 IDE의 메뉴에 구분선으로 합니다. 따라서 한 [그룹 요소](../../extensibility/group-element.md) 해당 서명, 우선 순위 및 부모를 통해서만 정의 됩니다.

 그룹 부모로 메뉴, 다른 그룹 또는 자체 있을 수 있습니다. 그러나 부모는 일반적으로 메뉴 또는 도구 모음. 앞의 예제에서 메뉴의 자식인는 `IDG_VS_MM_TOOLSADDINS` 그룹과 해당 그룹에는 Visual Studio 메뉴 모음의 자식입니다. 다음 예제에서 그룹에는 앞의 예제에서 메뉴의 자식입니다.

```xml
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"
priority="0x0600">
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
 </Group>
```

 메뉴의 일부 이기 때문에이 그룹에 명령 하는 일반적으로 포함 됩니다. 그러나 다른 메뉴도 포함할 수 있습니다. 이것이, 다음 예와에서 같이 하위 메뉴를 정의 하는 방법입니다.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"
priority="0x0100" type="Menu">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>
  <Strings>
    <ButtonText>Sub Menu</ButtonText>
    <CommandName>Sub Menu</CommandName>
  </Strings>
</Menu>
```

#### <a name="commands"></a>명령
 IDE에 제공 되는 명령으로 정의 되어는 [Button element](../../extensibility/button-element.md) 또는 [Combo 요소](../../extensibility/combo-element.md)합니다. 메뉴 또는 도구 모음에 표시할 명령을 부모로 그룹이 있어야 합니다.

##### <a name="buttons"></a>단추
 에 정의 된 단추는 `Buttons` 섹션입니다. 모든 메뉴 항목, 단추 또는 사용자가 단일 명령을 실행 하는 다른 요소는 단추를 간주 됩니다. 일부 단추 형식은 목록 기능을 포함할 수도 있습니다. 단추 필요한 동일한 및 메뉴 있는 선택적 특성을 가질 수도 있습니다 및는 [Icon 요소](../../extensibility/icon-element.md) GUID와 IDE에서 단추를 나타내는 비트맵의 ID를 지정 하는 합니다. 단추와 해당 특성에 대 한 자세한 내용은 참조는 [Buttons 요소](../../extensibility/buttons-element.md) 설명서.

 다음 예제에서 단추를 이전 예제에서는 그룹의 자식 이며 해당 그룹의 부모 메뉴에서 메뉴 항목으로 IDE에 나타났습니다.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

##### <a name="combos"></a>Combos
 Combos에 정의 된 `Combos` 섹션입니다. 각 `Combo` 요소 IDE의 드롭다운 목록 상자를 나타냅니다. 목록 상자 수도 값에 따라 사용자가 쓸 수 없습니다는 `type` 콤보의 특성입니다. Combos 동일한 요소가 포함 하 고 단추는 동작이 다음 추가 특성을 수도 있습니다.

- `defaultWidth` 픽셀 너비를 지정 하는 특성입니다.

- `idCommandList` 목록 상자에 표시 되는 항목이 포함 된 목록을 지정 하는 특성입니다. 동일한 명령 목록을 선언 해야 `GuidSymbol` 콤보 들어 있는 노드입니다.

  다음 예제에서는 콤보 요소를 정의 합니다.

```xml
<Combos>
  <Combo guid="guidFirstToolWinCmdSet"
         id="cmdidWindowsMediaFilename"
         priority="0x0100" type="DynamicCombo"
         idCommandList="cmdidWindowsMediaFilenameGetList"
         defaultWidth="130">
    <Parent guid="guidFirstToolWinCmdSet"
            id="ToolbarGroupID" />
    <CommandFlag>IconAndText</CommandFlag>
    <CommandFlag>CommandWellOnly</CommandFlag>
    <CommandFlag>StretchHorizontally</CommandFlag>
    <Strings>
      <CommandName>Filename</CommandName>
      <ButtonText>Enter a Filename</ButtonText>
    </Strings>
  </Combo>
</Combos>
```

##### <a name="bitmaps"></a>비트맵
 아이콘과 함께 표시 되는 명령을 포함 해야 합니다는 `Icon` 해당 GUID 및 ID를 사용 하 여 비트맵을 참조 하는 요소 각 비트맵으로 정의 됩니다는 [비트맵 요소](../../extensibility/bitmap-element.md) 에 `Bitmaps` 섹션입니다. 유일한 필수 특성을 `Bitmap` 정의 다음과 같습니다 `guid` 및 `href`, 소스 파일을 가리키는 합니다. 원본 파일은 리소스 스트립을 하는 경우는 **usedList** 특성이 필요 하며 스트립에서 사용할 수 있는 이미지를 나열 합니다. 자세한 내용은 참조는 [비트맵 요소](../../extensibility/bitmap-element.md) 설명서.

### <a name="parenting"></a>부모/자식 관리
 다음 규칙은 항목 부모로 다른 항목을 호출 하는 방법을 제어 합니다.

|요소|이 섹션의 명령 테이블 정의|포함 될 수 있습니다 (또는에서 배치를 부모로 가지는 `CommandPlacements` 섹션 중 하나 또는 둘 다)|포함 될 수 있습니다 (부모 라고 함)|
|-------------| - | - | - |
|그룹화|[Groups 요소](../../extensibility/groups-element.md), IDE, 다른 Vspackage|메뉴, 그룹 자체 항목|메뉴, 그룹 및 명령|
|메뉴|[Menus 요소](../../extensibility/menus-element.md), IDE, 다른 Vspackage|1 ~ *n* 그룹|0 *n* 그룹|
|ToolBar|[Menus 요소](../../extensibility/menus-element.md), IDE, 다른 Vspackage|항목과|0 *n* 그룹|
|메뉴 항목|[Buttons 요소](../../extensibility/buttons-element.md), IDE, 다른 Vspackage|1 ~ *n* 항목과 그룹|-0 *n* 그룹|
|단추|[Buttons 요소](../../extensibility/buttons-element.md), IDE, 다른 Vspackage|1 ~ *n* 항목과 그룹||
|콤보|[Combos 요소](../../extensibility/combos-element.md), IDE, 다른 Vspackage|1 ~ *n* 항목과 그룹||

### <a name="menu-command-and-group-placement"></a>메뉴, 명령 및 그룹 배치
 메뉴, 그룹 또는 명령 IDE에서 둘 이상의 위치에 나타날 수 있습니다. 여러 위치에 표시할 항목을 추가 해야 하는 `CommandPlacements` 으로 섹션을 [CommandPlacement 요소](../../extensibility/commandplacement-element.md)합니다. 모든 메뉴, 그룹 또는 명령 명령 배치를 추가할 수 있습니다. 그러나 이러한 상황에 맞는 여러 위치에 나타날 수 없습니다 때문에 도구 모음이 방식으로 배치할 수 없습니다.

 명령 배치 했습니다 `guid`, `id`, 및 `priority` 특성입니다. GUID 및 ID에 배치 되는 항목의 일치 해야 합니다. `priority` 특성은 다른 항목과 관련 된 항목의 배치를 제어 합니다. IDE 동일한 우선 순위를 가진 둘 이상의 항목을 병합 하는 경우에 IDE는 빌드될 때마다 패키지 리소스를 동일한 순서로 읽기는 보장 하지 않으므로 해당 배치 정의 되지 않습니다.

 메뉴 또는 그룹을 여러 위치에 있으면 각 인스턴스에서 해당 메뉴 또는 그룹의 모든 자식에 표시 됩니다.

## <a name="command-visibility-and-context"></a>명령을 표시 유형 및 컨텍스트
 여러 Vspackage 설치 되 면 도구 모음, 메뉴 및 메뉴 항목을 어렵게 IDE를 채울 수 있습니다. 이 문제를 방지 하려면 개별 UI 요소의 표시 유형을 사용 하 여 제어할 수 있습니다 *표시 유형 제약 조건* 및 명령 플래그입니다.

### <a name="visibility-constraints"></a>표시 유형 제약 조건
 표시 유형 제약 조건으로 설정 됩니다는 [VisibilityItem 요소](../../extensibility/visibilityitem-element.md) 에 `VisibilityConstraints` 섹션입니다. 표시 유형 제약 조건을 대상 항목 표시 되는 특정 UI 컨텍스트를 정의 합니다. 메뉴 또는이 섹션에 포함 된 명령 정의 컨텍스트 중 하나가 활성화 되어 있는 경우에 표시 됩니다. 이 섹션에서 메뉴 또는 명령을 참조 하지 않은 경우 기본적으로 표시는 항상입니다. 이 섹션에서는 그룹에 적용 되지 않습니다.

 `VisibilityItem` 요소 세 가지 특성을 다음과 같이 있어야 합니다: 합니다 `guid` 하 고 `id` 대상 UI 요소의 및 `context`합니다. `context` 대상 항목 표시 됩니다 하 고 해당 값으로 모든 유효한 UI 컨텍스트를 사용 하는 경우 특성을 지정 합니다. Visual Studio에 대 한 UI 컨텍스트 상수는의 멤버는 <xref:Microsoft.VisualStudio.VSConstants> 클래스입니다. 모든 `VisibilityItem` 요소 하나만 컨텍스트 값을 사용할 수 있습니다. 두 번째 컨텍스트를 적용 하려면 하나 더 만듭니다 `VisibilityItem` 다음 예와에서 같이 동일한 항목을 가리키는 요소입니다.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

### <a name="command-flags"></a>명령 플래그
 다음 명령 플래그를 메뉴 및 명령을 적용할 때의 표시 여부를 발생할 수 있습니다.

 `AlwaysCreate` 메뉴 단추 없거나 그룹에 해당 하는 경우에 만들어집니다.

 에 대해 유효 합니다. `Menu`

 `CommandWellOnly` 이 플래그를 적용이 최상위 메뉴에 명령이 표시 되지 않습니다 하 고 추가 셸 사용자 지정에 사용할 수 있도록 하려는 경우 예를 들어, 키 바인딩. 사용자가 열어 이러한 명령을 사용자 지정할 수는 VSPackage를 설치한 후 합니다 **옵션** 대화 상자 및 그런 다음 아래 명령 배치를 편집 합니다 **키보드 환경** 범주입니다. 바로 가기 메뉴, 도구 모음, 메뉴 컨트롤러 또는 하위 메뉴의 배치를 주지 않습니다.

 에 대 한 유효한: `Button`, `Combo`

 `DefaultDisabled` 기본적으로 명령이 비활성화 되어 있는 명령을 구현 하는 VSPackage가 로드 되지 않은 경우 QueryStatus 메서드 호출 되지 않았습니다.

 에 대 한 유효한: `Button`, `Combo`

 `DefaultInvisible` 기본적으로 명령은 표시 되지 않습니다 명령을 구현 하는 VSPackage가 로드 되지 않은 경우 QueryStatus 메서드 호출 되지 않았습니다.

 와 결합 된 `DynamicVisibility` 플래그입니다.

 에 대 한 유효한: `Button`, `Combo`, `Menu`

 `DynamicVisibility` 명령의 표시 유형을 사용 하 여 변경할 수 있습니다 합니다 `QueryStatus` 메서드 또는 컨텍스트에서에 포함 된 GUID는 `VisibilityConstraints` 섹션입니다.

 도구 모음에 없는 메뉴에 표시 되는 명령에 적용 됩니다. 최상위 도구 모음 항목을 사용할 수 있지만 숨겨져 있지 않으면 경우는 `OLECMDF_INVISIBLE` 플래그에서 반환 되는 `QueryStatus` 메서드.

 메뉴의이 플래그는이 자동으로 되었을 때 해당 멤버를 숨길지도 나타냅니다. 최상위 메뉴에 이미이 동작 때문에이 플래그는 일반적으로 하위 메뉴에 할당 됩니다.

 와 결합 된 `DefaultInvisible` 플래그입니다.

 에 대 한 유효한: `Button`, `Combo`, `Menu`

 `NoShowOnMenuController` 메뉴 컨트롤러에이 플래그를 있는 명령을 위치, 명령 드롭 다운 목록에 나타나지 않습니다.

 에 대해 유효 합니다. `Button`

 명령 플래그에 대 한 자세한 내용은 참조는 [CommandFlag 요소](../../extensibility/command-flag-element.md) 설명서.

#### <a name="general-requirements"></a>일반 요구 사항
 표시 되 고 사용 되기 전에 명령에서 다음과 같은 일련의 테스트를 전달 해야 합니다.

- 명령은 올바르게 배치 됩니다.

- `DefaultInvisible` 플래그가 설정 되지 않았습니다.

- 부모 메뉴 또는 도구 모음에 표시 됩니다.

- 에 컨텍스트 항목으로 인해 명령이 보이지 않는 아닙니다 합니다 [VisibilityConstraints 요소](../../extensibility/visibilityconstraints-element.md) 섹션입니다.

- VSPackage 구현 하는 코드는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스 표시 하 고 명령을 사용 하도록 설정 합니다. 인터페이스 코드 없이 가로채어 수행에 있습니다.

- 사용자가 명령에 설명 된 절차에 따라 됩니다 [라우팅 알고리즘](../../extensibility/internals/command-routing-algorithm.md)합니다.

## <a name="call-pre-defined-commands"></a>미리 정의 된 명령 호출
 합니다 [UsedCommands 요소](../../extensibility/usedcommands-element.md) 명령에 액세스할 때 다른 Vspackage 또는 IDE에 의해 제공 되는 Vspackage를 사용 하도록 설정 합니다. 이 작업을 수행 하려면 만듭니다는 [UsedCommand 요소](../../extensibility/usedcommand-element.md) 있는 GUID 및 ID를 사용 하는 명령입니다. 이렇게 하면 현재 Visual Studio 구성의 속하지 않는 경우에 명령을 Visual Studio에서 로드 됩니다. 자세한 내용은 [UsedCommand 요소](../../extensibility/usedcommand-element.md)합니다.

## <a name="interface-element-appearance"></a>인터페이스 요소 모양
 선택한 명령 요소 위치 지정에 대 한 고려 사항은 아래와 같습니다.

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 배치에 따라 다르게 표시 되는 여러 UI 요소를 제공 합니다.

- UI 요소를 사용 하 여 정의 된를 `DefaultInvisible` VSPackage 구현에서 표시 하지 않은 플래그 IDE에서 표시 되지 것입니다는 <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> 메서드를 특정 UI 컨텍스트를 사용 하 여 연결 된 또는 `VisibilityConstraints` 섹션.

- 명령은 성공적으로 배치도 표시 될 수 있습니다. IDE는 자동으로 숨기 거 나는 (또는 되지 않은) VSPackage 인터페이스에 따라 일부 명령을 표시 하기 때문에 구현 됩니다. 예를 들어, 일부 VSPackage 구현 하면 빌드 관련 항목이 자동으로 표시 될 인터페이스를 빌드합니다.

- 적용 된 `CommandWellOnly` UI 요소의 정의 플래그 명령을 사용자 지정 하 여만 추가할 수 있는지를 의미 합니다.

- IDE가 디자인 뷰임을 대화 상자가 표시 될 때에 명령 예를 들어, 특정 UI 컨텍스트 에서만에서 사용할 수 있습니다.

- IDE에 표시할 특정 UI 요소를 하나 이상의 인터페이스를 구현 하거나 코드를 작성 해야 합니다.

## <a name="see-also"></a>참고자료
- [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)