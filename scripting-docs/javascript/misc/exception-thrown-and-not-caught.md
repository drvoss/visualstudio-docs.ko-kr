---
title: 예외가 throw 잡히지 | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bae4ed0a335a9c12d16cb46208f77c4b66f12547
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946331"
---
# <a name="exception-thrown-and-not-caught"></a>예외가 throw되고 catch되지 않았습니다.
포함 하는 `throw` 하지만 코드에서 문 내에 포함 되지를 **시도** 블록 하거나 연결 된 **catch** 오류를 트래핑 하는 블록. 내에서 예외가 throw 됩니다는 **시도** 사용을 차단 합니다 **throw** 문을 외부 포착 하 고는 **시도** 블록을 **catch** 문입니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 예외를 throw 할 수 있는 코드를 묶습니다를 **시도** 블록 및 해당 보장 **catch** 블록입니다.  
  
- Catch 문의 올바른 형식의 예외를 예상 해야 합니다.  
  
- 예외 다시 throw 되는 경우 해당 catch 문을 다른 인지 확인 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Error 개체](../../javascript/reference/error-object-javascript.md)   
 [Throw 문](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally 문](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)