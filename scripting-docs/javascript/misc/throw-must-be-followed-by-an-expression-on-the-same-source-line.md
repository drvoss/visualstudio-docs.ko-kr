---
title: 같은 소스 줄에서 Throw 뒤에는 식이와 야 합니다. Microsoft Docs
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
ms.openlocfilehash: 8854acb3d1992283899c4ff095f5d754c05f55a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572755"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>같은 소스 줄에서 throw 뒤에는 식이 와야 합니다.
@No__t_0 키워드를 사용 했지만 동일한 소스 줄에서 식과 함께 사용 하지 않았습니다. @No__t_0 문은 `throw` 키워드와 throw 될 식의 두 부분으로 구성 됩니다. 예를 들면,  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 이러한 두 구성 요소는 분할할 수 없습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- Throw 할 `throw` 키워드와 식이 같은 줄에 표시 되는지 확인 합니다.  
  
## <a name="see-also"></a>참조  
 [오류 개체](../../javascript/reference/error-object-javascript.md)    
 [Throw 문](../../javascript/reference/throw-statement-javascript.md)    
 [try...catch...finally 문](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)