---
title: 작성 합니다. Vsct 파일 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85e466e7ebb6294a77e89040260c16fe0043e372
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437663"
---
# <a name="authoring-vsct-files"></a>작성 합니다. Vsct 파일
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 문서에는 Visual Studio 통합된 개발 환경 (IDE)에 메뉴 항목, 도구 모음 및 기타 사용자 인터페이스 (UI) 요소를 추가 하려면.vsct 파일을 작성 하는 방법을 보여 줍니다. .Vsct 파일을 이미 없는 Visual Studio 패키지 (VSPackage) UI 요소를 추가 하는 경우 다음이 단계를 사용 합니다.  
  
 새 프로젝트의 경우 선택 사항에 따라 이미 사용자 지정 편집기, 도구 창이 나 메뉴 명령에 대 한 필수 요소는.vsct 파일을 생성 하기 때문에 Visual Studio 패키지 템플릿을 사용 하는 것이 좋습니다. VSPackage의 요구 사항에 맞게이.vsct 파일을 수정할 수 있습니다. .Vsct 파일을 수정 하는 방법에 대 한 자세한 내용은에 나와 있는 예제를 참조 하세요 [확장 메뉴 및 명령을](../../extensibility/extending-menus-and-commands.md)합니다.  
  
## <a name="authoring-the-file"></a>파일 작성  
 이러한 단계에서.vsct 파일을 작성 합니다. 파일 및 리소스에 대 한 구조 만들기, UI 요소를 선언, IDE에서 UI 요소를 배치 및 모든 특수 동작을 추가 합니다.  
  
### <a name="file-structure"></a>파일 구조  
 .Vsct 파일의 기본 구조를 [CommandTable](../../extensibility/commandtable-element.md) 포함 하는 루트 요소를 [명령](../../extensibility/commands-element.md) 요소 및 [기호](../../extensibility/symbols-element.md) 요소입니다.  
  
##### <a name="to-create-the-file-structure"></a>파일 구조를 만들려면  
  
1. 단계를 수행 하 여.vsct 파일을 프로젝트에 추가할 [방법: 만들기는 합니다. Vsct 파일](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)합니다.  
  
2. 필요한 네임 스페이스를 추가 합니다 `CommandTable` 요소를 다음 예제에서와 같이 합니다.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3. 에 `CommandTable` 요소를 추가 `Commands` 요소를 사용자 지정 메뉴, 도구 모음, 명령 그룹 및 명령은 모든 호스트 합니다. 사용자 지정 UI 요소를 로드 하는 `Commands` 요소가 있어야 합니다. 해당 `Package` 특성 패키지의 이름으로 설정 합니다.  
  
     후 합니다 `Commands` 요소를 추가 `Symbols` 요소 이름과 패키지에 대 한 Guid를 정의 하 고 UI 요소에 대 한 명령 Id입니다.  
  
### <a name="including-visual-studio-resources"></a>Visual Studio 리소스를 포함 하 여  
 사용 된 [Extern](../../extensibility/extern-element.md) Visual Studio 명령 및 IDE에서 UI 요소를 배치 하는 데 필요한 메뉴를 정의 하는 파일에 액세스 하는 요소입니다. 패키지 외부에 정의 된 명령을 사용 하는 경우 사용 합니다 [UsedCommands](../../extensibility/usedcommands-element.md) Visual Studio에 알림을 보내야 하는 요소입니다.  
  
##### <a name="to-include-visual-studio-resources"></a>Visual Studio 리소스를 포함 합니다.  
  
1. 맨 위에 있는 `CommandTable` 요소를 추가 `Extern` 각 외부 파일을 참조 하 고 설정에 대 한 요소는 `href` 특성을 파일의 이름입니다. Visual Studio 리소스에 액세스 하려면 다음 헤더 파일을 참조할 수 있습니다.  
  
    - Stdidcmd.h, Visual Studio에서 노출 하는 모든 명령에 대 한 Id를 정의 합니다.  
  
    - Vsshlids.h, Visual Studio 메뉴에 대 한 명령 Id를 포함 합니다.  
  
