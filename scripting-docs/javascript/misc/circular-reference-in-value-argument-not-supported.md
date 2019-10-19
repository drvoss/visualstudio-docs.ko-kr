---
title: 값 인수의 순환 참조가 지원 되지 않습니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 542fca58778a7b85b3044ce984b6ea049db12509
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572340"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>값 인수에 순환 참조를 사용하는 것은 지원되지 않습니다.
잘못 된 값을 사용 하 여 `JSON.stringify`를 호출 하려고 한 경우 @No__t_0 인수인 배열 또는 개체는 순환 참조를 포함 합니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 인수에서 순환 참조를 제거 합니다.  
  
## <a name="example"></a>예제  
 이 예제의 코드는 `john` `mary`에 대 한 참조를 포함 하 고 `mary` `john`에 대 한 참조를 포함 하기 때문에 런타임 오류가 발생 합니다. 순환 참조를 제거 하려면 `mary` 개체 또는 `john` 개체에서 `sister` 속성 `brother` 속성을 제거 하거나 설정 해제 합니다.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>참조  
 [JSON 개체](../../javascript/reference/json-object-javascript.md)    
 [JSON   함수를 구문 분석 합니다.](../../javascript/reference/json-parse-function-javascript.md)  
 [JavaScript 런타임 오류](../../javascript/reference/javascript-run-time-errors.md)