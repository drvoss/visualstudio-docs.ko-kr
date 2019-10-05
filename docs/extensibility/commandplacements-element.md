---
title: CommandPlacements 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb22359c936caacef81f4c9b81993a46d47ccc0b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341891"
---
# <a name="commandplacements-element"></a>CommandPlacements 요소
CommandPlacements 요소 그룹 CommandPlacement 요소 및 기타 CommandPlacements 그룹화 합니다.

 CommandPlacements 요소는 선택 사항입니다. 이 섹션을 포함 하지 필요가 없는 명령, 그룹 또는 메뉴를 보조 위치에 포함 되어야 합니다, 경우에 *.vsct* 파일입니다.

## <a name="syntax"></a>구문

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|CommandPlacements|CommandPlacement 요소를 그룹화 하 고 기타 CommandPlacements 그룹화 합니다.|
|[CommandPlacement 요소](../extensibility/commandplacement-element.md)|단추, 그룹 및 메뉴 둘 이상의 그룹 또는 메뉴에 포함 될 수 있습니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|명령을 나타내는 모든 요소를 정의 합니다.|

## <a name="example"></a>예제

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>참고자료
- [CommandPlacement 요소](../extensibility/commandplacement-element.md)
- [Visual Studio 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)