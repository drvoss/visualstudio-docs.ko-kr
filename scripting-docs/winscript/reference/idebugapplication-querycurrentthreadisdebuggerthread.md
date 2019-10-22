---
title: 'IDebugApplication:: QueryCurrentThreadIsDebuggerThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.QueryCurrentThreadIsDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::QueryCurrentThreadIsDebuggerThread
ms.assetid: e22ad8a4-a8be-423d-80f2-28256a7448ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f70cde752506919d90bf963d010ebfc7abf5e88
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577209"
---
# <a name="idebugapplicationquerycurrentthreadisdebuggerthread"></a>IDebugApplication::QueryCurrentThreadIsDebuggerThread
현재 실행 중인 스레드가 디버거 스레드 인지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT QueryCurrentThreadIsDebuggerThread();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|성공한 메서드 및 현재 실행 중인 스레드는 디버거 스레드입니다.|  
|`S_FALSE`|현재 실행 중인 스레드는 디버거 스레드가 아닙니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 현재 실행 중인 스레드가 디버거 스레드 인지 여부를 확인 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)