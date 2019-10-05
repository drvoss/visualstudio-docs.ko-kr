---
title: IDebugEventCallback2::Event | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 37462b5f274ca6e6c2a4a2feb4083ea94ea2f066
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163981"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버그 이벤트의 알림을 보냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pEngine`  
 [in] [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 이 이벤트를 전송 하는 디버그 엔진 (DE)를 나타내는 개체입니다. 독일은이 매개 변수를 입력 해야 합니다.  
  
 `pProcess`  
 [in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 이벤트가 발생 하는 프로세스를 나타내는 개체입니다. 이 매개 변수는 세션 디버그 관리자 (SDM)에서 채워집니다. 독일에는 항상이 매개 변수에 대해 null 값을 전달합니다.  
  
 `pProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 이 이벤트가 발생 하는 프로그램을 나타내는 개체입니다. 대부분의 이벤트에 대 한이 매개 변수가 아닌 경우 null 값  
  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 이 이벤트가 발생 하는 스레드를 나타내는 개체입니다. 중지 이벤트에 대 한 스택 프레임은이 매개 변수에서 가져온 대로이 매개 변수 null 값이 될 수 없습니다.  
  
 `pEvent`  
 [in] [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 디버그 이벤트를 나타내는 개체입니다.  
  
 `riidEvent`  
 [in] 얻을 수 있는 이벤트 인터페이스를 식별 하는 GUID는 `pEvent` 매개 변수입니다.  
  
 `dwAttrib`  
 [in] 플래그의 조합 된 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) 열거형입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드를 호출 하는 경우는 `dwAttrib` 매개 변수에서 반환 된 값과 일치 해야 합니다는 [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) 전달 된 이벤트 개체에서 호출 메서드는 `pEvent` 매개 변수입니다.  
  
 모든 디버그 이벤트는 이벤트 자체 비동기 인지 여부에 관계 없이 비동기적으로 게시 됩니다. DE이이 메서드를 호출 하는 경우 반환 값을 나타내지 않습니다 이벤트가 처리 된 여부를 이벤트를 받은 있는지 여부를 합니다. 사실 대부분의 상황에서 이벤트 처리 되지 않았습니다이 메서드가 반환 될 때입니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