2. 패키지는 Visual Studio에서 또는 다른 패키지에서 정의 된 모든 명령을 호출 하는 경우 추가 `UsedCommands` 요소 뒤의 `Commands` 요소입니다. 이 요소와 채우기는 [UsedCommand](../../extensibility/usedcommand-element.md) 패키지의 일부가 아닌 호출 된 각 명령에 대 한 요소입니다. 설정 합니다 `guid` 및 `id` 의 특성을 `UsedCommand` 요소를 호출 하는 명령의 GUID 및 ID 값입니다. Guid 및 Visual Studio의 Id의 명령을 찾는 방법에 대 한 자세한 내용은 참조 하세요. [Guid 및 Visual Studio 명령 Id](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)합니다. 명령에서 다른 패키지를 호출 하려면 GUID 및 해당 패키지에 대 한.vsct 파일에 정의 된 명령 ID를 사용 합니다.  
  
### <a name="declaring-ui-elements"></a>UI 요소를 선언합니다.  
 모든 새로운 UI 요소에 선언 된 `Symbols` .vsct 파일의 섹션입니다.  
  
##### <a name="to-declare-ui-elements"></a>UI 요소를 선언 하려면  
  
1. 에 `Symbols` 요소를 3 개 추가 [GuidSymbol](../../extensibility/guidsymbol-element.md) 요소입니다. 각 `GuidSymbol` 요소에는 `name` 특성으로 `value` 특성입니다. 설정 된 `name` 특성 요소의 용도 반영 합니다. `value` 특성은 GUID를 사용 합니다. (에서 GUID를 생성 하는 **도구** 메뉴에서 클릭 **GUID 만들기**를 선택한 후 **레지스트리 형식**.)  
  
     첫 번째 `GuidSymbol` 요소 패키지를 나타내며 일반적으로 자식이 없습니다. 두 번째 `GuidSymbol` 요소 나타냅니다 명령을 설정 하 고 모든 프로그램 메뉴, 그룹 및 명령을 정의 하는 기호가 포함 됩니다. 세 번째 `GuidSymbol` 요소 이미지 저장소를 나타내고 프로그램 명령에 대 한 아이콘의 모든 기호가 포함 되어 있습니다. 명령 없음 아이콘을 사용 하는 경우에 세 번째를 생략할 수 있습니다 `GuidSymbol` 요소입니다.  
  
2. 에 `GuidSymbol` 하나 이상 추가 하는 명령 집합을 나타내는 요소 [IDSymbol](../../extensibility/idsymbol-element.md) 요소입니다. 이러한 각 메뉴, 도구 모음, 그룹 또는 UI를 추가 하는 명령을 나타냅니다.  
  
     각각에 대 한 `IDSymbol` 요소를 설정 합니다 `name` 특성을 사용 하 여 해당 메뉴, 그룹 또는 명령 참조를 설정한 이름을 `value` 명령 id를 나타내는 16 진수 숫자로 요소입니다. 두 개의 `IDSymbol` 동일한 부모 요소에 동일한 값을 가질 수 있습니다.  
  
3. 아이콘에 필요한 UI 요소에 있는 경우 추가 `IDSymbol` 각 아이콘에 대 한 요소는 `GuidSymbol` 이미지 저장소를 나타내는 요소입니다.  
  
### <a name="putting-ui-elements-in-the-ide"></a>IDE에서 UI 요소를 배치합니다.  
 [메뉴](../../extensibility/menus-element.md) 요소인 [그룹](../../extensibility/groups-element.md) 요소 및 [단추](../../extensibility/buttons-element.md) 요소는 모든 메뉴, 그룹 및 패키지에 정의 된 명령에 대 한 정의 포함 합니다. 이러한 메뉴, 그룹 및 명령을 사용 하 여 IDE에서 배치를 [부모](../../extensibility/parent-element.md) 를 사용 하 여 또는 UI 요소 정의의 일부인 요소를 [CommandPlacement](../../extensibility/commandplacement-element.md) 요소를 다른 곳에 정의 합니다.  
  
 각 `Menu`, `Group`, 및 `Button` 요소에는 `guid` 특성 및 `id` 특성입니다. 항상 설정 합니다 `guid` 특성의 이름과 일치 하도록를 `GuidSymbol` 명령을 나타내는 요소를 설정 및 설정를 `id` 특성의 이름으로는 `IDSymbol` 프로그램 메뉴, 그룹 또는 명령에는 나타내는요소`Symbols`섹션입니다.  
  
##### <a name="to-define-ui-elements"></a>UI 요소를 정의 하려면  
  
