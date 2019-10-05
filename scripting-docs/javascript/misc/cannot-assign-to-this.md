---
title: "'This'에 할당할 수 없습니다 | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a4ba5d852a7d131a88930dd66931c026074549b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946591"
---
# <a name="cannot-assign-to-this"></a>'this'에 할당할 수 없습니다.
값을 할당 하려고 **이**합니다. **이렇게** 되는 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 키워드 중 하나를 참조 하는:

- 현재 메서드 실행, 개체

- 현재 메서드가 없는 (또는 메서드가 다른 개체에 속해 있지 않으므로) 하는 경우 전역 개체입니다.

메서드는을 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 개체를 통해 호출 되는 함수입니다. 메서드 내에서 **이** 키워드는 메서드를 통해 호출 된 개체에 대 한 참조 (사용 하 여 클래스 생성자를 호출 하 여 생성 된 개체에 **새** 연산자).

메서드 내에서 사용할 수 있습니다 **이렇게** 있지만 현재 개체를 가리키도록 새 값을 할당할 수 없습니다 **이**합니다.

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 에 할당 하지 마세요 **이**합니다. 인스턴스화된 개체의 메서드나 속성에 액세스 하려면 점 연산자를 사용 하 여 (예를 들어 **circle.radius**).

  > [!NOTE]
  > 사용자가 만든 변수 이름을 지정할 수 없습니다 **이**; 것을 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 예약어입니다.

## <a name="see-also"></a>참고 항목

- [this 문](../../javascript/reference/this-statement-javascript.md)
- [스크립트 문제 해결](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)