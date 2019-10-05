---
title: 함수가 필요 합니다. | Microsoft 문서
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4442143b2766ed3608a852d0f811a6b943fd19df
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007108"
---
# <a name="function-expected"></a>함수가 필요합니다.
중 하나를 호출 하려고 하거나 합니다 **함수 프로토타입** 되지 않은 개체의 메서드는 `Function` 개체, 함수 호출 컨텍스트의 개체를 사용 합니다. 때문에 다음 코드에서이 오류를 생성 하는 예를 들어 **예제에서는** 함수가 아닙니다.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 호출한 **함수 프로토타입에** 메서드를 `Function` 개체입니다.  
  
- 함수 호출 연산자를 사용 해야 `()` 만 함수를 호출 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [함수 개체](../../javascript/reference/function-object-javascript.md)   
 [prototype 속성(Object)](../../javascript/reference/prototype-property-object-javascript.md)