---
title: 예상 ')' 정규식 (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7daf5d876f68168ce0b58ea2cc9b52a309107bc6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446539"
---
# <a name="expected--in-regular-expression-javascript"></a>정규식에 ')'가 필요합니다.(JavaScript)
정규식 캡처, 어설션 또는 그룹을 만들려고 시도 했음 해도 닫는 괄호를 포함 하지 않았습니다. 괄호는 정규식의 몇 가지 목적이 있습니다. 주로 사용 되는 하위 식에서 어설션을 지정 하거나 항목으로 하나의 단위로 처리할 수 있도록 패턴을 그룹화 하려면 캡처 *, +,? 등입니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 오른쪽에 있는 닫는 괄호를 추가 합니다.  
  
    > [!NOTE]
    > 단일 괄호 일치 하도록 하려는 경우-백슬래시로 이스케이프 \\(에서 특수 문자로 해석 되지 않습니다 있도록- [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Regular Expression 개체](../../javascript/reference/regular-expression-object-javascript.md)   
 [정규식 구문 (JavaScript)](https://msdn.microsoft.com/library/1400241x)