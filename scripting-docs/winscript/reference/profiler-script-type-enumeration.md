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
ms.openlocfilehash: e08583f9bb914adfbd144715646991c6070f3f32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574580"
---
# <a name="profiler_script_type-enumeration"></a>PROFILER_SCRIPT_TYPE 열거형
스크립트의 유형을 지정 합니다.  
  
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
|PROFILER_SCRIPT_TYPE_USER|사용자가 작성 한 스크립트 코드를 지정 합니다.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|실행 중에 동적으로 생성 되는 스크립트 코드를 지정 합니다.|  
|PROFILER_SCRIPT_TYPE_NATIVE|스크립팅 엔진에서 정의 하는 개체와 네이티브 함수에 대 한 스크립트 유형을 지정 합니다.|  
|PROFILER_SCRIPT_TYPE_DOM|Internet Explorer의 문서 개체 모델 (DOM) 호출을 지정 합니다. 예를 들어 `document.getElementById` 메서드를 호출 합니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 프로파일러 상수, 열거형 및 구조체](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)    
 [IActiveScriptProfilerCallback:: ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)    
 [IActiveScriptProfilerCallback2:: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)    
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)