---
title: 예기치 않은 수량자 (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52b98875b560e4863a93849cf99c2f8756cd438a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005893"
---
# <a name="unexpected-quantifier-javascript"></a>예기치 않은 수량자입니다.(JavaScript)
정규식 검색 패턴을 작성할 때 잘못 된 반복 요소를 사용 하 여 패턴 요소를 만들었습니다. 예를 들어, 패턴  
  
```js
/^+/  
```  
  
 유효 하지 않은 때문에 요소 ^ (입력의 시작 부분) 반복 인수를 사용할 수 없습니다. 다음 표에서 반복 요소를 가질 수 없는 요소를 나열 합니다.  
  
|요소|설명|  
|-------------|-----------------|  
|^|입력의 시작|  
|$|입력의 끝|  
|\b|단어 경계|  
|\B|비단어 경계|  
|*|0 개 이상의 반복|  
|+|하나 이상의 반복|  
|?|0 개 이상의 반복|  
|{n}|n 반복|  
|{n}|n 또는 반복 횟수가|  
|{n, m}|N-m 반복을 포함|  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 검색 패턴 요소 포함 법적 반복 요소에만 확인 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Regular Expression 개체](../../javascript/reference/regular-expression-object-javascript.md)   
 [정규식 구문 (JavaScript)](https://msdn.microsoft.com/library/1400241x)