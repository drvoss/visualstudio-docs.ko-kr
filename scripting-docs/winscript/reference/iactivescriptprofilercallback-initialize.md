---
title: 'IActiveScriptProfilerCallback:: Initialize | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Initialize
apilocation:
- scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbbd61d6b3c10dcfffe2df215cc5a60d685dd803
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576449"
---
# <a name="iactivescriptprofilercallbackinitialize"></a>IActiveScriptProfilerCallback::Initialize
스크립팅 엔진에서 프로 파일링이 시작 될 때마다 프로파일러 개체를 초기화 하기 위해 호출 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwContext`  
 진행 [IActiveScriptProfilerControl:: StartProfiling 파일링](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)에 전달 되는 4 바이트 값입니다.  
  
## <a name="return-value"></a>반환 값  
 HRESULT를 반환 합니다. 다음과 같은 값을 사용할 수 있습니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 메서드가 프로파일러 개체를 초기화할 수 없는 경우 스크립팅 엔진에 알리기 위해 오류 HRESULT를 반환 해야 합니다. 이 경우 스크립팅 엔진은 [IActiveScriptProfilerCallback:: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)을 직접 호출 하 고 매개 변수에 HRESULT를 전달한 다음 프로파일러 개체를 해제 해야 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptProfilerCallback 인터페이스](../../winscript/reference/iactivescriptprofilercallback-interface.md)