1. 새 메뉴, 하위 메뉴, 바로 가기 메뉴 또는 도구 모음을 정의 하는 경우 추가 `Menus` 요소는 `Commands` 요소입니다. 그런 다음 만들려는 각 메뉴에 대 한 추가 [메뉴](../../extensibility/menu-element.md) 요소를 `Menus` 요소입니다.  
  
    설정 합니다 `guid` 및 `id` 의 특성을 `Menu` 요소와 설정은 `type` 원하는 메뉴 유형의 특성입니다. 설정할 수도 있습니다는 `priority` 특성을 상위 그룹에서 메뉴의 상대적 위치를 설정 합니다.  
  
   > [!NOTE]
   > `priority` 특성 도구 모음과 상황에 맞는 메뉴에 적용 되지 않습니다.  
  
2. Visual Studio IDE에 있는 모든 명령 메뉴 및 도구 모음의 직계 자식만 명령 그룹으로 호스트 되어야 합니다. 새 메뉴 또는 도구 모음에 추가할 IDE, 이러한 새 명령 그룹을 포함 해야 합니다. 또한 명령을 시각적으로 그룹화 할 수 있도록 기존 메뉴 및 도구 모음에 명령 그룹을 추가할 수 있습니다.  
  
    새 명령 그룹을 추가한 경우 먼저 만들어야 합니다는 `Groups` 요소를 추가 하 고는 [그룹](../../extensibility/group-element.md) 각 명령 그룹에 대 한 요소입니다.  
  
    설정 합니다 `guid` 하 고 `id` 각 특성 `Group` 요소와 설정을 `priority` 부모 메뉴에 있는 그룹의 상대 위치를 설정 하는 특성입니다. 자세한 내용은 [단추가의 다시 사용할 수 있는 그룹 만들기](../../extensibility/creating-reusable-groups-of-buttons.md)합니다.  
  
3. 새 명령을 ide에 추가 하는 경우 추가 `Buttons` 요소는 `Commands` 요소입니다. 그런 다음 각 명령에 대 한 추가 [단추](../../extensibility/button-element.md) 요소는 `Buttons` 요소입니다.  
  
   1. 설정 합니다 `guid` 및 `id` 각 특성 `Button` 요소와 설정의 `type` 특성을 원하는 단추의 종류입니다. 설정할 수도 있습니다는 `priority` 특성을 상위 그룹에서 명령의 상대적 위치를 설정 합니다.  
  
      > [!NOTE]
      > 사용 하 여 `type="button"` 표준 메뉴 명령 및 도구 모음의 단추에 대 한 합니다.  
  
   2. 에 `Button` 요소를 추가 [문자열](../../extensibility/strings-element.md) 포함 하는 요소는 [ButtonText](../../extensibility/buttontext-element.md) 요소 및 [CommandName](../../extensibility/commandname-element.md) 요소입니다. `ButtonText` 요소 메뉴 항목 또는 도구 모음 단추에 대 한 도구 설명에 대 한 텍스트 레이블을 제공 합니다. `CommandName` 요소 명령에 사용할 명령의 이름을 제공 합니다.  
  
   3. 명령 아이콘이는 경우 만들기는 [아이콘](../../extensibility/icon-element.md) 요소에는 `Button` 요소를 설정 하 고 해당 `guid` 및 `id` 특성을 `Bitmap` 아이콘에 대 한 요소입니다.  
  
      > [!NOTE]
      > 도구 모음 단추에는 아이콘이 있어야 합니다.  
  
      자세한 내용은 참조 하세요. [Menucommand 합니다. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)합니다.  
  
4. 아이콘에 필요한 모든 명령의 경우 추가 [비트맵](../../extensibility/bitmaps-element.md) 요소는 `Commands` 요소입니다. 그런 다음 각 아이콘에 대 한 추가 [비트맵](../../extensibility/bitmap-element.md) 요소는 `Bitmaps` 요소입니다. 비트맵 리소스의 위치를 지정 하는 위치입니다. 자세한 내용은 [메뉴 명령에 아이콘 추가](../../extensibility/adding-icons-to-menu-commands.md)합니다.  
  
   대부분의 메뉴, 그룹 및 명령을 올바르게 배치할 부모/자식 관리 구조에 사용할 수 있습니다. 매우 큰 명령 집합에 대 한 여러 위치에서 메뉴, 그룹 또는 명령 해야 표시 되 면 명령 배치를 지정 하는 것이 좋습니다.  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>IDE에서 UI 요소를 배치 하는 부모/자식 관리에 의존  
  
