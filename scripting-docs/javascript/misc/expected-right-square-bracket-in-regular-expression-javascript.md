---
title: 정규식에 '] '가 필요 합니다. (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9af38a5fa754a811416f1a998b90946345f3e4a2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576487"
---
# <a name="expected--in-regular-expression-javascript"></a>정규식에 ']'가 필요합니다.(JavaScript)
정규식 일치 항목에 대 한 문자 클래스를 만들려고 했지만 오른쪽 대괄호가 포함 되지 않았습니다. 개별 리터럴 문자 조합을 문자 클래스로 조합 하 여 대괄호 안에 배치할 수 있습니다. 문자 클래스는 포함 하는 문자 하나를 찾습니다. 예를 들어/[abc]/는 문자 "a", "b" 또는 "c" 중 하나를 찾습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 정규식에 오른쪽 괄호를 추가 합니다.  
  
    > [!NOTE]
    > 대괄호 하나를 일치 시키려는 경우에는 백슬래시-\\ [-로 이스케이프 합니다. 따라서 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]는 특수 문자로 해석 되지 않습니다.  
  
## <a name="see-also"></a>참조  
 [Regular Expression 개체](../../javascript/reference/regular-expression-object-javascript.md)    
 [정규식 구문 (JavaScript)](https://msdn.microsoft.com/library/1400241x)