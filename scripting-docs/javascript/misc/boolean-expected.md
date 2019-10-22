---
title: 부울이 필요 합니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91ff0ec8cbd6e5cedb5ec02a8c574ff137b1c6ad
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576053"
---
# <a name="boolean-expected"></a>부울이 필요합니다.
@No__t_2이 아닌 형식의 개체에 대해 **valueOf** **메서드를 호출** 하려고 한 경우입니다. 이 호출 형식의 개체는 `Boolean` 형식 이어야 합니다. 예를 들면,

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- **부울** 형식의 개체에 대해서만 **valueOf** **메서드를 호출 합니다.**

## <a name="see-also"></a>참조

- [Boolean 개체](../../javascript/reference/boolean-object-javascript.md)
- [데이터 형식](../../javascript/data-types-javascript.md)
- [프로그램 흐름 제어](../../javascript/controlling-program-flow-javascript.md)
- [데이터 복사, 전달 및 비교](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)