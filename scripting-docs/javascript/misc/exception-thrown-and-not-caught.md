---
title: 예외가 발생 하 여 catch 하지 않음 | Microsoft Docs
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
ms.openlocfilehash: 05a9e4f51d5daf7a9e1b1153acbbe8b76b539b72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572861"
---
# <a name="exception-thrown-and-not-caught"></a>예외가 throw되고 catch되지 않았습니다.
코드에 `throw` 문을 포함 했지만 **try** 블록 내에 포함 되지 않았거나 오류를 트랩할 연결 된 **catch** 블록이 없습니다. 예외는 **throw** 문을 사용 하 여 **try** 블록 내에서 throw 되 고 **catch** 문을 사용 하 여 **try** 블록 외부에서 catch 됩니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- **Try** 블록에서 예외를 throw 할 수 있는 코드를 묶고 해당 하는 **catch** 블록이 있는지 확인 합니다.  
  
- Catch 문이 올바른 형식의 예외를 예상 하는지 확인 합니다.  
  
- 예외가 다시 throw 되는 경우 다른 해당 catch 문이 있는지 확인 합니다.  
  
## <a name="see-also"></a>참조  
 [오류 개체](../../javascript/reference/error-object-javascript.md)    
 [Throw 문](../../javascript/reference/throw-statement-javascript.md)    
 [try...catch...finally 문](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)