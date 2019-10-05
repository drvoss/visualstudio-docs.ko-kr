---
title: PROFILER_SCRIPT_TYPE 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca90a566db422d75fefc44267ffe10504bb872ce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816787"
---
# <a name="profilerscripttype-enumeration"></a>PROFILER_SCRIPT_TYPE 열거형
스크립트의 유형을 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|사용자가 작성 한 스크립트 코드를 지정합니다.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|실행 하는 동안 동적으로 생성 되는 스크립트 코드를 지정 합니다.|  
|PROFILER_SCRIPT_TYPE_NATIVE|네이티브 함수 및 스크립트 엔진에 의해 정의 된 개체에 대 한 스크립트 유형을 지정 합니다.|  
|PROFILER_SCRIPT_TYPE_DOM|호출에는 개체 모델 DOM (문서)에 대 한 호출 예를 들어, Internet Explorer의 지정 된 `document.getElementById` 메서드.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 Profiler 상수, 열거형 및 구조체](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)