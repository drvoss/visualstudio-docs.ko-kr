---
title: '&lt;값&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ac74dde41a2d6cea0a768cfc89838cc34ce41afd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179317"
---
# <a name="ltvaluegt-javascript"></a>&lt;값&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

에 대 한 설명서 정보 지정 `get` 및 `set` ECMAScript 3 속성에 대 한 함수입니다.  
  
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
 `type`  
 선택 사항입니다. 속성의 데이터 형식입니다. 형식은 다음 중 하나일 수 있습니다.  
  
- ECMAScript 5 사양(예: `Number` 및 `Object`)에 있는 ECMAScript 언어 형식입니다.  
  
- `HTMLElement`, `Window` 및 `Document`와 같은 DOM 개체입니다.  
  
- JavaScript 생성자 함수입니다.  
  
  `integer`  
  선택 사항입니다. 하는 경우 `type` 는 `Number`, 속성 정수 인지 여부를 지정 합니다. 로 `true` 속성이 정수; 임을 나타내려면이 고, 그렇지로 `false`합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.  
  
  `domElement`  
  선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `type` 특성이 이 특성보다 우선합니다. 이 특성 문서화 된 속성에는 DOM 요소 인지 여부를 지정 합니다. 로 `true` DOM 요소를; 속성을 지정 하려면이 고, 그렇지로 `false`합니다. 경우는 `type` 특성이 설정 되지 않은 및 `domElement` 로 설정 된 `true`, IntelliSense를 문서화 된 속성을 처리는 `HTMLElement` 문 완성 기능을 수행 하는 경우.  
  
  `mayBeNull`  
  선택 사항입니다. 문서화 된 속성을 설정할 수 있는지 여부를 지정 하려면 null입니다. 로 `true` 설정에 null이 고 그렇지 않으면 속성을 설정할 수 있도록 나타내려면 `false`합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.  
  
  `elementType`  
  선택 사항입니다. `type`이 `Array`인 경우 이 특성은 배열의 요소 유형을 지정합니다.  
  
  `elementInteger`  
  선택 사항입니다. `type`이 `Array`이고 `elementType`이 `Number`인 경우 이 특성은 배열의 요소가 정수인지 여부를 지정합니다. 배열의 요소가 정수임을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.  
  
  `elementDomElement`  
  선택 사항입니다. 이 특성은 더 이상 사용되지 않으며, `elementType` 특성이 이 특성보다 우선합니다. `type`이 `Array`인 경우 이 특성은 배열의 요소가 DOM 요소인지 여부를 지정합니다. 요소가 DOM 요소임을 지정하려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. `elementType` 특성이 설정되지 않고 `elementDomElement`가 `true`로 설정된 경우 IntelliSense는 명령문 완성을 수행할 때 배열의 각 요소를 `HTMLElement`로 처리합니다.  
  
  `elementMayBeNull`  
  선택 사항입니다. `type`이 `Array`인 경우 배열의 요소를 null로 설정할 수 있는지 여부를 지정합니다. 배열의 요소를 null로 설정할 수 있음을 나타내려면 `true`로 설정하고, 그렇지 않으면 `false`로 설정합니다. 기본값은 `false`입니다. 이 특성은 Visual Studio에서 IntelliSense 정보를 제공하는 데 사용되지 않습니다.  
  
  `locid`  
  선택 사항입니다. 속성에 대 한 지역화 정보에 대 한 식별자입니다. 식별자는 멤버 ID이거나 OpenAjax 메타데이터에 의해 정의된 메시지 번들의 `name` 속성 값에 해당합니다. 식별자 유형은 [\<loc>](../ide/loc-javascript.md) 요소에 지정된 형식에 따라 달라집니다.  
  
  `description`  
  선택 사항입니다. 속성에 대한 설명입니다.  
  
## <a name="remarks"></a>설명  
 ECMAScript 5 속성 사용 합니다 [ \<요약 >](../ide/summary-javascript.md) 요소입니다.  
  
 사용 합니다 `<value>` 요소 바로 앞의 `get` 또는 `set` 함수입니다.  
  
## <a name="example"></a>예  
 다음 코드 예제를 사용 하는 방법을 보여 줍니다 합니다 `<value>` 요소는 `get` 함수입니다.  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)
