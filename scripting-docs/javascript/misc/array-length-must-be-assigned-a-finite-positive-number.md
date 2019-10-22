---
title: 배열 길이는 유한한 양수로 할당 해야 합니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cff9c8c42199e106cca5f6f2808866e46a26afe2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576075"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>배열의 길이는 유한한 양수로 할당해야 합니다.
기존 **배열** 개체의 **length** 속성을 설정할 때 양수 또는 0이 아닌 배열 길이를 지정 했습니다. 음수 이거나 숫자가 아닌 `Array` 개체의 **length** 속성에 값을 할당 하는 경우이 오류가 발생 합니다 (`NaN`). @No__t_0은 자동으로 소수 자릿수를 정수로 변환 합니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- Length 속성에 양의 정수를 할당 합니다. 최대 정수 값 (약 40억)이 아닌 배열의 크기에 대 한 상한이 없습니다. 다음 예제에서는 **배열** 개체의 **length** 속성을 설정 하는 올바른 방법을 보여 줍니다.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>참조  
 [배열 사용](../../javascript/advanced/using-arrays-javascript.md)