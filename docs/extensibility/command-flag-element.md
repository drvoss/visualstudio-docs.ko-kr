---
title: 명령 플래그 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a38708d6256556693b7ab1dfc8c04b79f484ee8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334846"
---
# <a name="command-flag-eelement"></a>명령 플래그 Eelement
부모 요소를 수정합니다.

## <a name="syntax"></a>구문

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 잘못 된 요소 값을 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|값|설명|
|-----------|-----------------|
|AllowParams|사용자의 명령 매개 변수를 입력할 수를 나타냅니다 합니다 **명령** 명령의 정식 이름을 입력할 때 창입니다.<br /><br /> 에 대해 유효 합니다. `Button`|
|AlwaysCreate|메뉴 단추 없거나 그룹에 해당 하는 경우에 만들어집니다.<br /><br /> 에 대해 유효 합니다. `Menu`|
|CaseSensitive|사용자 항목 대/소문자를 구분 하지 않습니다.<br /><br /> 에 대해 유효 합니다. `Combo`|
|CommandWellOnly|최상위 메뉴에 명령이 표시 되지 않습니다 하 고 바로 가기 키에 바인딩 추가 셸 사용자 지정, 예를 들어 사용할 수 있도록 하려는 경우이 플래그를 적용 합니다. VSPackage를 설치한 후 열고 다음이 명령을 사용자를 지정할 수 있습니다 합니다 **옵션** 대화 상자 및 그런 다음 아래 명령 배치를 편집 합니다 **키보드 환경** 범주입니다. 이 플래그는 바로 가기 메뉴, 도구 모음, 메뉴 컨트롤러 또는 하위 메뉴에 대 한 배치 영향을 주지 않습니다.<br /><br /> 에 대 한 유효한: `Button`, `Combo`|
|DefaultDisabled|명령을 구현 하는 VSPackage가 로드 되지 않은 경우 기본적으로 비활성화 또는 `QueryStatus` 메서드 호출 되지 않았습니다.<br /><br /> 에 대 한 유효한: `Button`, `Combo`|
|DefaultDocked|기본적으로 도킹 합니다. 항상 컨트롤이 도킹 된 도구 모음에 적용이 더 이상 설정 합니다.|
|DefaultInvisible|기본적으로 명령이 보이지 않으면 구현 하는 VSPackage가 로드 되지 않은 경우 또는 `QueryStatus` 메서드 호출 되지 않았습니다.<br /><br /> 이를 결합 하는 것이 좋습니다는 `DynamicVisibility` 플래그입니다.<br /><br /> 에 대 한 유효한: `Button`, `Combo`, `Menu`|
|DontCache|개발 환경 캐시 하지 않습니다는 `QueryStatus` 이 명령에 대 한 메서드 결과입니다.<br /><br /> 메뉴에 메뉴 컨트롤러를 해당 메뉴 항목의 텍스트를 캐시 하지 그러면 합니다. 메뉴 동적 항목 또는 동적 텍스트가 포함 된 항목을 포함 하는 경우이 플래그를 사용 합니다.<br /><br /> 에 대 한 유효한: `Button`, `Menu`|
|DynamicItemStart|동적 목록 시작을 나타냅니다. 연속적으로 호출 하 여 목록을 작성 하는 환경을 가능 하 게이 `QueryStatus` OLECMDERR_E_UNSUPPORTED 플래그 반환 될 때까지 목록 항목에는 메서드. 이 가장 최근에 사용 된 같은 (MRU) 목록 및 창 목록 항목에 대 한 잘 작동 합니다.<br /><br /> 에 대해 유효 합니다. `Button`|
|DynamicVisibility|명령의 가시성을 통해 변경할 수 있습니다 합니다 `QueryStatus` 메서드 또는 컨텍스트에 포함 된 GUID 통해는 `VisibilityConstraints` 섹션입니다.<br /><br /> 주 창에 표시 되는 최상위 도구 모음에는 없지만 메뉴 및 도구 창 도구 모음에서 표시 되는 명령에 적용 됩니다. 최상위 도구 모음 항목을 사용 하지 않도록 설정 하지만 숨겨져 있지 않으면이 OLECMDF_INVISIBLE 플래그에서 반환 되 면 수는 `QueryStatus` 메서드. 도구 창 도구 모음에 표시 되는 도구 모음 명령은 숨길 수 있습니다.<br /><br /> 메뉴의이 플래그는이 자동으로 숨기면 모든 해당 멤버를 숨길지도 나타냅니다. 최상위 메뉴에 이미이 동작 때문에이 플래그는 일반적으로 하위 메뉴에 할당 됩니다.<br /><br /> 이 플래그를 사용 하 여 결합 된 `DefaultInvisible` 플래그입니다.<br /><br /> 에 대 한 유효한: `Button`, `Combo`, `Menu`|
|FilterKeys|아래에서 필터링 하는 키 항목을 참조 하세요 [Combo 요소](../extensibility/combo-element.md)합니다.<br /><br /> 에 대해 유효 합니다. `Combo`|
|FixMenuController|이 명령이 메뉴 컨트롤러에서 배치 되는, 명령이 항상 기본값이; 즉, 메뉴 컨트롤러 단추 자체 선택 될 때마다 명령을 선택 합니다. 메뉴 컨트롤러에는 `TextIsAnchorCommand` 플래그가 설정 메뉴 컨트롤러도 되는 명령 해당 텍스트를 사용 하는 다음을 `FixMenuController` 플래그입니다.<br /><br /> 메뉴 컨트롤러에서 명령을 하나만 있어야 합니다 `FixMenuController` 플래그입니다. 둘 이상의 명령으로 표시 하므로 기본 명령을 메뉴에서 마지막 명령인이 됩니다.<br /><br /> 에 대해 유효 합니다. `Button`|
|IconAndText|메뉴 및 도구 모음에서 아이콘 및 텍스트를 표시 합니다.<br /><br /> 에 대 한 유효한: `Button`, `Combo`, `Menu`|
|NoAutoComplete|자동 완성 기능을 사용 하는 사용할 수 없습니다.<br /><br /> 에 대해 유효 합니다. `Combo`|
|NoButtonCustomize|이 단추를 사용자 지정 사용자 수 없도록 합니다.<br /><br /> 에 대 한 유효한: `Button`, `Combo`|
|NoKeyCustomize|사용자 지정 키보드를 사용 하지 마십시오.<br /><br /> 에 대 한 유효한: `Button`, `Combo`|
|NoShowOnMenuController|이 명령이 메뉴 컨트롤러에서 배치 되는, 명령 드롭 다운 목록에 나타나지 않습니다.<br /><br /> 에 대해 유효 합니다. `Button`|
|NotInTBList|사용 가능한 도구 모음 목록에 나타나지 않습니다. 도구 모음 메뉴 형식에 대해서만 유효합니다.<br /><br /> 에 대해 유효 합니다. `Menu`|
|NoToolbarClose|사용자는 도구 모음을 닫을 수 없습니다. 도구 모음 메뉴 형식에 대해서만 유효합니다.<br /><br /> 에 대해 유효 합니다. `Menu`|
|pict|도구 모음 있지만 메뉴에 텍스트만 아이콘을 표시 합니다. 아이콘 없음이 지정 된 경우 도구 모음에서 클릭할 수 있는 빈 공간을 보여 줍니다.<br /><br /> 에 대해 유효 합니다. `Button`|
|PostExec|명령 비차단 수 있습니다. 모든 사전 처리 쿼리가 완료 될 때까지 실행을 지연 하는 개발 환경입니다.<br /><br /> 에 대해 유효 합니다. `Button`|
|RouteToDocs|이 명령은 현재 문서에 라우팅됩니다.<br /><br /> 에 대해 유효 합니다. `Button`|
|StretchHorizontally|이 플래그를 설정 하는 경우 너비 콤보 상자에 대 한 최소 너비 되며 콤보 상자의 사용 가능한 공간을 채우기 위해 늘여 도구 모음에서 공간이 있는 경우. 이 도구 모음, 도킹 가로로 및 하나의 콤보 상자 도구 모음에서 (첫 번째 콤보 상자를 제외한 모든 플래그는 무시 됨) 플래그를 사용할 수는 경우에 발생 합니다.<br /><br /> 에 대해 유효 합니다. `Combo`|
|TextMenuUseButton|사용 된 `ButtonText` 메뉴에 대 한 필드입니다. 기본 필드는 `MenuText` 지정 된 경우.<br /><br /> 에 대해 유효 합니다. `Button`|
|TextChanges|명령 또는 메뉴 텍스트도 통해 일반적으로 런타임 시 변경할 수 있습니다는 `QueryStatus` 메서드.<br /><br /> 에 대 한 유효한: `Button`, `Menu`|
|TextChangesButton|에 대해 유효 합니다. `Button`|
|TextIsAnchorCommand|메뉴 컨트롤러에 대 한 메뉴의 텍스트 (앵커) 기본 명령에서 가져옵니다. 앵커 명령에는 마지막 명령을 선택한 래치입니다. 이 플래그를 설정 하지 않으면, 메뉴 컨트롤러는 자체 `MenuText` 필드입니다. 그러나 해당 컨트롤러에서 마지막 선택한 명령을 활성화 계속 메뉴 컨트롤러를 클릭 합니다.<br /><br /> 이 플래그를 결합 하는 것이 좋습니다는 `TextChanges` 플래그입니다.<br /><br /> 이 플래그는 MenuController 또는 MenuControllerLatched 메뉴 형식에 적용 됩니다.<br /><br /> 에 대해 유효 합니다. `Menu`|
|TextMenuCtrlUseMenu|사용 된 `MenuText` 필드에 메뉴 컨트롤러입니다. 기본 필드는 `ButtonText`합니다.<br /><br /> 에 대해 유효 합니다. `Button`|
|TextMenuUseButton|사용 된 `ButtonText` 메뉴에 대 한 필드입니다. 기본 필드는 `MenuText` 지정 된 경우.<br /><br /> 에 대해 유효 합니다. `Button`|
|TextOnly|아이콘을 지정 하는 경우에 도구 모음 또는 메뉴 있지만 아이콘 없음만 텍스트를 표시 합니다.<br /><br /> 에 대해 유효 합니다. `Button`|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Buttons 요소](../extensibility/buttons-element.md)|에 대 한 그룹을 제공 [Button 요소](../extensibility/button-element.md) 요소입니다.|
|[Menus 요소](../extensibility/menus-element.md)|VSPackage를 구현 하는 모든 메뉴를 정의 합니다.|

## <a name="see-also"></a>참고자료
- [Visual Studio 명령 테이블 (합니다. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)