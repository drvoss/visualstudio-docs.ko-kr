---
title: GuidSymbol 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bebcec561f915bd8223d0adc183293a1760c261d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342209"
---
# <a name="guidsymbol-element"></a>GuidSymbol 요소
`GuidSymbol` 요소 메뉴, 그룹 또는 명령을 나타내는 guid: id 쌍의 GUID를 포함 합니다. ID에서 제공 되는 `IDSymbol` 요소에는 `GuidSymbol` 요소입니다. `GuidSymbol` 요소에는 `name` 에 포함 된 GUID 친숙 한 이름을 제공 하는 특성을 `value` 특성.

## <a name="syntax"></a>구문

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|name|필수 요소. GUID 기호와의 이름입니다.|
|값|필수 요소. GUID 기호와의 GUID입니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[IDSymbol 요소](../extensibility/idsymbol-element.md)|메뉴, 그룹 또는 명령을 나타내는 guid: id 쌍의 ID를 포함 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Symbols 요소](../extensibility/symbols-element.md)|그룹 `GuidSymbol` 의 요소를 *.vsct* 파일입니다.|

## <a name="remarks"></a>설명
 일반적으로 *.vsct* 파일을 포함 된 세 가지 `GuidSymbol` 요소에 해당 `Symbols` 섹션, 패키지 자체에 대 한 명령 집합 (메뉴의 컬렉션으로 그룹화 및 패키지를 사용할 수 있도록 하는 명령)에 대 한 및 단추 및 기타 시각적 구성 요소에 대 한 아이콘을 제공 하는 비트맵에 대 한 하나입니다. 모든 `IDSymbol` 요소에는 주어진 `GuidSymbol` 요소는 고유 해야 합니다. `value`합니다. 그러나 `IDSymbol` 으로 부모가 서로 다른 패키지에 동일한 값을 가진 요소가 있을 수 있습니다.

## <a name="see-also"></a>참고자료
- [Visual Studio 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)