1. 일반적인 부모/자식 관리를 만듭니다는 `Parent` 각 요소 `Menu`, `Group`, 및 `Command` 패키지에 정의 된 요소입니다.  
  
    대상의 `Parent` 요소는 메뉴 또는 메뉴를 포함 하는 그룹, 그룹 또는 명령입니다.  
  
   1. 설정 된 `guid` 특성의 이름으로는 `GuidSymbol` 명령 집합을 정의 하는 요소입니다. 해당 대화 상자가 패키지의 일부가 아닌 경우에 대상 요소는 해당.vsct 파일에 정의 된 대로 해당 명령 집합의 guid를 사용 합니다.  
  
   2. 설정 된 `id` 일치 하는 특성을 `id` 대상 메뉴 또는 그룹의 특성입니다. 메뉴 및 Visual Studio에 의해 노출 되는 그룹의 나열을 참조 하세요 [Guid 및 Visual Studio 메뉴의 Id](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) 하거나 [Guid 및 Id의 Visual Studio 도구 모음](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)합니다.  
  
   IDE에 배치 하는 UI 요소 수가 많은 경우 또는 여러 위치에 표시 되는 요소가 있으면 해당 배치에 정의 된 [CommandPlacements](../../extensibility/commandplacements-element.md) 요소를 다음 단계에 표시 된 대로.  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>명령 배치를 사용 하 여 IDE에서 UI 요소를 배치 하려면  
  
1. 후 합니다 `Commands` 요소를 추가 `CommandPlacements` 요소입니다.  
  
2. 에 `CommandPlacements` 요소를 추가 `CommandPlacement` 각 메뉴, 그룹 또는 배치 하는 명령에 대 한 요소입니다.  
  
    각 `CommandPlacement` 요소 또는 `Parent` IDE 한곳에서 메뉴, 그룹 또는 명령 하나를 배치 하는 요소입니다. UI 요소에 하나의 부모 하나만 있지만 여러 명령 배치를 가질 수 있습니다. 여러 위치에서 UI 요소를 배치 하려면 추가 `CommandPlacement` 각 위치에 대 한 요소입니다.  
  
3. 설정 합니다 `guid` 및 `id` 각 특성 `CommandPlacement` 호스팅 메뉴나 하듯이 그룹 요소에 대 한 것을 `Parent` 요소입니다. 설정할 수도 있습니다는 `priority` UI 요소의 상대 위치를 설정 하는 특성입니다.  
  
   부모/자식 관리 하 여 배치 및 명령 배치를 혼합할 수 있습니다. 그러나 매우 큰 명령 집합에 대 한 명령 배치만 사용 하는 것이 좋습니다.  
  
### <a name="adding-specialized-behaviors"></a>특수 한 동작 추가  
 사용할 수 있습니다 [CommandFlag](../../extensibility/command-flag-element.md) 요소 모양과 표시를 변경 하려면, 예를 들어 메뉴 및 명령 동작을 수정 합니다. 명령을 사용 하 여 표시 되는 경우 달라질 수 있습니다 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)를 사용 하 여 바로 가기 키를 추가 하거나 [KeyBindings](../../extensibility/keybindings-element.md)합니다. 특정 종류의 메뉴 및 명령에 이미 기본 제공 동작 전문화가 있습니다.  
  
##### <a name="to-add-specialized-behaviors"></a>특수 한 동작을 추가 하려면  
  
1. UI 요소를 표시 하려면 예를 들어, 특정 UI 컨텍스트 에서만에서 솔루션을 로드 되 면 표시 유형 제약 조건을 사용 합니다.  
  
   1. 후 합니다 `Commands` 요소를 추가 `VisibilityConstraints` 요소입니다.  
  
   2. 제한 하려면 각 UI 항목에 대해 추가 된 [VisibilityItem](../../extensibility/visibilityitem-element.md) 요소입니다.  
  
   3. 각각에 대해 `VisibilityItem` 요소를 설정 합니다 `guid` 및 `id` 메뉴, 그룹 또는 명령 및 설정 하는 특성을 `context` 에 정의 된 대로 원하는 UI 컨텍스트에 특성를 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 클래스. 자세한 내용은 [VisibilityItem 요소](../../extensibility/visibilityitem-element.md)합니다.  
  
