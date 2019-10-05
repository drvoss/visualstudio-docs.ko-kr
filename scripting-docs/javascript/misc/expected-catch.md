---
title: "'Catch' 필요 | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 941d49a530b14e2af64ddcb599dd775feb347de0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935401"
---
# <a name="expected-catch"></a>'catch'가 필요합니다.
예외 처리를 사용 **시도** 차단 하지만 연결 된 작성 하지 않은 **catch** 문입니다. 예외 처리 메커니즘 내에 있어야는 예외가 발생할 경우 실행 되지 않도록 하는 코드와 함께 실패할 수 있는 코드를 **시도** 블록입니다. 내에서 예외가 throw 됩니다는 **시도** 사용을 차단 합니다 **throw** 문 외부 포착 하 고는 **시도** 하나를 사용 하 여 블록 **catch**문입니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 연결 된 추가 **catch** 블록입니다.  
  
- 사용해를 **finally** 블록 대신를 **catch** 블록입니다.  
  
## <a name="see-also"></a>참고 항목  
 [try... catch 마지막 문...](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error 개체](../../javascript/reference/error-object-javascript.md)