---
title: '&lt;var&gt;(JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca6207d22d82e607fa589f944230b36b46e633c2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670355"
---
# <a name="ltparamgt-javascript"></a>&lt;param &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

함수 또는 메서드의 매개 변수에 대한 정보를 지정합니다.

## <a name="syntax"></a>구문

```
<param name="parameterName" type="ParameterType"
    integer="true|false" domElement="true|false"
    mayBeNull="true|false" elementType="ArrayElementType"
    elementInteger="true|false" elementDomElement="true|false"
    elementMayBeNull="true|false" locid="descriptionID"
    parameterArray="true|false" optional="true|false"
    value="code">description
</param>
```

#### <a name="parameters"></a>매개 변수
 `name` 필수입니다. 매개 변수의 이름입니다.

 `type` 선택 사항입니다. 매개 변수의 데이터 형식입니다. 형식은 다음 중 하나일 수 있습니다.

- ECMAScript 5 사양(예: `Number` 및 `Object`)에 있는 ECMAScript 언어 형식입니다.

- `HTMLElement`, `Window` 및 `Document`와 같은 DOM 개체입니다.

- JavaScript 생성자 함수입니다.

  `integer` 선택 사항입니다. `type` `Number` 경우 매개 변수가 정수 인지 여부를 지정 합니다. 변수가 정수임을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `domElement` 선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `type` 특성이 이 특성보다 우선합니다. 이 특성은 문서화된 변수가 DOM 요소인지 여부를 지정합니다. 변수가 DOM 요소임을 지정하려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. `type` 특성이 설정되지 않고 `domElement`가 `true`로 설정된 경우 IntelliSense는 명령문 완성을 수행할 때 문서화된 변수를 `HTMLElement`로 처리합니다.

  `mayBeNull` 선택 사항입니다. 문서화된 변수를 null로 설정할 수 있는지 여부를 지정합니다. 변수를 null로 설정할 수 있음을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `elementType` 선택 사항입니다. `type`이 `Array`인 경우 이 특성은 배열의 요소 유형을 지정합니다.

  `elementInteger` 선택 사항입니다. `type`이 `Array`이고 `elementType`이 `Number`인 경우 이 특성은 배열의 요소가 정수인지 여부를 지정합니다. 배열의 요소가 정수임을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `elementDomElement` 선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `elementType` 특성이 이 특성보다 우선합니다. `type`이 `Array`인 경우 이 특성은 배열의 요소가 DOM 요소인지 여부를 지정합니다. 요소가 DOM 요소임을 지정하려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. `elementType` 특성이 설정되지 않고 `elementDomElement`가 `true`로 설정된 경우 IntelliSense는 명령문 완성을 수행할 때 배열의 각 요소를 `HTMLElement`로 처리합니다.

  `elementMayBeNull` 선택 사항입니다. `type`이 `Array`인 경우 배열의 요소를 null로 설정할 수 있는지 여부를 지정합니다. 배열의 요소를 null로 설정할 수 있음을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `locid` 선택 사항입니다. 변수에 대한 지역화 정보의 식별자입니다. 식별자는 멤버 ID이거나 OpenAjax 메타데이터에 의해 정의된 메시지 번들의 `name` 속성 값에 해당합니다. 식별자 유형은 [\<loc>](../ide/loc-javascript.md) 요소에 지정된 형식에 따라 달라집니다.

  `parameterArray` 선택 사항입니다. `String.format` 함수에서 지원 되는 반복 매개 변수와 유사 하 게 설명 된 매개 변수를 함수 호출에서 반복할 수 있는지 여부를 지정 합니다. 매개 변수를 반복할 수 있음을 나타내려면 `true`로 설정 합니다. 그렇지 않으면 `false`로 설정 합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `optional` 선택 사항입니다. 호출 하는 함수에서 문서화 된 매개 변수가 선택적인 지 여부를 지정 합니다. 매개 변수가 선택적인 지 여부를 나타내려면 `true`로 설정 합니다. 그렇지 않으면 `false`로 설정 합니다.

  `value` 선택 사항입니다. 함수 코드 자체 대신 IntelliSense에서 사용 하기 위해 평가 해야 하는 코드를 지정 합니다. 매개 변수 형식이 정의 되어 있지 않은 경우이 특성을 사용 하 여 형식 정보를 제공할 수 있습니다. 예를 들어 `value=’1’`를 사용 하 여 매개 변수 형식을 숫자로 취급할 수 있습니다.

  `description` 선택 사항입니다. 매개 변수에 대한 설명

## <a name="remarks"></a>설명
 유일 하 게 필요한 특성은 `name`입니다. 다른 모든 특성은 선택 사항입니다.

 [\<summary>](../ide/summary-javascript.md), [\<param>](../ide/param-javascript.md) 및 [\<returns>](../ide/returns-javascript.md)를 포함하는 함수에 주석을 추가하는 데 사용되는 요소는 문장 앞에 배치되어야 합니다.

 이름이 같은 `<param>` 요소가 여러 개 있는 경우 `<param>` 요소 중 하나가 사용 되며 중복 요소가 무시 됩니다. 사용 되는 요소를 결정 하는 동작은 정의 되지 않습니다. `name` 존재 하지 않는 매개 변수를 참조 하는 경우 요소는 무시 됩니다.

## <a name="example"></a>예
 다음 코드 예제에서는 `<param>` 요소를 사용하는 방법을 보여줍니다.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

// Uses of <param> with the value attribute.

function calculate(a) {
    /// <param name='a' value='1'/>
    a.    // Completion list for a Number.
}

function calculate(a) {
    /// <param name='a' value='{x:0,y:0}'/>
    a.    // x and y appear in the completion list.
}

```

## <a name="see-also"></a>참고 항목
 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)
