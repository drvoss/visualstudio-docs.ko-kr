---
title: 'IActiveScriptProfilerControl:: SetProfilerEventMask | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.SetProfilerEventMask
apilocation:
- scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4162cf2e5325bfb41bce9c3a47a52b1b36d74f2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571583"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
스크립팅 엔진에서 발생 해야 하는 이벤트 유형을 지정 하는 4 바이트 비트 마스크를 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwEventMask`  
 진행 이벤트 유형을 지정 하는 4 바이트 비트 마스크입니다. 비트는 [PROFILER_EVENT_MASK 열거형](../../winscript/reference/profiler-event-mask-enumeration.md)에 정의 되어 있습니다.  
  
## <a name="return-value"></a>반환 값  
 HRESULT를 반환 합니다. 다음과 같은 값을 사용할 수 있습니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|메서드가 성공했으며|  
|`ACTIVPROF_E_PROFILER_ABSENT`|프로 파일링이 사용 하도록 설정 되어 있지 않습니다.|  
  
## <a name="see-also"></a>참조  
 [IActiveScriptProfilerControl 인터페이스](../../winscript/reference/iactivescriptprofilercontrol-interface.md)