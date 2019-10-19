---
title: 'IRemoteDebugApplicationThread:: GetSystemThreadId | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetSystemThreadId
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetSystemThreadId
ms.assetid: 6a6d5f62-4f60-4e87-9206-3c6f2e026d11
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35c281047bd3333f8fdc3945ed97ad3f402c53a4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575225"
---
# <a name="iremotedebugapplicationthreadgetsystemthreadid"></a>IRemoteDebugApplicationThread::GetSystemThreadId
는 스레드와 연결 된 운영 체제 종속 식별자를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetSystemThreadId(  
   DWORD*  dwThreadId  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwThreadId`  
 제한이 스레드와 연결 된 운영 체제 종속 식별자입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 @No__t_0의 값은 여러 컴퓨터에서 고유할 필요가 없습니다.  
  
## <a name="see-also"></a>참조  
 [IRemoteDebugApplicationThread 인터페이스](../../winscript/reference/iremotedebugapplicationthread-interface.md)