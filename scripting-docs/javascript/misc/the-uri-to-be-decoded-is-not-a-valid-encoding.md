---
title: 디코딩할 URI가 올바른 인코딩이 아닙니다 | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fd8add72d016bc3f2e815f41c29c735505c8817
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006223"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>디코딩할 URI가 올바른 인코딩이 아닙니다.
형식이 잘못 된 URI (Uniform Resource Identifier)를 디코딩 하려고 했습니다. Uri에는 특수 구문이; URI에서 사용할 수 전에 대부분의 영숫자가 아닌 문자를 인코딩해야 합니다. 사용할 수는 `encodeURI` 하 고 `encodeURIComponent` 에서 보통 URI를 만드는 방법 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 문자열입니다.  
  
 완전 한 URI 구성 요소 및 구분 기호 구성 됩니다. 일반 형식은 다음과 같습니다.  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 꺾쇠 괄호의 이름은 구성 요소를 나타내며와 ":", "/", ";" 및 "?" 예약 된 문자를 구분 기호로 사용 됩니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 유효한 Uri만 디코딩 하려는 것을 확인 합니다. 일반을 디코딩할 수 없습니다. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 문자열에 잘못 된 문자가 포함 되어 있을 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [decodeURI 함수](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent 함수](../../javascript/reference/decodeuricomponent-function-javascript.md)