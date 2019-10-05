---
title: KeyBinding 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3bc5e10c928c50bca1ea3879531885f4580519
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309636"
---
# <a name="keybinding-element"></a>KeyBinding 요소
KeyBinding 요소는 명령에 대 한 바로 가기 키를 지정합니다.

 명령에는 상호 연결 된 단일 및 이중 키 바인딩을 가질 수 있습니다. 단일 키 바인딩을 예로 **Ctrl**+**S** 에 대 한 합니다 **저장** 명령입니다. 이중 키 바인딩을 두 개의 연속 키 조합의 명령을 트리거할 필요 합니다. 이중 키 바인딩을 예로 <strong>Ctrl *+</strong>K<strong>를</strong>Ctrl<strong>+</strong>K** 책갈피를 설정 합니다.

## <a name="syntax"></a>구문

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|guid|필수 요소.|
|ID|필수 요소.|
|편집기|필수 요소. 편집기 GUID는이 바로 가기 키를 활성화 될 편집 컨텍스트를 나타냅니다. 전역 바인딩 범위 값은 "guidVSStd97"입니다.|
|key1|필수 요소. 유효한 값은 모두 입력할 수 영숫자 및 두 자리 16 진수 값 0x로 시작 하 고 [VK_constants](/windows/desktop/inputdev/virtual-key-codes)합니다.|
|mod1|선택 사항입니다. 조합을 **Ctrl**를 **Alt**, 및 **Shift** 공백으로 구분 합니다.|
|key2|선택 사항입니다. 유효한 값은 모두 입력할 수 영숫자 및 두 자리 16 진수 값 0x로 시작 하 고 [VK_constants](/windows/desktop/inputdev/virtual-key-codes)합니다.|
|mod2|선택 사항입니다. 조합을 **Ctrl**를 **Alt**, 및 **Shift** 공백으로 구분 합니다.|
|에뮬레이터|선택 사항입니다.|
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|부모||
|주석||

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[KeyBindings 요소](../extensibility/keybindings-element.md)|KeyBinding 요소 그룹 및 다른 KeyBindings 그룹화 합니다.|

## <a name="example"></a>예제

```
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>참고자료
- [KeyBindings 요소](../extensibility/keybindings-element.md)
- [Visual Studio 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
