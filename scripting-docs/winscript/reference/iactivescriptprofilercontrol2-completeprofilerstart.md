---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36a1f5d6a1401e2860b65a29c8e383627e83c6be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993026"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
모든 적용 가능한 스크립팅 엔진에서 프로 파일링 시작 했다고 프로파일러에 알립니다. 이 메서드를 사용 하 여 얻을 수 있으면 전체 호출 스택을 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 프로 파일링을 시작할 때 실행 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>매개 변수  
 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 HRESULT를 반환합니다. 다음과 같은 값을 사용할 수 있습니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_FAIL`|프로 파일링을 시작할 수 없습니다.|  
|`S_FALSE`|프로 파일링 스크립트 실행 되지 않는 경우 시작 되었습니다.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|프로 파일링 사용 되지 않습니다. 콜백이 없는 설정 되었습니다.|  
|`E_OUTOFMEMORY`|호출 스택의 메모리의 조건으로 인해 얻을 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 호출 `IActiveScriptProfilerControl2::CompleteProfilerStart` 호출 스택에 있는 함수에 대 한 이벤트 전송 되는지 확인 합니다. 이 메서드는 현재 탭에 있는 모든 스크립팅 엔진에서 시작을 프로 파일링 한 후 호출 합니다. 모든 스크립팅 엔진에 대 한 메서드를 호출할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 인터페이스](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)