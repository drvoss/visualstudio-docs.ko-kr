---
title: 'IDebugCodeContext:: SetBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCodeContext.SetBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugCodeContext::SetBreakPoint
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df2bb0395cc1aeaceda3763b2c4016bbd9ba7e1f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573214"
---
# <a name="idebugcodecontextsetbreakpoint"></a>IDebugCodeContext::SetBreakPoint
이 코드 컨텍스트에서 중단점을 설정 하거나 해제 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `bps`  
 진행 이 코드 컨텍스트의 중단점 상태를 지정 합니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는이 코드 컨텍스트에서 중단점을 설정 하거나 해제 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugCodeContext 인터페이스](../../winscript/reference/idebugcodecontext-interface.md)   
 [BREAKPOINT_STATE 열거형](../../winscript/reference/breakpoint-state-enumeration.md)