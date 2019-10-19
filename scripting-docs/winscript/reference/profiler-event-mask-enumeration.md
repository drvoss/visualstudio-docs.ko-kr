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
ms.openlocfilehash: c1e1e7f3b604832014cb23245b105756d1126c5b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572287"
---
# <a name="profiler_event_mask-enumeration"></a>PROFILER_EVENT_MASK 열거형
프로 파일링 해야 하는 이벤트 유형을 나타냅니다.  
  
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
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|사용자가 작성 한 스크립트와 동적 코드에 정의 된 함수를 프로 파일링 합니다.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|스크립팅 엔진에서 정의 되는 네이티브 함수를 프로 파일링 합니다.|  
|PROFILER_EVENT_MASK_TRACE_ALL|문서 개체 모델 (DOM) 호출을 제외 하 고 모든 사용자 정의 및 스크립팅 엔진 함수를 프로 파일링 합니다.|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|DOM을 호출 하는 함수를 프로 파일링 합니다.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|DOM에 대 한 호출을 포함 하 여 모든 함수를 프로 파일링 합니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 프로파일러 상수, 열거형 및 구조체](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)    
 [IActiveScriptProfilerControl:: SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)    
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)