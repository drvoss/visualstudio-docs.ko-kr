---
title: IJsDebugBreakPoint::D i) 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.Disable
apilocation:
- jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51e4be2abc8b5a507e091b330de1779cfb14b57e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577730"
---
# <a name="ijsdebugbreakpointdisable-method"></a>IJsDebugBreakPoint::Disable 메서드
중단점을 사용 하지 않도록 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Disable(void);  
```  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 삭제 된 중단점에서 호출 된 경우 E_UNEXPECTED를 반환 합니다. 이미 사용 하지 않도록 설정 된 중단점에서 호출 되는 경우 S_FALSE를 반환 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugBreakPoint 인터페이스](../../winscript/reference/ijsdebugbreakpoint-interface.md)