---
title: "'return' 문이 함수 외부 | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01ef96385d5fe3dccf14a7491e67983d39913280
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006408"
---
# <a name="return-statement-outside-of-function"></a>함수 외부에 'return' 문이 있습니다.
사용 하는 `return` 코드의 전역 범위에 문의 합니다. `return` 함수의 본문 안에 문을 사용할만 해야 합니다.  
  
 사용 하 여 함수를 호출 합니다 `()` 연산자는 식입니다. 모든 식에 값이 있습니다. `return` 문을 사용 하는 함수에서 반환 된 값을 지정 합니다. 일반 형식은 다음과 같습니다.  
  
```js
  
return [ expression ];  
```  
  
 경우는 `return` 문이 실행 될 *식* 평가 되 고 함수의 값으로 반환 합니다. 식이 없는 경우 **정의 되지 않은** 반환 됩니다.  
  
 함수 실행이 중단 될 때를 `return` 함수 본문에 계속 남아 있는 다른 문의 경우에 문이 실행 됩니다. 이 규칙의 예외는 경우는 **반환** 문 내에서 발생을 **시도** 블록 및 해당 **마지막** 블록, 코드는  **마지막으로** 블록 함수가 반환 되기 전에 실행 됩니다.  
  
 함수를 실행 하지 않고도 함수 본문의 끝에 도달 하기 때문에 반환 하는 경우는 `return` 문에서 반환 되는 값을 **정의 되지 않은** 값 (즉, 더 큰 수식의 일부로 함수 결과 사용할 수 없습니다 ).  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 제거 된 `return` 문 본문의 코드 (전역 범위).  
  
## <a name="see-also"></a>참고 항목  
 [return 문](../../javascript/reference/return-statement-javascript.md)   
 [함수 개체](../../javascript/reference/function-object-javascript.md)   
 [caller 속성(Function)](../../javascript/reference/caller-property-function-javascript.md)