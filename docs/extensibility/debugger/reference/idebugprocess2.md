---
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0bea73c1bce5367d9686e835bb58dd99a83cc818
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314135"
---
# <a name="idebugprocess2"></a>IDebugProcess2
이 인터페이스는 포트에서 실행 되는 프로세스를 나타냅니다. 포트의 경우 로컬 포트에 다음 `IDebugProcess2` 일반적으로 로컬 컴퓨터의 실제 프로세스를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 인터페이스는 프로그램을 관리 그룹으로 사용자 지정 포트 공급자를 통해 구현 됩니다. 포트 공급자가이 인터페이스를 구현 해야 합니다.

 시작을 통해 프로그램 지 원하는 경우에이 인터페이스를 구현 디버그 엔진 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 이 인터페이스는 세션 디버그 관리자 (SDM)에서 주로이 프로세스에서 식별 한 프로그램 그룹을 사용 하 여 상호 작용 하기 위해 호출 됩니다.

 호출 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) 하거나 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) 이 인터페이스를 가져올 수 있습니다. 이 인터페이스를 호출 하 여도 반환 됩니다 `IDebugEngineLaunch2::LaunchSuspended`합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugProcess2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|프로세스에 대 한 설명을 가져옵니다.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|이 프로세스에 포함 된 프로그램을 열거 합니다.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|제목, 이름 또는 프로세스의 파일 이름을 가져옵니다.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|이 프로세스에서 실행 중인 서버 컴퓨터의 인스턴스를 가져옵니다.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|프로세스를 종료합니다.|
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|프로세스에 연결 합니다.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|SDM 프로세스를 분리할 수 있습니다 하는 경우를 결정 합니다.|
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|프로세스에서 디버거를 분리합니다.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|시스템 프로세스 식별자를 가져옵니다.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|이 프로세스에 대 한 전역적으로 고유 식별자를 가져옵니다.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [사용 되지 않음]|프로세스를 디버깅 하는 세션의 이름을 가져옵니다.<br /><br /> [사용 되지 않습니다. 항상 반환 해야 `E_NOTIMPL`.]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|프로세스에서 실행 중인 스레드를 열거 합니다.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|다음 프로그램에서 프로세스 중지가 코드를 실행 하도록 요청 합니다.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|이 프로세스에서 실행 되는 포트를 가져옵니다.|

## <a name="remarks"></a>설명
 `IDebugProcess2` 하나 이상 포함 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스입니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)