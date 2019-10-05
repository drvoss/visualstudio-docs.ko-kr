---
title: 루프 외부에서 '중단'를 사용할 수 없습니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a02848230187eb465d56ed73e44380e4b043b117
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946630"
---
# <a name="cant-have-break-outside-of-loop"></a>루프 외부에서 'break'를 사용할 수 없습니다.
사용 하려고 합니다 **중단** 루프 외부에서 키워드입니다. 합니다 **나누기** 키워드는 루프를 종료 하는 데 사용 됩니다 또는 `switch` 문입니다. 루프의 본문에 포함 되어 있어야 합니다 또는 `switch` 문입니다. 그러나를 **레이블** break 키워드 다음에 올 수 있습니다.  
  
```js
break labelname;  
```  
  
 레이블이 지정 된 형식의 하기만 하면 합니다 **나누기** 키워드를 사용 하는 경우 중첩 루프 또는 `switch` 문과 없는 가장 안쪽의 루프를 중단 해야 합니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 있는지 확인 합니다 **중단** 키워드는 바깥쪽 루프 또는 switch 문 내부에 표시 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [break 문](../../javascript/reference/break-statement-javascript.md)   
 [프로그램 흐름 제어](../../javascript/controlling-program-flow-javascript.md)   
 [스크립트 문제 해결](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)