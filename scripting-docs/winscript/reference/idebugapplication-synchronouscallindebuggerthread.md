---
title: IDebugApplication::SynchronousCallInDebuggerThread | Microsoft Docs
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
ms.openlocfilehash: d5460efaa3448c7812707e0baa7b2f5afe1d27a0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990564"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
호출자에 게 디버거 스레드에서 코드를 실행 하는 메커니즘을 제공 합니다.  
  
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
 [in] 호출 개체입니다.  
  
 `dwParam1`  
 [in] 첫 번째 매개 변수를 전달 하 여 `IDebugThreadCall::ThreadCallHandler` 메서드.  
  
 `dwParam2`  
 [in] 두 번째 매개 변수를 전달 하 여 `IDebugThreadCall::ThreadCallHandler` 메서드.  
  
 `dwParam3`  
 [in] 세 번째 매개 변수를 전달 하 여 `IDebugThreadCall::ThreadCallHandler` 메서드.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 언어 엔진과 호스트 일반적으로 자유 스레드 개체는 단일 스레드 구현 기반으로 구현 하려면이 메서드를 사용 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugApplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugThreadCall 인터페이스](../../winscript/reference/idebugthreadcall-interface.md)