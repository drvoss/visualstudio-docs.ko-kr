---
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3d76c3e41159e9bc200acdb788c13ad5f995cc3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310520"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
이 인터페이스는 세션 디버그 관리자 (SDM)로 디버그 이벤트를 보내는 디버그 엔진 (DE)에 의해 사용 됩니다.

## <a name="syntax"></a>구문

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 디버그 엔진에서 이벤트를 수신 하려면이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 SDM 호출할 때 일반적으로이 인터페이스를 받는 디버그 엔진 [연결](../../../extensibility/debugger/reference/idebugprogram2-attach.md)를 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md), 또는 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)합니다. 디버그 엔진은 SDM에 호출 하 여 이벤트를 보냅니다 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugEventCallback2`합니다.

|메서드|설명|
|------------|-----------------|
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|SDM 이벤트 디버깅에 대 한 알림을 보냅니다.|

## <a name="remarks"></a>설명
 하지만 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 및 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 많으며는 지정는 `IDebugEventCallback2` 인터페이스,이 경우 아니며 인터페이스 포인터에 null 값은 항상. 디버그 엔진 대신 사용 해야 합니다 `IDebugEventCallback2` 인터페이스에 대 한 호출에서 받은 [연결](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md), 또는 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)합니다.

 패키지를 구현 하는 경우 [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) 관리 코드에서 것이 좋습니다입니다 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> 에 전달 되는 다양 한 인터페이스에서 호출할 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)