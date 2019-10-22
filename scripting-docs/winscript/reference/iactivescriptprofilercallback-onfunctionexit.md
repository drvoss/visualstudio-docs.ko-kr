---
title: 'IActiveScriptProfilerCallback:: OnFunctionExit | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionExit
apilocation:
- scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87801b7873e43498031264ff4719fb47eca99f40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571675"
---
# <a name="iactivescriptprofilercallbackonfunctionexit"></a>IActiveScriptProfilerCallback::OnFunctionExit
스크립팅 엔진이 DOM (문서 개체 모델)에 대 한 호출이 아닌 함수 호출의 실행을 완료 했음을 프로파일러 개체에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `scriptId`  
 진행 함수가 포함 된 스크립트의 고유 ID입니다. 이 ID는 스크립팅 엔진에서 할당 합니다.  
  
 `functionId`  
 진행 함수의 고유 ID입니다. 이 ID는 스크립팅 엔진에서 할당 합니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드의 반환 값은 스크립팅 엔진에서 무시 됩니다.  
  
## <a name="remarks"></a>주의  
 DOM 호출의 경우 스크립팅 엔진은 `IActiveScriptProfilerCallback::OnFunctionExit` 대신 [IActiveScriptProfilerCallback2:: OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) 를 호출 합니다. 이는 DOM에서 많은 수의 고유한 메서드와 속성 때문입니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptProfilerCallback:: OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)    
 [IActiveScriptProfilerCallback 인터페이스](../../winscript/reference/iactivescriptprofilercallback-interface.md)