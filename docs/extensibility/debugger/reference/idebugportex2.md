---
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bed6cd047af4ba57a1880d87e30a990dcf83efac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340427"
---
# <a name="idebugportex2"></a>IDebugPortEx2
이 인터페이스를 사용 하면 프로그램 및 포트에서 실행 되는 프로세스 관리자 (SDM) 컨트롤을 디버깅 세션이 있습니다.

## <a name="syntax"></a>구문

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 사용자 지정 포트 공급자 구현 하는 동일한 개체에서이 인터페이스를 구현 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 SDM 호출 [QueryInterface](/cpp/atl/queryinterface) 에 `IDebugPort2` 인터페이스가이 인터페이스를 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugPortEx2`합니다.

|메서드|설명|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|실행 파일을 시작합니다.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|프로세스의 실행을 다시 시작합니다.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|프로세스를 종료할 수 있는지 여부를 결정 합니다.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|프로세스를 종료합니다.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|포트의 프로세스 ID를 가져옵니다.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|프로그램 노드와 연결 된 프로그램을 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 SDM 및 사용자 지정 포트 공급자 간에 일반적으로 개인입니다.

 디버그 엔진 (DE) 원하는 경우이 인터페이스에 대 한 볼 수를 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스에 전달 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 사용 하 여 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) 프로그램을 시작 합니다. 그러나 이것이 요구 사항은 없습니다 및는 DE 요청 프로그램을 시작 하기 위해 필요한 작업을 수행할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: portpriv.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)