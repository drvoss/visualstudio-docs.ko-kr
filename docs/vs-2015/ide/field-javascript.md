---
title: '&lt;var&gt;(JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b2fe09070261460b7b83f54de44a07cf96d40cf2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181267"
---
# <a name="ltfieldgt-javascript"></a>&lt;필드&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

설명을 포함하여 개체에 정의된 필드 또는 멤버에 대한 정보를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
<field name="fieldName" static="true|false"  
    type="FieldType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID"  
    value="code">description  
</field>  
```  
  
#### <a name="parameters"></a>매개 변수  
 `name`  
 필드 또는 멤버의 이름입니다. 경우는 `<field>` 요소를 사용 하는 생성자 함수에서 `name` 필요 하 고 태그를 적용할 멤버를 정의 합니다. 경우는 `<field>` 요소는 직접 필드,이 특성은 무시에 주석을 달고 Visual Studio에서 사용 하는 이름은 소스 코드에서 실제 필드의 이름입니다.  
  
 `static`  
 선택 사항입니다. 필드는 생성자 함수 멤버인 생성자 함수에서 반환 된 개체의 멤버 지정 합니다. 로 `true` 생성자 함수의 구성원으로 필드를 처리 합니다. 로 `false` 생성자 함수에서 반환 되는 개체의 구성원으로 필드를 처리 합니다.  
  
 `type`  
 선택 사항입니다. 필드의 데이터 형식을 입력합니다. 형식은 다음 중 하나일 수 있습니다.  
  
- ECMAScript 5 사양(예: `Number` 및 `Object`)에 있는 ECMAScript 언어 형식입니다.  
  
- `HTMLElement`, `Window` 및 `Document`와 같은 DOM 개체입니다.  
  
- JavaScript 생성자 함수입니다.  
  
  `integer`  
  선택 사항입니다. `type`이 `Number`인 경우 변수가 정수인지 여부를 지정합니다. 변수가 정수임을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.  
  
  `domElement`  
  선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `type` 특성이 이 특성보다 우선합니다. 이 특성은 문서화된 변수가 DOM 요소인지 여부를 지정합니다. 변수가 DOM 요소임을 지정하려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. `type` 특성이 설정되지 않고 `domElement`가 `true`로 설정된 경우 IntelliSense는 명령문 완성을 수행할 때 문서화된 변수를 `HTMLElement`로 처리합니다.  
  
  `mayBeNull`  
  선택 사항입니다. 문서화된 변수를 null로 설정할 수 있는지 여부를 지정합니다. 변수를 null로 설정할 수 있음을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.  
  
  `elementType`  
  선택 사항입니다. `type`이 `Array`인 경우 이 특성은 배열의 요소 유형을 지정합니다.  
  
  `elementInteger`  
  선택 사항입니다. `type`이 `Array`이고 `elementType`이 `Number`인 경우 이 특성은 배열의 요소가 정수인지 여부를 지정합니다. 배열의 요소가 정수임을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.  
  
  `elementDomElement`  
  선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `elementType` 특성이 이 특성보다 우선합니다. `type`이 `Array`인 경우 이 특성은 배열의 요소가 DOM 요소인지 여부를 지정합니다. 요소가 DOM 요소임을 지정하려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. `elementType` 특성이 설정되지 않고 `elementDomElement`가 `true`로 설정된 경우 IntelliSense는 명령문 완성을 수행할 때 배열의 각 요소를 `HTMLElement`로 처리합니다.  
  
  `elementMayBeNull`  
  선택 사항입니다. `type`이 `Array`인 경우 배열의 요소를 null로 설정할 수 있는지 여부를 지정합니다. 배열의 요소를 null로 설정할 수 있음을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.  
  
  `helpKeyword`  
  선택 사항입니다. F1 도움말의 키워드입니다.  
  
  `locid`  
  선택 사항입니다. 변수에 대한 지역화 정보의 식별자입니다. 식별자는 멤버 ID이거나 OpenAjax 메타데이터에 의해 정의된 메시지 번들의 `name` 속성 값에 해당합니다. 식별자 유형은 [\<loc>](../ide/loc-javascript.md) 태그에 지정된 형식에 따라 달라집니다.  
  
  `value`  
  선택 사항입니다. 함수 코드 자체 대신 IntelliSense에서 사용 하기 위해 평가 되어야 하는 코드를 지정 합니다. 에 대 한 `<field>`,이 특성 생성자 함수에 대 한 지원 되지만 개체 리터럴에 대 한 지원 되지 않습니다. 이 사용 하 여 특성 필드 형식이 정의 된 형식 정보를 제공 하는 것입니다. 예를 들어 사용할 수 있습니다 `value=’1’` 필드 형식을 숫자로 처리 하도록 합니다.  
  
  `description`  
  선택 사항입니다. 오류에 대한 설명입니다.  
  
## <a name="remarks"></a>설명  
 `name` 특성은 생성자 함수에서 필드를 문서화 하는 경우에 필요 합니다. 다른 모든 시나리오에 대 한 모든 특성이 `<field>` 요소는 선택 사항입니다.  
  
 생성자 함수를 문서화 하는 경우는 `<field>` 요소 필드 선언 바로 앞에 나타나야 합니다. `name` 특성에는 소스 코드에 사용 되는 필드 이름과 일치 해야 합니다. 개체 멤버에 대 한 합니다 `name` 경우 특성을 생략할 수 있습니다는 `<field>` 개체 멤버 선언 직전 요소가 표시 됩니다.  
  
## <a name="example"></a>예  
 다음 코드 예제에서는 `<field>` 요소를 사용하는 방법을 보여줍니다.  
  
```javascript  
// Use of <field> in an object definition.  
var Rectangle = {  
    /// <field type='Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type='Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
  
// Use of <field> in a constructor function.  
// The name attribute is required.  
function Engine() {  
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
    this.HorsePower = 150;  
}  
```  
  
## <a name="example"></a>예  
 다음 예제에서는 `<field>` `static` 특성이로 `true`설정 된 요소를 사용 하는 방법을 보여 줍니다.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## <a name="example"></a>예  
 다음 예제에서는 `<field>` `static` 특성이로 `false`설정 된 요소를 사용 하는 방법을 보여 줍니다.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
var eng = new Engine();  
// IntelliSense on the field is available here.  
eng.  
  
```  
  
## <a name="example"></a>예  
 다음 예제에서는 `value` 특성에서 `<field>` 요소를 사용하는 방법을 보여 줍니다.  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>참고 항목  
 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)
