---
title: IDebugBreakpointErrorEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bae4a63ef03ca3b8d3fa642f7333ff2357084b47
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352942"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
이 인터페이스는 보류 중인 중단점을 바인딩할 수 없습니다는 로드 프로그램 경고 또는 오류 때문에 세션 디버그 관리자 SDM ()를 알려 줍니다.

## <a name="syntax"></a>구문

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE 중단점에 대 한 지원의 일부로이 인터페이스를 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 이 인터페이스와 동일한 개체에서 인터페이스를 구현 해야 (SDM 사용 [QueryInterface](/cpp/atl/queryinterface) 액세스 하는 `IDebugEvent2` 인터페이스).

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 DE을 만들어 디버깅 중인 프로그램에 보류 중인 중단점을 바인딩할 수 없습니다 하는 경우이 이벤트 개체를 보냅니다. 이벤트를 사용 하 여 전송 되는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM를 디버깅 중인 프로그램에 연결할 때 제공한 콜백 함수.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugBreakpointErrorEvent2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|가져옵니다 합니다 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 경고 또는 오류를 설명 하는 인터페이스입니다.|

## <a name="remarks"></a>설명
 중단점이 바인딩된, 때마다 SDM에 이벤트가 전송 됩니다. 중단점을 바인딩할 수 없는 경우는 `IDebugBreakpointErrorEvent2` 이 고, 그렇지 않으면 보낸는 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 보내집니다.

 예를 들어, 구문 분석 또는 평가 위한 관련 된 보류 중인 중단점 조건이 실패 하면 경고 지금은 보류 중인 중단점을 바인딩할 수 없습니다 전송 됩니다. 이 중단점에 대 한 코드를 아직 로드 되지 않은 경우 발생할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)