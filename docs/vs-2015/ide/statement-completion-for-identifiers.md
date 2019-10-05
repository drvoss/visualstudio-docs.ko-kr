---
title: 식별자 문 완성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 89f507c2f4d01cf5e3e1e983cfcb5bafd9d9a7dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152908"
---
# <a name="statement-completion-for-identifiers"></a>식별자 문 완성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript 변수 선언에 대 한 입력 명시적 허용 하지 않습니다. 결과적으로, IntelliSense 개체에 대 한 완성 목록을 제공할 항상 수 없습니다. 다양 한 상황에서 발생할 수 있습니다. 다음은 몇 가지 일반적인 경우입니다.  
  
- 매개 변수는 선언 되지만 호출 되지 않았습니다 다른 곳에서 활성 문서에서 다음 예와에서 같이 합니다.  
  
  ```javascript  
  function illuminate(light) {  
           light.  // Accurate statement completion is not available   
                   // unless illuminate is called elsewhere with a   
                   // parameter that has a value. If it is called only  
                   // in a function that is a sibling to   
                   // illuminate(light) in the call hierarchy, the   
                   // IntelliSense engine also cannot determine the   
                   // parameter type.  
       }  
  
  // Sibling function. No statement completion for light   
  // object in preceding code.  
  function lightLamp() {  
      var x = illuminate(1);  
  }  
  
  // Uncomment the next line to obtain statement completion for  
  // light object in preceding code.  
  // var x = illuminate(1);  
  ```  
  
- 개체는 이벤트에 대 한 응답에서 호출 되는 함수입니다. 디자인 타임에 IntelliSense 엔진은이 상황에서 사용 하는 개체의 형식을 확인할 수 없습니다.  
  
   IntelliSense 엔진 이벤트를 호출 해야 함을, 일반적으로 사용을 통해 확인할 수 있으면 `addEventListener` 활성 문서의 이벤트에 대 한 IntelliSense 정보를 보다 정확 하 게 제공 됩니다.  
  
  IntelliSense 개체를 식별할 수 없는 경우 명명 된 엔터티 또는 활성 문서에 있는 식별자를 사용 하 여 완성 목록을 IntelliSense 엔진에 채웁니다. 완성 목록에 이러한 식별자가 포함 된 경우 정보 아이콘 옆에 나타납니다. 또한 각 식별자에 대 한 도구 설명 식 알려진 아님을 나타냅니다. 다음 그림에서는 문 완료 옵션 형식의 개체에 대 한 `light` 개체 및 해당 속성 정의 되므로 식별할 수 없습니다. 그러나 합니다 `intensity` 에서 사용 되어 속성을 식별자 목록에서 사용할 수는 `illuminate` 함수입니다.  
  
  **식별할 수 없는 개체에 대 한 완료 옵션**  
  
  ![식별자에 대 한 JavaScript IntelliSense](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")  
  
  개체에 대 한 완성 목록에는 XML 문서 주석 또는 JavaScript IntelliSense 확장성 기능을 사용 하 여 재정의할 수 있습니다. 이러한 기능을 사용 하 여 제공할 수 있습니다 형식 정보 및 설명이 포함 된 IntelliSense 정보 것이 고 그렇지 못할 경우. 자세한 내용은 [JavaScript IntelliSense 확장](../ide/extending-javascript-intellisense.md) 하 고 [XML 문서 주석 만들기](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
