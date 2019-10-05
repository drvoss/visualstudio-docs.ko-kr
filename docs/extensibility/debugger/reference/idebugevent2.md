---
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f87184481c5d01e74d284b175078b67f6f2612d1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310604"
---
# <a name="idebugevent2"></a>IDebugEvent2
이 인터페이스는 모두 중단점에서 중지 하는 등의 중요 한 디버그 정보 및 디버깅 메시지와 같은 중요 하지 않은 정보를 전달 하기 위해 사용 됩니다.

## <a name="syntax"></a>구문

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE) 및 사용자 지정 포트 공급자를 다른 모든 이벤트 인터페이스와 같은 개체에서이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 인터페이스에 지정 된 ID (IID) 인수를 사용 하 여 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 또는 [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md), 세션 디버그 관리자 (SDM) 호출 [QueryInterface](/cpp/atl/queryinterface) 에 `IDebugEvent2` 를 얻기 위해 인터페이스 적절 한 이벤트 인터페이스입니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugEvent2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|이 디버그 이벤트에 대 한 특성을 가져옵니다.|

## <a name="remarks"></a>설명
 와 같은 보다 구체적인 이벤트 인터페이스 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)IDebugEvent2 인터페이스에서 파생 되지 않은 되지만 동일한 개체에서 별도 인터페이스로 구현 대신 됩니다 `IDebugEvent2`합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)