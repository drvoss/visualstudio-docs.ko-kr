---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b6f59c9444b0c54f8a230f8eb4487e16b65ebf4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345231"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
디버그 엔진 (DE)에 의해 시작 프로그램을 종료 하는 데 사용 합니다.

## <a name="syntax"></a>구문

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 인터페이스는 사용자 지정 포트를 통해 완전히 처리할 수 없는 프로세스를 시작 하는 것에 대 한 특별 한 요구 사항이 있을 경우 사용자 지정 DE 하 여 구현 됩니다. 이 경우 일반적으로 DE 인터프리터의 일부 이며 디버깅 중인 프로세스 스크립트: 인터프리터 먼저 시작 해야 하며 스크립트 로드 되 고 시작 합니다. 포트는 인터프리터를 시작할 수 있지만 스크립트 (여기서는 DE는 역할을를 임) 특별 한 처리가 필요할 수 있습니다. 이 인터페이스는 사용자 지정 포트를 처리할 수 없는 프로그램을 시작 하는 것에 대 한 고유한 요구 사항이 있는 경우에 구현 됩니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 이 인터페이스 라고 세션 디버그 관리자 (SDM)에서 SDM이이 인터페이스를 가져올 수 있습니다 하는 경우에서 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 인터페이스 (QueryInterface 사용). 이 인터페이스를 가져올 수는 DE 특별 한 요구 사항이 있고 시작 포트 대신 프로그램을 시작 하려면이 인터페이스를 호출 SDM 알고 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugEngineLaunch2`합니다.

|메서드|설명|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|DE를 사용 하 여 프로세스를 시작합니다.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|프로세스 실행을 다시 시작 합니다.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|프로세스를 종료할 수 있습니다 하는 경우를 결정 합니다.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|프로세스를 종료합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)