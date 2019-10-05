---
title: 예상된 진수 | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82f020b5f3b82ab2ce3545102be83a5cd41c6069
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446516"
---
# <a name="expected-hexadecimal-digit"></a>16진수가 필요합니다.
잘못 된 유니코드 이스케이프 시퀀스를 만들었습니다. 유니코드 이스케이프 시퀀스 \u, 정확히 4 자리 16 진수 (더 이상 및 적지 않은) 다음으로 시작 합니다. 유니코드 16 진수는 숫자 0-9만, 대문자 문자 A-f를 소문자 문자 a-f를 포함할 수 있습니다. 다음 예제에는 올바른된 유니코드 이스케이프 시퀀스를 보여 줍니다.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 유니코드 진수 \u 시작, 숫자 0-9, A-f 소문자 문자 a-f; 대문자 문자를 포함 해야 4 자리에 그룹화 됩니다.  
  
    > [!NOTE]
    > 문자열에서 리터럴 텍스트 \u를 사용 하 여 다음 두 개의 백슬래시-사용 하려는 경우 (\\\u)-첫 번째 백슬래시를 이스케이프 하 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 형식](../../javascript/data-types-javascript.md)