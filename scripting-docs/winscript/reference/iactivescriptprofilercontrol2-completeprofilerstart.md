---
title: 'IActiveScriptProfilerControl2:: CompleteProfilerStart | Microsoft Docs'
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
ms.openlocfilehash: f0230ecb480792b5b24b7375f5b95926735d0a61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571562"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
해당 하는 모든 스크립팅 엔진에서 프로 파일링을 시작 했음을 프로파일러에 알립니다. 이 메서드를 사용 하 여 프로 파일링을 시작할 때 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 실행 되 고 있으면 전체 호출 스택을 가져올 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>매개 변수  
 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 HRESULT를 반환 합니다. 다음과 같은 값을 사용할 수 있습니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_FAIL`|프로 파일링을 시작할 수 없습니다.|  
|`S_FALSE`|스크립트가 실행 되 고 있지 않을 때 프로 파일링이 시작 되었습니다.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|프로 파일링이 사용 하도록 설정 되어 있지 않습니다. 콜백이 설정 되지 않았습니다.|  
|`E_OUTOFMEMORY`|메모리 부족 상태로 인해 호출 스택을 가져올 수 없습니다.|  
  
## <a name="remarks"></a>주의  
 @No__t_0를 호출 하면 이미 호출 스택에 있는 함수에 대 한 이벤트가 전송 됩니다. 현재 탭에 있는 모든 스크립팅 엔진에서 프로 파일링이 시작 된 후이 메서드를 호출 해야 합니다. 모든 스크립팅 엔진에 대해 메서드를 호출할 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptProfilerControl2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)    
 [IActiveScriptProfilerControl2 인터페이스](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)