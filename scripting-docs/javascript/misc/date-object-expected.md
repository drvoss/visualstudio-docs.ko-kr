---
title: Date 개체가 필요 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05e27b822f933ade811084552f6f0379257ae82e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947643"
---
# <a name="date-object-expected"></a>Date 개체가 필요합니다.
호출 하려고 합니다 **Date.prototype.toString** 또는 **Date.prototype.valueOf** 이외의 다른 형식의 개체의 메서드를 `Date`입니다. 이 형식의 호출 개체 유형 이어야 `Date`합니다. 예를 들어:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
-   만 호출 합니다 **Date.prototype.toString** 또는 **Date.prototype.valueOf** 형식의 개체에 있는 메서드의 `Date`합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Date 개체](../../javascript/reference/date-object-javascript.md)   
 [getDate 메서드 (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [내장 개체](../../javascript/intrinsic-objects-javascript.md)