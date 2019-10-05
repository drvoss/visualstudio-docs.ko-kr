---
title: Throw 따라야 식에서 같은 소스 줄에서 | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c8ed951fb30b84f114f8f44a60e94b88f0f1d0f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005943"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>같은 소스 줄에서 throw 뒤에는 식이 와야 합니다.
사용 된 `throw` 키워드를 따르지이 식을 사용 하 여 같은 소스 줄에 있지만. A `throw` 문의 두 부분으로 이루어져:는 `throw` throw 식 뒤에 키워드를 합니다. 예를 들어:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 이러한 두 구성 요소 분할할 수 없습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 확인을 `throw` 키워드와 throw 식 동일한 줄에 나타납니다.  
  
## <a name="see-also"></a>참고 항목  
 [Error 개체](../../javascript/reference/error-object-javascript.md)   
 [Throw 문](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally 문](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)