---
title: 요소를 포함 합니다. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7287f4e8b611f55ea28e648aec3f95d1407bf07e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350104"
---
# <a name="include-element"></a>요소를 포함 합니다.
찾을 수 있는 파일을 지정 하는 Include 요소에 제공 된 현재 파일에 삽입에 대 한 경로 포함 합니다.  모든 기호 및 형식 정의 컴파일된 결과 포함 됩니다.

## <a name="syntax"></a>구문

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|href|필수 요소. 헤더 파일에 대 한 경로:<br /><br /> href="stdidcmd.h"|
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|없음|없음|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|명령을 나타내는 요소를 모두 정의-메뉴 항목, 메뉴, 도구 모음 및 콤보 상자,-VSPackage IDE를 제공 하는 합니다.|

## <a name="example"></a>예제

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>참고자료
- [Visual Studio 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)