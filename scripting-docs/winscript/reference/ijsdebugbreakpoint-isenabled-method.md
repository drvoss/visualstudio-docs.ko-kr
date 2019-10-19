---
title: 'IJsDebugBreakPoint:: IsEnabled 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.IsEnabled
apilocation:
- jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25d66b7f8691a74eac77e9a90ec610fa21ec688e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577664"
---
# <a name="ijsdebugbreakpointisenabled-method"></a>IJsDebugBreakPoint::IsEnabled 메서드
중단점을 사용할 수 있는지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pIsEnabled`  
 제한이 중단점을 사용할 수 있으면 true를 반환 하 고, 그렇지 않으면 false를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 삭제 된 중단점에서 호출 된 경우 E_UNEXPECTED를 반환 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugBreakPoint 인터페이스](../../winscript/reference/ijsdebugbreakpoint-interface.md)