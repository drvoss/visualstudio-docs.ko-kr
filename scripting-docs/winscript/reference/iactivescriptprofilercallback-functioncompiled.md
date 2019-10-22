---
title: 'IActiveScriptProfilerCallback:: FunctionCompiled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.FunctionCompiled
apilocation:
- scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a17ce7548a6524df6911cdf952393020472b88ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576470"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
스크립트를 컴파일할 때 스크립팅 엔진에서 함수를 발견 했음을 프로파일러 개체에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `functionId`  
 진행 함수의 고유 ID입니다. 이 ID는 스크립팅 엔진에서 할당 합니다.  
  
 `scriptId`  
 진행 함수가 포함 된 스크립트의 고유 ID입니다.  
  
 `pwszFunctionName`  
 진행 함수의 이름 이거나 익명 함수의 경우 null입니다.  
  
 `pwszFunctionNameHint`  
 진행 함수의 유추 이름 이거나, 스크립팅 엔진에서 이름을 유추 하지 않는 경우 null입니다.  
  
 `pIDebugDocumentContext`  
 진행 사용 가능한 경우 프로파일러가 [Idebugdocumentcontext 인터페이스](../../winscript/reference/idebugdocumentcontext-interface.md) 포인터를 쿼리해야 하는 `IUnknown` 인터페이스에 대 한 포인터입니다. 그렇지 않으면 null입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드의 반환 값은 스크립팅 엔진에서 무시 됩니다.  
  
## <a name="remarks"></a>주의  
 스크립팅 엔진은 호스트에서 지원 되는 경우에만 문서 컨텍스트를 제공할 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptProfilerCallback 인터페이스](../../winscript/reference/iactivescriptprofilercallback-interface.md)