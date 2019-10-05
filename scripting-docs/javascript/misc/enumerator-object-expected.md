---
title: Enumerator 개체가 필요 | Microsoft 문서
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06005f635e5173e903cfba6a952750d64181d0bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946344"
---
# <a name="enumerator-object-expected"></a>Enumerator 개체가 필요합니다.
호출 하려고 합니다 **Enumerator.prototype.atEnd, Enumerator.prototype.item Enumerator.prototype.moveFirst를** 또는 **Enumerator.prototype.moveNext** 형식의 다른 개체에서 메서드 보다 `Enumerator`합니다. 이 형식의 호출 개체 유형 이어야 `Enumerator`합니다. 이 규칙을 중단 하는 코드의 예는 다음과 같습니다.  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 만 호출 합니다 **Enumerator.prototype.atEnd**, **Enumerator.prototype.item**합니다 **Enumerator.prototype.moveFirst**, 또는  **Enumerator.prototype.moveNext** 형식의 개체에 있는 메서드의 `Enumerator`합니다. 개체가 있는지 확인 하려면를 `Enumerator` 개체를 사용 합니다.  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [Enumerator 개체](../../javascript/reference/enumerator-object-javascript.md)