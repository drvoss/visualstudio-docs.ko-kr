---
title: VSCT XML 스키마 조건부 특성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11807129c34fa613ef06b3534adc7c7ebb9865e0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322947"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML 스키마 조건부 특성
모든 목록 및 항목에 조건부 특성을 적용할 수 있습니다. 논리 연산자 및 기호 확장 식에는 true 또는 false로 평가합니다. True 이면 연결 된 목록이 나 항목이 결과 출력에 포함 됩니다.

 다른 토큰 확장 또는 상수에 대 한 토큰 확장을 테스트할 수 있습니다. 함수 `Defined()` 값이 없는 경우에 특정 이름을 정의 되어 있는지 여부를 테스트 합니다.

 Condition 특성을 목록에 적용 하면 조건 목록에서 모든 자식 요소에 적용 됩니다. 자식 요소 자체의 Condition 특성에 있으면 다음 조건이 결합 됩니다 부모 식을 사용 하 여 AND 연산에 의해.

 1, '1' 및 'true' 값을 true로 평가 하 고 0, '0' 및 'f a l'이 false로 평가 됩니다.

## <a name="operators"></a>연산자
 조건부 식을 평가 하는 다음 연산자를 사용 합니다.

|연산자|정의|
|--------------|----------------|
|(,)|그룹화|
|!|논리 NOT|
|\<, >, \<=, >=, ==, !=|관계형 및 같음|
|및|Boolean|
|또는|Boolean|

## <a name="examples"></a>예제

```xml
<Menu Condition="Defined(DEBUG)" ...
</Menu>

<Menu Condition="%(SKU_MODE) = 'Demo'" ...
</Menu>

<Menus Condition="Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>

<Menus Condition="Defined(DEMO_SKU)">
    <Menus Condition="!Defined(DEBUG)">
        <Menu ...
        </Menu>
    </Menus>

    <Menu ...
    </Menu>
</Menus>

<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))
and !Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>
```

## <a name="see-also"></a>참고자료
- [Visual Studio 명령 테이블 (합니다. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)