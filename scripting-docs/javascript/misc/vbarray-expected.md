---
title: VBArray가 필요 | Microsoft 문서
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d1fabd8da6f825a266614a4a5c7fabd5c307130
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005994"
---
# <a name="vbarray-expected"></a>VBArray가 필요합니다.
필요한 Visual Basic safeArray에 없는 개체를 제공 했습니다.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays는 읽기 전용이므로 직접 만들 수 없습니다. SafeArray 인수를 VBArray 값 및 얻어야 합니다 VBArray 값에 전달 되기 전에 `VBArray` 생성자입니다. 이 작업은 기존 ActiveX 또는 다른 개체에서 값을 검색하는 방식으로만 수행할 수 있습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 만 전달 해야 **VBArray** 개체를 **VBArray** 생성자입니다.  
  
## <a name="see-also"></a>참고 항목  
 [VBArray 개체](../../javascript/reference/vbarray-object-javascript.md)   
 [배열 사용](../../javascript/advanced/using-arrays-javascript.md)