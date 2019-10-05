---
title: 주석이 종결 되지 않았습니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bf7c570c832fb5db5489a2a9f9bec459f26f0a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005957"
---
# <a name="unterminated-comment"></a>종결되지 않은 주석입니다.
여러 줄의 주석 블록을 시작 해도 제대로 종료 되지 않았습니다. 여러 줄 주석을로 시작는 "/\*" 조합과로 끝나야 "\*/" 조합 합니다. 예를 들면 다음과 같습니다.  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 여러 줄의 주석을 종결 합니다 "*/"입니다.  
  
## <a name="see-also"></a>참고 항목  
 [Comment 문](../../javascript/reference/comment-statements-javascript.md)