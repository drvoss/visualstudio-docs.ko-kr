---
title: 'IDebugApplication:: RemoveStackFrameSniffer | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveStackFrameSniffer
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 605daf51214ba5af9d6010b28be9569453ca7962
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571120"
---
# <a name="idebugapplicationremovestackframesniffer"></a>IDebugApplication::RemoveStackFrameSniffer
이 응용 프로그램에서 스택 프레임 열거자 공급자를 제거 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwCookie`  
 진행 스택 프레임 열거자 공급자를 추가할 때 `AddStackFrameSniffer` 메서드에서 반환 되는 쿠키입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 @No__t_0 메서드는이 응용 프로그램에서 스택 프레임 열거자 공급자를 제거 합니다.  
  
## <a name="see-also"></a>참조  
 [Idebugapplication:: AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)    
 [Idebugapplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)    
 [IDebugStackFrameSniffer 인터페이스](../../winscript/reference/idebugstackframesniffer-interface.md)