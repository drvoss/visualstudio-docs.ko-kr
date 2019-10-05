---
title: '&lt;param&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a8477de8bf84950d778d4ce843522be35b2d7387
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203753"
---
# <a name="ltparamgt-javascript"></a>&lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

함수 또는 메서드 매개 변수에 대해 문서 정보를 지정합니다.  
  
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
 `name`  
 필수 요소. 매개 변수의 이름입니다.  
  
 `type`  
 선택 사항입니다. 매개 변수의 데이터 형식입니다. 형식은 다음 중 하나일 수 있습니다.  
  
- ECMAScript 5 사양에는 ECMAScript 언어와 같은 입력 `Number` 고 `Object`입니다.  
  
- `HTMLElement`, `Window` 및 `Document`와 같은 DOM 개체입니다.  
  
- JavaScript 생성자 함수입니다.  
  
  `integer`  
  선택 사항입니다. 하는 경우 `type` 는 `Number`, 매개 변수는 정수 인지 여부를 지정 합니다. 로 `true` 매개 변수는 정수; 임을 나타내려면이 고, 그렇지로 `false`합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.  
  
  `domElement`  
  선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `type` 특성이 이 특성보다 우선합니다. 이 특성은 문서화 된 매개 변수는 DOM 요소 인지 여부를 지정 합니다. 로 `true` 매개 변수는 DOM 요소를 지정 하려면이 고, 그렇지로 `false`합니다. 경우는 `type` 특성이 설정 되지 않은 및 `domElement` 로 설정 된 `true`, IntelliSense를 문서화 된 매개 변수를 처리는 `HTMLElement` 문 완성 기능을 수행 하는 경우.  
  
  `mayBeNull`  
  선택 사항입니다. 문서화 된 매개 변수를 설정할 수 있는지 여부를 지정 하려면 null입니다. 로 `true` 설정에 null이 고 그렇지 않으면 매개 변수를 설정할 수 있도록 나타내려면 `false`합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.  
  
  `elementType`  
  선택 사항입니다. `type`이 `Array`인 경우 이 특성은 배열의 요소 유형을 지정합니다.  
  
  `elementInteger`  
  선택 사항입니다. `type`이 `Array`이고 `elementType`이 `Number`인 경우 이 특성은 배열의 요소가 정수인지 여부를 지정합니다. 배열의 요소가 정수임을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.  
  
  `elementDomElement`  
  선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `elementType` 특성이 이 특성보다 우선합니다. `type`이 `Array`인 경우 이 특성은 배열의 요소가 DOM 요소인지 여부를 지정합니다. 요소가 DOM 요소임을 지정하려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. `elementType` 특성이 설정되지 않고 `elementDomElement`가 `true`로 설정된 경우 IntelliSense는 명령문 완성을 수행할 때 배열의 각 요소를 `HTMLElement`로 처리합니다.  
  
  `elementMayBeNull`  
  선택 사항입니다. `type`이 `Array`인 경우 배열의 요소를 null로 설정할 수 있는지 여부를 지정합니다. 배열의 요소를 null로 설정할 수 있음을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.  
  
  `locid`  
  선택 사항입니다. 매개 변수에 대 한 지역화 정보에 대 한 식별자입니다. 식별자는 멤버 ID이거나 OpenAjax 메타데이터에 의해 정의된 메시지 번들의 `name` 속성 값에 해당합니다. 식별자 유형은 [\<loc>](../ide/loc-javascript.md) 요소에 지정된 형식에 따라 달라집니다.  
  
  `parameterArray`  
  선택 사항입니다. 문서화 된 매개 변수에서 지원 되는 매개 변수를 반복에 비슷한 함수 호출에서 반복 될 수 있는지 여부를 지정 된 `String.format` 함수입니다. 로 `true` 로 매개 변수가 고 그렇지 않으면 반복 수 있음을 나타내려면 `false`합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.  
  
  `optional`  
  선택 사항입니다. 문서화 된 매개 변수는 함수 호출에서 선택적 여부를 지정 합니다. 로 `true` 로 매개 변수가 고 그렇지 않으면 선택적 임을 나타내려면 `false`합니다.  
  
  `value`  
  선택 사항입니다. 함수 코드 자체 대신 IntelliSense에서 사용 하기 위해 평가 되어야 하는 코드를 지정 합니다. 이 사용 하 여 특성 매개 변수 형식이 정의 된 형식 정보를 제공 하는 것입니다. 예를 들어 사용할 수 있습니다 `value=’1’` 매개 변수 형식을 숫자로 처리 하도록 합니다.  
  
  `description`  
  선택 사항입니다. 매개 변수의 설명입니다.  
  
## <a name="remarks"></a>설명  
 유일한 필수 특성은 `name`합니다. 다른 모든 특성은 선택 사항입니다.  
  
 요소와 같은 함수에 주석을 추가 하는 데 [ \<요약 >](../ide/summary-javascript.md)를 [ \<param >](../ide/param-javascript.md), 및 [ \<반환 >](../ide/returns-javascript.md)를 배치 해야 합니다 모든 문 앞 함수 본문입니다.  
  
 여러 개의 `<param>` 중 하나는 동일한 이름을 가진 요소를 `<param>` 요소에서 사용 되 고 중복 요소는 무시 됩니다. 요소는 결정 하는 동작을 정의 되지 않았습니다. 경우 `name` 참조 존재 하지 않는 매개 변수에 요소가 무시 됩니다.  
  
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
