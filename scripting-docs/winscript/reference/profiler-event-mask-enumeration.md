---
title: PROFILER_EVENT_MASK 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_EVENT_MASK
apilocation:
- scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7230e65e5559d53e56cf6424a34dd44aa4edda7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831644"
---
# <a name="profilereventmask-enumeration"></a>PROFILER_EVENT_MASK 열거형
프로 파일링 해야 하는 이벤트의 형식을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|사용자가 작성 한 스크립트 및 동적 코드에 정의 된 프로필 함수입니다.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|스크립팅 엔진에 의해 정의 된 네이티브 함수 프로필입니다.|  
|PROFILER_EVENT_MASK_TRACE_ALL|문서 개체 모델 (DOM)로 호출을 제외한 모든 사용자 정의 및 스크립팅 엔진 함수에 프로필을 만듭니다.|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Dom을 호출 하는 프로필 함수|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Dom에 대 한 호출을 비롯 한 모든 함수를 프로필|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 Profiler 상수, 열거형 및 구조체](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)