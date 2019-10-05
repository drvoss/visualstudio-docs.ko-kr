---
title: Combo 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a97163f1f7dc2a1152bc22f4bc3a68ed32b3cfe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334904"
---
# <a name="combo-element"></a>Combo 요소
콤보 상자에 표시 되는 명령을 정의 합니다. 다음과 같이 네 가지 콤보 상자를 가지: DropDownCombo, DynamicCombo, IndexCombo, 및 MRUCombo 합니다.

## <a name="syntax"></a>구문

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|guid|필수 요소. GUID/i D 명령 식별자의 GUID입니다.|
|ID|필수 요소. GUID/i D 명령 식별자의 ID입니다.|
|defaultWidth|필수 요소. 콤보 상자에 대 한 픽셀 너비를 지정 하는 정수입니다.|
|idCommandList|필수 요소. 콤보 상자에 표시할 항목의 목록을 검색 하려면 현재 명령 대상에 전송 되는 ID입니다. 컨트롤 같은 GUID 범위 ID 됩니다.|
|priority|선택 사항입니다. 우선 순위를 지정 하는 숫자 값입니다.|
|type|선택 사항입니다. 단추의 종류를 지정 하는 열거형된 값입니다.<br /><br /> 지정 하지 않으면 단추를 사용 합니다.<br /><br /> DropDownCombo<br /> VSPackage는이 콤보 상자에 내용을 입력 하는 일을 담당 합니다. 사용자의이 드롭다운 텍스트 상자에 아무 것도 입력할 수 없습니다.<br /><br /> DynamicCombo<br /> VSPackage는이 콤보 상자의 내용을 입력 하는 일을 담당 합니다. 사용자는이 콤보를 편집 하 고 그 안에 항목을 선택할 수도 수 있습니다.<br /><br /> IndexCombo<br /> 해당 텍스트가 아닌 항목의 인덱스를 발생 DynamicCombo 한다는 점을 제외 하면 동일 합니다.<br /><br /> MRUCombo<br /> VSPackage 대신 하 여 통합된 개발 환경 (IDE)에 의해 채워집니다.  사용자가이 콤보 상자에서 편집할 수 있습니다. 콤보 상자 당 마지막 16 개 항목만 최대 IDE 기억합니다.<br /><br /> 사용자는 콤보 상자에서 항목을 선택 하거나 새 기다린다, 적절 한 VSPackage를 IDE에 알립니다.|
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|부모|선택 사항입니다. 단추의 부모 요소입니다.|
|CommandFlag|필수 요소. 참조 [Command flag 요소](../extensibility/command-flag-element.md)합니다. 단추에 대 한 유효한 CommandFlag 값은 다음과 같습니다.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> - DynamicVisibility<br /><br /> -필터 키<br /><br /> - IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|
|문자열|필수 요소. 참조 [Strings 요소](../extensibility/strings-element.md)합니다. 자식 ButtonText 요소 정의 되어야 합니다.|
|주석|선택적 설명입니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Commands 요소](../extensibility/commands-element.md)|VSPackage 도구 모음에서 명령의 컬렉션을 나타냅니다.|

## <a name="example"></a>예제

```xml
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>

<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  priority="0x0500" type="DropDownCombo" defaultWidth="100"
  idCommandList="cmdidGetInsertOptionsList">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>
```

## <a name="see-also"></a>참고자료
- [Visual Studio 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
