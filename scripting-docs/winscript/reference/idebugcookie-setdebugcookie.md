---
title: 'IDebugCookie:: SetDebugCookie | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCookie.SetDebugCookie
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugCookie::SetDebugCookie
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 664939d0b91b8dbbf87dbff2978064811ffee486
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573178"
---
# <a name="idebugcookiesetdebugcookie"></a>IDebugCookie::SetDebugCookie
디버그 응용 프로그램 쿠키를 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwDebugAppCookie`  
 진행 디버그 응용 프로그램을 식별 하는 쿠키입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 여러 디버거를 프로세스에 연결할 수 있도록 하는 디버그 응용 프로그램 쿠키를 설정 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugCookie 인터페이스](../../winscript/reference/idebugcookie-interface.md)