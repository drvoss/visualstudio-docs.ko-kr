---
title: Extern 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34e38618a153aa74bdc2449895272fc9e399c82d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342794"
---
# <a name="extern-element"></a>Extern 요소
Extern 요소는 모든 외부 헤더가 참조 ( *.h*)를 병합 하는 파일을 *.vsct* 컴파일 타임에 파일입니다. VSCT 컴파일러인 지정 되거나 참조 포함 경로에 병합할 파일 이어야 합니다는 [Include 요소](../extensibility/include-element.md)합니다. 기타 파일이 될 수 있습니다 *.vsct* 파일 또는 C++ 헤더 파일입니다.

 폼의 헤더 파일에 정의 해야 "#define [기호] [Value]" 값을 이전에 정의 된 경우 다른 기호를 수 있습니다. 명령은 항목의 조건문에서 정의 사용할 수 있습니다. 실제로 사용 되는 모든 기호는 무시 됩니다.

 CommandTable 요소 Extern 요소

## <a name="syntax"></a>구문

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|href|필수 요소. 헤더 파일에 대 한 경로:<br /><br /> href="stdidcmd.h"|
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|
|language|선택 사항입니다. 모든 기본 언어가 [ \<문자열 >](../extensibility/strings-element.md) 명령 테이블에 있는 요소:<br /><br /> language="en-us"|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|없음|없음|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|명령을 나타내는 요소를 모두 정의-메뉴 항목, 메뉴, 도구 모음 및 콤보 상자,-VSPackage IDE를 제공 하는 합니다.|

## <a name="example"></a>예제

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>참고자료
- [Visual Studio 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)