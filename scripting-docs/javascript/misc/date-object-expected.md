---
title: 날짜 개체가 필요 합니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10af48c4804df3b5513df71578b948abe73ff8c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572891"
---
# <a name="date-object-expected"></a>Date 개체가 필요합니다.
`Date`이외의 형식의 개체에 대해 **date. prototype** 또는 **valueOf** 메서드를 호출 하려고 했습니다. 이 호출 형식의 개체는 `Date`형식 이어야 합니다. 예를 들면 다음과 같습니다.  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- `Date`형식의 개체에 대해서만 **valueOf** **메서드를 호출 합니다.**  
  
## <a name="see-also"></a>참고 항목  
 [Date 개체](../../javascript/reference/date-object-javascript.md)   
 [GetDate 메서드 (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [내장 개체](../../javascript/intrinsic-objects-javascript.md)