---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f364b6aa622bf9c7481d61e7646e955cebe00933
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695395"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버그 엔진 (DE)는 현재 실행 중인 프로그램에 예외가 throw 되 면 (SDM) 세션 디버그 관리자에 게이 인터페이스를 보냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE 디버깅 중인 프로그램에서 예외가 발생에 보고서에이 인터페이스를 구현 합니다. 합니다 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 이 인터페이스와 동일한 개체에서 인터페이스를 구현 해야 합니다. SDM 사용 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 액세스는 `IDebugEvent2` 인터페이스입니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 DE가 만들고 예외를 보고 하려면이 이벤트 개체를 보냅니다. 이벤트를 사용 하 여 보내집니다 합니다 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 디버깅 중인 프로그램에 연결할 때 SDM에서 제공 하는 콜백 함수입니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugExceptionEvent2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|이 이벤트를 발생 시킨 예외에 대 한 자세한 정보를 가져옵니다.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|이 이벤트를 발생 시킨 throw 된 예외에 대 한 알기 쉬운 설명을 가져옵니다.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|디버그 엔진 (DE) 실행을 다시 시작할 때 디버깅 중인 프로그램에이 예외를 전달 하는 옵션을 지원 여부를 결정 합니다.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|예외를 삭제 해야 하는 경우 또는 예외 실행을 다시 시작할 때 디버깅 중인 프로그램에 전달 되어야 합니다 있는지 여부를 지정 합니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>설명  
 이벤트를 보내기 전에 DE 확인 하는 경우이 예외 이벤트가 지정 된 첫째 또는 둘째 예외에 대 한 이전 호출 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)합니다. 첫째 예외를 지정 된 경우는 `IDebugExceptionEvent2` SDM에 이벤트가 전송 됩니다. 그렇지 않은 경우는 DE 예외를 처리 하는 응용 프로그램에 제공 합니다. 없음 예외 처리기가 제공 하 고 예외를 두 번째 예외를으로 지정 된 경우는 `IDebugExceptionEvent2` SDM에 이벤트가 전송 됩니다. 그렇지 않으면는 DE 프로그램의 실행을 다시 시작 하 고 운영 체제 또는 런타임 예외를 처리 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
