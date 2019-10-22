---
title: '&lt;value &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aefe710cc730d5624abc01bbdfc54d9961788787
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656394"
---
# <a name="ltvaluegt-javascript"></a>&lt;value &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ECMAScript 3 속성의 `get` 및 `set` 함수에 대 한 문서 정보를 지정 합니다.

## <a name="syntax"></a>구문

```
<value type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID">description
</value>
```

#### <a name="parameters"></a>매개 변수
 `type` 선택 사항입니다. 속성의 데이터 형식입니다. 형식은 다음 중 하나일 수 있습니다.

- ECMAScript 5 사양(예: `Number` 및 `Object`)에 있는 ECMAScript 언어 형식입니다.

- `HTMLElement`, `Window` 및 `Document`와 같은 DOM 개체입니다.

- JavaScript 생성자 함수입니다.

  `integer` 선택 사항입니다. @No__t_0 `Number` 이면 속성이 정수 인지 여부를 지정 합니다. 속성이 정수 임을 나타내려면 `true`로 설정 합니다. 그렇지 않으면 `false`로 설정 합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `domElement` 선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `type` 특성이 이 특성보다 우선합니다. 이 특성은 문서화 된 속성이 DOM 요소 인지 여부를 지정 합니다. 속성이 DOM 요소 임을 지정 하려면 `true`로 설정 합니다. 그렇지 않으면 `false`로 설정 합니다. @No__t_0 특성을 설정 하지 않고 `domElement`를 `true`로 설정 하면 IntelliSense는 문 완성을 수행할 때 문서화 된 속성을 `HTMLElement`로 처리 합니다.

  `mayBeNull` 선택 사항입니다. 문서화 된 속성을 null로 설정할 수 있는지 여부를 지정 합니다. 속성을 null로 설정할 수 있음을 나타내려면 `true`로 설정 합니다. 그렇지 않으면 `false`로 설정 합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `elementType` 선택 사항입니다. `type`이 `Array`인 경우 이 특성은 배열의 요소 유형을 지정합니다.

  `elementInteger` 선택 사항입니다. `type`이 `Array`이고 `elementType`이 `Number`인 경우 이 특성은 배열의 요소가 정수인지 여부를 지정합니다. 배열의 요소가 정수임을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `elementDomElement` 선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `elementType` 특성이 이 특성보다 우선합니다. `type`이 `Array`인 경우 이 특성은 배열의 요소가 DOM 요소인지 여부를 지정합니다. 요소가 DOM 요소임을 지정하려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. `elementType` 특성이 설정되지 않고 `elementDomElement`가 `true`로 설정된 경우 IntelliSense는 명령문 완성을 수행할 때 배열의 각 요소를 `HTMLElement`로 처리합니다.

  `elementMayBeNull` 선택 사항입니다. `type`이 `Array`인 경우 배열의 요소를 null로 설정할 수 있는지 여부를 지정합니다. 배열의 요소를 null로 설정할 수 있음을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.

  `locid` 선택 사항입니다. 속성에 대 한 지역화 정보에 대 한 식별자입니다. 식별자는 멤버 ID이거나 OpenAjax 메타데이터에 의해 정의된 메시지 번들의 `name` 속성 값에 해당합니다. 식별자 유형은 [\<loc>](../ide/loc-javascript.md) 요소에 지정된 형식에 따라 달라집니다.

  `description` 선택 사항입니다. 속성에 대한 설명입니다.

## <a name="remarks"></a>설명
 ECMAScript 5 속성은 [\<summary >](../ide/summary-javascript.md) 요소를 사용 합니다.

 @No__t_1 또는 `set` 함수 바로 앞에 `<value>` 요소를 사용 합니다.

## <a name="example"></a>예
 다음 코드 예제에서는 `get` 함수에서 `<value>` 요소를 사용 하는 방법을 보여 줍니다.

```javascript
function Sys$CancelEventArgs$get_cancel() {
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>
    if (arguments.length !== 0) throw Error.parameterCount();
    return this._cancel();
}
```

## <a name="see-also"></a>참고 항목
 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)
