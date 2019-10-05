---
title: IRemoteDebugApplicationThread::SetNextStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.SetNextStatement
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c4b19322a15e92adcf2609c479af6b21e2078bd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788143"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
지정 된 프레임의 컨텍스트에서 지정 된 코드 컨텍스트를 최대한 가깝게 계속 강제로 실행 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pStackFrame`  
 [in] 스택 프레임 개체입니다. 이 인수는 현재 스택 프레임을 사용 해야 하는 NULL이 될 수 있습니다.  
  
 `pCodeContext`  
 [in] 코드 컨텍스트입니다. 이 인수에는 현재 코드 컨텍스트를 사용 해야 하는 NULL이 될 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 이 메서드를 사용 하면 실행을 계속 하 여 지정 된 코드 컨텍스트를 최대한 가깝게 `pCodeContext`를 지정한 프레임의 컨텍스트에서 `pStackFrame`합니다. 이러한 인수 중 하나가 될 수 있습니다 `NULL`을 현재 프레임 또는 컨텍스트를 나타내는입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IRemoteDebugApplicationThread 인터페이스](../../winscript/reference/iremotedebugapplicationthread-interface.md)