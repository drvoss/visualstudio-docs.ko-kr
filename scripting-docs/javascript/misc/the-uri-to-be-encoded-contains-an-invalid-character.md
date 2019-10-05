---
title: 인코딩할 URI에 잘못 된 문자가 | Microsoft 문서
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2f9111acf656bf882a3d506fe95b8361f3693ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006210"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>인코딩할 URI에 잘못된 문자가 들어 있습니다.
문자열로 URI (일정 한 리소스 식별자)로 인코딩 하려고 하지만 잘못 된 문자가 포함 되어 있어. 대부분의 문자는 Uri로 변환 된 문자열 내에 유효한, 일부 유니코드 문자 시퀀스를 사용할 수 없습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 인코딩될 문자열에 올바른 유니코드 문자열만 있는지 확인 합니다. 완전 한 URI 구성 요소 및 구분 기호 구성 됩니다. 꺾쇠 괄호의 이름은 구성 요소를 나타내며와 ":", "/", ";" 및 "?" 예약 된 문자를 구분 기호로 사용 됩니다. 일반 형식은 다음과 같습니다.  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [encodeURI 함수](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent 함수](../../javascript/reference/encodeuricomponent-function-javascript.md)