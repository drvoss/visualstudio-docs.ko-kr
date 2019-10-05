---
title: 요소 단추 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e10b4f8749aa7e42a7fb95afb31d98907e45d05f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321292"
---
# <a name="button-element"></a>Button 요소
사용자가 상호 작용할 수 있는 요소를 정의 합니다. 다른 종류의 단추 수 있습니다. 단추, MenuButton, 및 SplitDropDown 합니다.

## <a name="syntax"></a>구문

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|guid|필수 요소. GUID/i D 명령 식별자의 GUID입니다.|
|ID|필수 요소. GUID/i D 명령 식별자의 ID입니다.|
|priority|선택 사항입니다. 우선 순위를 지정 하는 숫자 값입니다.|
|type|선택 사항입니다. 단추의 종류를 지정 하는 열거형된 값입니다.<br /><br /> 지정 하지 않으면 단추를 사용 합니다.<br /><br /> 단추<br /> 메뉴 및 상황에 맞는 메뉴 (일반적으로 아이콘 단추로) 도구 모음에 표시 되는 표준 명령입니다.<br /><br /> MenuButton<br /> 명령 실행 되지 않는 메뉴 항목 이지만 다른 메뉴를 생성 합니다.<br /><br /> SplitDropDown<br /> Microsoft Word의 표준 도구 모음에서 실행 취소 및 다시 실행 단추와 같은 컨트롤입니다.|
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[부모 요소](../extensibility/parent-element.md)|선택 사항입니다. 단추의 부모 요소입니다.|
|[Icon 요소](../extensibility/icon-element.md)|선택 사항입니다. 단추와 연결 된 아이콘입니다.|
|[Command flag 요소](../extensibility/command-flag-element.md)|필수 요소. 단추에 대 한 유효한 CommandFlag 값은 다음과 같습니다.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> - DontCache<br /><br /> -DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> -Pict<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|
|[Strings 요소](../extensibility/strings-element.md)|필수 요소. 자식 [ButtonText 요소](../extensibility/buttontext-element.md) 정의 해야 합니다.|
|주석|선택적 설명입니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Buttons 요소](../extensibility/buttons-element.md)|단추 요소를 그룹화합니다.|

## <a name="example"></a>예제
 다음 예제에서는 정의의 단추를 *.vsct* 파일입니다.

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>참고자료
- [Visual Studio 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)