---
title: IDebugThread2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df63bc6484905249adc1756ce701b3ee91f45015
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319973"
---
# <a name="idebugthread2"></a>IDebugThread2
이 인터페이스는 프로그램에서 실행 중인 스레드를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE)은 단일 프로그램에서 실행 스레드를 나타내는 데이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 호출 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) 현재 활성 스레드를 나타내는이 인터페이스를 가져올 수 있습니다.

 이 인터페이스는 또한 중단점 요청을 만드는 사용 됩니다 (참조 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 이 인터페이스는 바운드 또는 오류 중단점 해결 하는 경우에 반환 됩니다 (참조 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 하 고 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugThread2`합니다.

|메서드|설명|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|이 스레드에 대 한 스택 프레임의 목록을 검색합니다.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|스레드의 이름을 가져옵니다.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|스레드 이름을 설정합니다.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|스레드가 실행 되는 프로그램을 가져옵니다.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|다음 문은 지정 된 스택 프레임 및 코드 컨텍스트를 설정할 수 있는 여부를 결정 합니다.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|다음 문은 지정 된 스택 프레임 및 코드 컨텍스트를 설정합니다.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|시스템 스레드 식별자를 가져옵니다.|
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|스레드를 일시 중단합니다.|
|[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)|스레드를 다시 시작합니다.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|스레드를 설명 하는 속성을 가져옵니다.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|이 실제 스레드와 연결 된 논리적 스레드를 가져옵니다.|

## <a name="remarks"></a>설명
 단일 실제 스레드에 여러 프로그램을 하나 이상에서 실행 될 수 있으므로 `IDebugThread2` 둘 이상의 프로그램에서 동일한 실제 스레드에서 나타낼 수 있습니다.

 중단점 또는 예외가 발생 하면 이벤트를 호출 하 여 보내집니다 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)합니다. 이 메서드를 인수 중 하나는 `IDebugThread2` 현재 스레드를 나타내는 인터페이스입니다. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 가져오는 데 사용 되는 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 현재 스택 프레임에 대 한 인터페이스입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)