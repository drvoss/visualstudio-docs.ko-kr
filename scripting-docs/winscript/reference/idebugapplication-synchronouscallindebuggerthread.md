---
title: 'IDebugApplication:: SynchronousCallInDebuggerThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SynchronousCallInDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 134717b6ce30c87ccfb4bbb50ffe958717ae757f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574591"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
호출자가 디버거 스레드에서 코드를 실행 하는 메커니즘을 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pptc`  
 진행 호출할 개체입니다.  
  
 `dwParam1`  
 진행 `IDebugThreadCall::ThreadCallHandler` 메서드에 전달할 첫 번째 매개 변수입니다.  
  
 `dwParam2`  
 진행 `IDebugThreadCall::ThreadCallHandler` 메서드에 전달할 두 번째 매개 변수입니다.  
  
 `dwParam3`  
 진행 `IDebugThreadCall::ThreadCallHandler` 메서드에 전달할 세 번째 매개 변수입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 언어 엔진 및 호스트는 일반적으로이 메서드를 사용 하 여 단일 스레드 구현 위에 자유 스레드 개체를 구현 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Idebugapplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugThreadCall 인터페이스](../../winscript/reference/idebugthreadcall-interface.md)