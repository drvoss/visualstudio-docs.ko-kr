---
title: 'IActiveScriptProfilerCallback:: Shutdown | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Shutdown
apilocation:
- scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: deecfe4134a4b0e18591823f194ceaf6d1eb0a14
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571651"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
스크립팅 엔진에서 프로 파일링이 중지 될 때마다 프로파일러 개체에 알리기 위해 호출 됩니다. 이러한 방식으로 프로파일러 개체는 필요한 경우 정리 루틴을 호출할 수 있습니다. 이 메서드는 스크립팅 엔진을 종료할 때 또는 [IActiveScriptProfilerCallback:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) 호출이 실패할 때 스크립팅 엔진에서 호출 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `hrReason`  
 진행 종료 이유입니다. 스크립팅 엔진을 종료 하는 경우 `S_OK` 전달 됩니다. [IActiveScriptProfilerCallback:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) 호출에서 오류 hresult를 반환 하는 경우 hresult가 전달 됩니다. 그렇지 않으면이 값은 [IActiveScriptProfilerControl:: StopProfiling 파일링](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)에서 검색 됩니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드의 반환 값은 스크립팅 엔진에서 무시 됩니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptProfilerCallback 인터페이스](../../winscript/reference/iactivescriptprofilercallback-interface.md)