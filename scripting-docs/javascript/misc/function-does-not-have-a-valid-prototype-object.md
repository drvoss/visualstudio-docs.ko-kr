---
title: 함수에 유효한 프로토타입 개체가 없습니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 413f73a53a6d4f698219139a87c449be4c155831
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007505"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>함수에 올바른 프로토타입 개체가 없습니다.
사용 하려는 **instanceof** 개체는 특정 함수 클래스에서 파생 된 개체를 다시 정의 되지만 결정할 `prototype` 속성으로 `null`, 또는 외부 개체 형식 (모두 유효 하지 않습니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 개체). 외부 개체 (예를 들어, Internet Explorer의 문서 또는 창 개체)에서 호스트 개체 모델에서 개체 또는 외부 COM 개체 수 있습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 함수를 확인 하십시오 `prototype` 속성은 유효한 참조 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 개체입니다.  
  
## <a name="see-also"></a>참고 항목  
 [함수 개체](../../javascript/reference/function-object-javascript.md)   
 [prototype 속성(Object)](../../javascript/reference/prototype-property-object-javascript.md)