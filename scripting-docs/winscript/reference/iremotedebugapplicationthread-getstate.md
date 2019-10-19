---
title: 'IRemoteDebugApplicationThread:: GetState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetState
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42f7f2a292c908b5fe49f1097b0fe56b8b0b11e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575244"
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
이 스레드의 상태를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pState`  
 제한이 다음 스레드 상태 플래그의 조합입니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|스레드가 실행 되 고 있습니다.|  
|THREAD_STATE_SUSPENDED|0x00000002|스레드가 일시 중단 되었습니다.|  
|THREAD_BLOCKED|0x00000004|스레드가 차단 되었습니다.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|스레드의 콘텐츠가 부족 합니다.|  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는이 스레드의 상태를 가져옵니다.  
  
## <a name="see-also"></a>참조  
 [IRemoteDebugApplicationThread 인터페이스](../../winscript/reference/iremotedebugapplicationthread-interface.md)