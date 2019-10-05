---
title: Date 개체가 필요 합니다. | Microsoft Docs
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
ms.openlocfilehash: 2767ffc16b637c6b1e7bdf51cb0815d71f58edac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946383"
---
# <a name="date-object-expected"></a>Date 개체가 필요합니다.
호출 하려고 합니다 **Date.prototype.toString** 또는 **Date.prototype.valueOf** 이외의 다른 형식의 개체의 메서드를 `Date`입니다. 이 형식의 호출 개체 유형 이어야 `Date`합니다. 예를 들어:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 만 호출 합니다 **Date.prototype.toString** 또는 **Date.prototype.valueOf** 형식의 개체에 있는 메서드의 `Date`합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Date 개체](../../javascript/reference/date-object-javascript.md)   
 [getDate 메서드 (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [내장 개체](../../javascript/intrinsic-objects-javascript.md)