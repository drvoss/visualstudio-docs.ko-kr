---
title: Icon 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd56391084788729c0f8439728f9afffd59da946
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311249"
---
# <a name="icon-element"></a>Icon 요소
아이콘 태그의 guid 속성에 정의 된 비트맵의 guid입니다. `id` 특성 비트맵 스트립에 슬롯을 선택 합니다. 이 요소는 선택적입니다. 이 요소를 사용 하는 경우의 값이 포함 되었습니다 **guidOfficeIcon:msotcidNoIcon** 암시 됩니다.

## <a name="syntax"></a>구문

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|guid|필수 요소. 정의 된 비트맵의 guid입니다.|
|ID|필수 요소. 비트맵 스트립에 슬롯을 선택합니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|없음|없음|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Buttons 요소](../extensibility/buttons-element.md)||

## <a name="see-also"></a>참고자료
- [Visual Studio 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)