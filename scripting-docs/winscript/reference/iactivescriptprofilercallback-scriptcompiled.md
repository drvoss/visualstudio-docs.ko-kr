---
title: 'IActiveScriptProfilerCallback:: ScriptCompiled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.ScriptCompiled
apilocation:
- scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7252134fc86bfd63b74a181b18327212a1b2dc1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571666"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
스크립팅 엔진이 스크립트를 컴파일 했음을 프로파일러 개체에 알립니다. 이 메서드는 컴파일되는 모든 스크립트에 대해 호출 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `scriptId`  
 진행 컴파일된 스크립트의 고유 ID입니다. 이 ID는 스크립팅 엔진에서 할당 합니다.  
  
 `type`  
 진행 컴파일되는 스크립트의 형식입니다. 값은 [PROFILER_SCRIPT_TYPE 열거형](../../winscript/reference/profiler-script-type-enumeration.md)에 정의 되어 있습니다.  
  
 `pIDebugDocumentContext`  
 진행 사용 가능한 경우 프로파일러가 [Idebugdocumentcontext 인터페이스](../../winscript/reference/idebugdocumentcontext-interface.md) 포인터를 쿼리해야 하는 `IUnknown` 인터페이스에 대 한 포인터입니다. 그렇지 않으면 null이 됩니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드의 반환 값은 스크립팅 엔진에서 무시 됩니다.  
  
## <a name="remarks"></a>주의  
 스크립팅 엔진은 호스트에서 지원 되는 경우에만 문서 컨텍스트를 제공할 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptProfilerCallback 인터페이스](../../winscript/reference/iactivescriptprofilercallback-interface.md)