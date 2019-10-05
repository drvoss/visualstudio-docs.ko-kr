---
title: 요소를 기호 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 303d13d94a413ad3ce17e0bd2b56fe95455e9f54
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316657"
---
# <a name="symbols-element"></a>Symbols 요소
Guid 및 기타 VSCT 요소에서 사용 되는 Id를 정의 합니다. 비관리 코드에 대 한이 정보 일반적으로 제공 하 여 지정 된 헤더 파일에서 [Extern 요소](../extensibility/extern-element.md)합니다. 코드는이 정보를 정의 하는 기호 요소의 자식 요소를 관리 합니다.

 기존.cto 파일에서.vsct 파일을 만든 경우 기호를 기호 요소의 자식으로 생성 됩니다. 자세한 내용은 [방법: 만들기는 합니다. 기존 Vsct 파일입니다. Cto 파일](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)합니다.

 Symbols 요소와 혼동 하지 마십시오 합니다 [정의 요소](../extensibility/define-element.md), 전처리기 사용에 대 한 이름-값 쌍을 정의 하는 합니다.

## <a name="syntax"></a>구문

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|없음||

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|GuidSymbol|GUID 기호를 정의합니다. GuidSymbol에 2 개의 필수 특성이: 이름 및 값입니다. 이름은 기호, 이름 및 값은 문자열로 GUID의 값입니다.<br /><br /> 예를 들어:\<GuidSymbol 이름 = "guidVsPackage1Pkg" value = "{c5f54698-101a-4846-84d3-dc748f9cd848}" / >|
|IDSymbol|기호를 정의합니다. IDSymbol에 2 개의 필수 특성이: 이름 및 값입니다. 이름은 기호, 이름 및 값은 문자열로 기호의 값입니다.<br /><br /> 예를 들어:\<IDSymbol 이름 = "MyMenuGroup" value = "0x1020" / >|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|.Vsct 파일의 루트 요소입니다.|

## <a name="example"></a>예제

```
<Symbols>
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
    <IDSymbol name="cmdidMyTool" value="0x0101" />
  </GuidSymbol>
</Symbols>
```

## <a name="see-also"></a>참고 항목
- [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)