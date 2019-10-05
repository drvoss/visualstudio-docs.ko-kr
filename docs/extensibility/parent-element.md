---
title: 부모 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f64c99f030fa436eb250531ddd5c2f11bcd2bac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316927"
---
# <a name="parent-element"></a>부모 요소
단추 또는 콤보 상자의 부모를 그룹 수만 있습니다. 메뉴 또는 그룹의 부모는 다른 메뉴 또는 그룹 수 있습니다. 에 [CommandPlacement 요소](../extensibility/commandplacement-element.md)에이 요소가 필요 하며 다른 모든 인스턴스에 선택적 것입니다. 이 요소를 생략 하면 부모의 `Group_Undefined:0` 암시 됩니다.

## <a name="syntax"></a>구문

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|guid|필수 요소. GUID의 GUID/i D 명령 식별자입니다.|
|ID|필수 요소. ID의 GUID/i D 명령 식별자입니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|통합된 개발 환경 (IDE)에 VSPackage가 제공 하는 명령을 나타내는 모든 요소를 정의 합니다. 예를 들어 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자입니다.|
|[Buttons 요소](../extensibility/buttons-element.md)|그룹 [Button 요소](../extensibility/button-element.md) 요소입니다.|
|[Menus 요소](../extensibility/menus-element.md)|VSPackage를 구현 하는 모든 메뉴를 정의 합니다.|
|[Groups 요소](../extensibility/groups-element.md)|VSPackage의 명령 그룹을 정의 하는 항목을 포함 합니다.|

## <a name="see-also"></a>참고자료
- [Visual Studio 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)