---
title: 조건부 컴파일이 꺼져 있습니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56621d6f7fcc195a4ece7654adeafd1096c37e8b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572937"
---
# <a name="conditional-compilation-is-turned-off"></a>조건부 컴파일이 해제되었습니다.
먼저 조건부 컴파일을 설정 하지 않고 조건부 컴파일 변수를 사용 하려고 했습니다. 조건부 컴파일을 사용 하도록 설정 하면 @로 시작 하는 식별자를 조건부 컴파일 변수로 해석 하도록 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 컴파일러에 지시 합니다. 이렇게 하려면 다음과 같이 문을 사용 하 여 조건부 코드를 시작 합니다.  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 조건부 코드의 시작 부분에 다음 문을 추가 합니다.  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>참조  
 [조건부 컴파일](../../javascript/advanced/conditional-compilation-javascript.md)    
 [조건부 컴파일 변수](../../javascript/advanced/conditional-compilation-variables-javascript.md)    
 [@cc_on 문](../../javascript/reference/at-cc-on-statement-javascript.md)    
 [@if 문](../../javascript/reference/at-if-statement-javascript.md)    
 [@set 문](../../javascript/reference/at-set-statement-javascript.md)