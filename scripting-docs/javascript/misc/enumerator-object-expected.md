---
title: 열거자 개체가 필요 합니다. | Microsoft Docs
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
ms.openlocfilehash: d90b6b923f631c7785428a1b3879528e97c1bfd6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572870"
---
# <a name="enumerator-object-expected"></a>Enumerator 개체가 필요합니다.
@No__t_2 아닌 형식의 개체에 대해 **enumerator. atEnd, enumerator** . Prototype. MoveFirst 또는 **enumerator** 메서드를 호출 하려고 한 경우 .이 메서드는. 이 호출 형식의 개체는 `Enumerator` 형식 이어야 합니다. 다음은이 규칙을 위반 하는 코드의 예입니다.  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- @No__t_4 형식의 개체에 대 **한 열거자.** **prototype.** **. i** **a. a**. i. i. i. 개체가 `Enumerator` 개체 인지 확인 하려면 다음을 사용 합니다.  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>참조  
 [Enumerator 개체](../../javascript/reference/enumerator-object-javascript.md)