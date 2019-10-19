---
title: 'IRemoteDebugApplicationThread:: SetNextStatement | Microsoft Docs'
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
ms.openlocfilehash: 71e690d0e5b7567aabc88aabde907b67517f12aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575515"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
지정 된 프레임의 컨텍스트에서 지정 된 코드 컨텍스트와 최대한 가깝게 계속 실행 되도록 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pStackFrame`  
 진행 스택 프레임 개체입니다. 이 인수는 NULL 일 수 있으며,이는 현재 스택 프레임을 사용 해야 함을 의미 합니다.  
  
 `pCodeContext`  
 진행 코드 컨텍스트입니다. 이 인수는 NULL 일 수 있습니다 .이는 현재 코드 컨텍스트를 사용 해야 함을 의미 합니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 `pStackFrame`으로 지정 된 프레임의 컨텍스트에서 `pCodeContext`에 지정 된 코드 컨텍스트와 최대한 가깝게 계속 실행 되도록 합니다. 이러한 인수 중 하나는 현재 프레임이 나 컨텍스트를 나타내는 `NULL` 될 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IRemoteDebugApplicationThread 인터페이스](../../winscript/reference/iremotedebugapplicationthread-interface.md)