2. 코드에서 표시 유형 또는 UI 항목의 가용성을 설정 하려면 하나 이상의 다음 명령 플래그를 사용 합니다.  
  
   - DefaultDisabled  
  
   - DefaultInvisible  
  
   - DynamicItemStart  
  
   - DynamicVisibility  
  
   - NoShowOnMenuController  
  
   - NotInTBList  
  
     자세한 내용은 [Command Flag 요소](../../extensibility/command-flag-element.md)합니다.  
  
3. 요소 표시 되거나 동적으로 모양을 변경 하는 방법을 변경 하려면 하나 이상의 다음 명령 플래그를 사용 합니다.  
  
   - AlwaysCreate  
  
   - CommandWellOnly  
  
   - DefaultDocked  
  
   - DontCache  
  
   - DynamicItemStart  
  
   - FixMenuController  
  
   - IconAndText  
  
   - pict  
  
   - StretchHorizontally  
  
   - TextMenuUseButton  
  
   - TextChanges  
  
   - TextOnly  
  
     자세한 내용은 [Command Flag 요소](../../extensibility/command-flag-element.md)합니다.  
  
4. 요소 명령을 수신 하는 경우 어떻게 반응할지를 변경 하려면 다음 명령 플래그 중 하나 이상을 사용 합니다.  
  
   - AllowParams  
  
   - CaseSensitive  
  
   - CommandWellOnly  
  
   - FilterKeys  
  
   - NoAutoComplete  
  
   - NoButtonCustomize  
  
   - NoKeyCustomize  
  
   - NoToolbarClose  
  
   - PostExec  
  
   - RouteToDocs  
  
   - TextIsAnchorCommand  
  
     자세한 내용은 [Command Flag 요소](../../extensibility/command-flag-element.md)합니다.  
  
5. 종속 메뉴 바로 가기 메뉴 또는 메뉴에 있는 항목에 연결할 추가 앰퍼샌드 문자 ('& ')에 `ButtonText` 메뉴 또는 메뉴 항목에 대 한 요소입니다. 앰퍼샌드 뒤의 문자가 부모 메뉴 열려 있을 때 현재 바로 가기 키입니다.  
  
6. 메뉴에 관계 없이 바로 가기 키에 연결 하려면 명령을 사용 하 여 [KeyBindings](../../extensibility/keybindings-element.md)합니다. 자세한 내용은 [KeyBinding 요소](../../extensibility/keybinding-element.md)합니다.  
  
7. 메뉴 텍스트를 지역화 하려면 사용 된 `LocCanonicalName` 요소입니다. 자세한 내용은 [Strings 요소](../../extensibility/strings-element.md)합니다.  
  
   일부 메뉴 및 단추 형식에는 특수 한 동작이 포함 됩니다. 다음 표에서 몇 가지 특수 한 메뉴 및 단추 형식에 설명합니다. 다른 형식에 대 한 참조를 `types` 특성에 대 한 설명을 [메뉴 요소](../../extensibility/menu-element.md), [Button 요소](../../extensibility/button-element.md), 및 [Combo 요소](../../extensibility/combo-element.md)합니다.  
  
   콤보 상자  
   콤보 상자에 도구 모음에서 사용할 수 있는 드롭다운 목록입니다. 콤보 상자에 UI를 추가 하려면 만들기를 [Combos](../../extensibility/combos-element.md) 요소에는 `Commands` 요소입니다. 추가할 합니다 `Combos` 요소를 `Combo` 각 콤보 상자에 추가할 요소입니다. `Combo` 요소는 동일한 특성 및 자식으로 `Button` 요소와 `DefaultWidth` 및 `idCommandList` 특성입니다. 합니다 `DefaultWidth` 픽셀에서 너비를 설정 하는 특성 및 `idCommandList` 특성 콤보 상자를 채우는 데 사용 되는 명령 ID를 가리킵니다. 자세한 내용은 참조는 `Combo` 요소 설명서.  
  
   MenuController  
   메뉴 컨트롤러는 옆쪽 화살표가 있는 단추입니다. 화살표를 클릭 하면 목록을 엽니다. UI에 메뉴 컨트롤러를 추가 하려면 만듭니다는 `Menu` 요소 집합과 해당 `type` 특성을 **MenuController** 또는 **MenuControllerLatched**원하는 동작에 따라 합니다. 메뉴 컨트롤러를 채우기 위해의 부모로 설정할는 `Group` 요소입니다. 메뉴 컨트롤러는 해당 그룹의 모든 자식 드롭다운 목록에 표시 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio 명령 테이블 (합니다. Vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)
