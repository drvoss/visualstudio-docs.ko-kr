---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0cfc29f300bc9f28f857424a7a91b4b6bfd3bf82
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331523"
---
# <a name="idebugprogram3"></a>IDebugProgram3
이 인터페이스는 프로세스에서 실행 되 고 확장 하는 프로그램을 나타내는 [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md) 스레드 정보를 제공 합니다.

## <a name="syntax"></a>구문

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE) 및 사용자 지정 포트 공급자 프로세스에는 프로그램을 나타내며이 인터페이스를 구현 합니다. 세션 디버그 관리자 (SDM) 정보를 제공 하려면이 인터페이스 구현 [연결](../../../extensibility/debugger/reference/idebugprogram2-attach.md)합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 합니다 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트에 대 한 새 프로그램을이 인터페이스를 반환 합니다. 이 인터페이스에 대 한 많은 메서드 여러 인터페이스를 매개 변수로 사용 됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugProgram3`합니다.

|메서드|설명|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|프로그램을 실행합니다. 스레드는 스레드를 사용자가 실행할 때 보고 디버거 정보를 제공 해에 반환 됩니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>설명
 프로그램은 하나 이상의 응용 프로그램의 프로세스 이루어집니다 하는 동안 특정 런타임 아키텍처에서 실행 되는 스레드 컨테이너입니다.

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)