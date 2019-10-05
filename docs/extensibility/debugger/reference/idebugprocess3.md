---
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8db169a06864fad24ef7e6ce4c2d188e2a88ef1d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313853"
---
# <a name="idebugprocess3"></a>IDebugProcess3
이 인터페이스는 실행 중인 프로세스와 프로그램을 나타냅니다. 이 인터페이스의 여러 메서드를 대체도 존재 합니다 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스입니다. 프로세스에서 모든 프로그램에 대 한 제어를 제공합니다.

> [!NOTE]
> [계속](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), 및 [단계](../../../extensibility/debugger/reference/idebugprogram2-step.md) 메서드는 사용 되지 않으며 더 이상 사용 해야 합니다. 해당 메서드를 사용 합니다 `IDebugProcess3` 대신 인터페이스입니다.

## <a name="syntax"></a>구문

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 인터페이스는 프로그램을 관리 그룹으로 사용자 지정 포트 공급자를 통해 구현 됩니다. 프로그램 그룹으로 관리 되는 경우에 실행을 제어 하 고 식 계산기에 대 한 언어를 설정할 수 있습니다. 포트 공급자가이 인터페이스를 구현 해야 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 이 인터페이스는 세션 디버그 관리자 (SDM)에서 주로이 프로세스에서 식별 한 프로그램 그룹을 사용 하 여 상호 작용 하기 위해 호출 됩니다.

 호출 [QueryInterface](/cpp/atl/queryinterface) 에 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 인터페이스가이 인터페이스를 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 상속 된 메서드 외에도 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|프로세스를 통해 단계별 실행 또는 실행을 계속 합니다.|
|[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|프로세스의 실행을 시작합니다.|
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|프로세스의 한 문이나 명령 앞으로 이동 합니다.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|프로세스가 디버깅을 위해 시작 된는 이유를 가져옵니다.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|디버그 엔진에서 적절 한 식 계산기를 로드할 수 있도록 호스팅 언어를 설정 합니다.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|이 프로세스에 대 한 현재 설정 된 언어를 검색 합니다.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|이 프로세스에 대 한 편집 및 계속 (ENC)를 해제합니다.<br /><br /> 사용자 지정 포트 공급자는이 메서드를 구현 하지 않습니다 (항상 반환할 `E_NOTIMPL`).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|이 프로세스에 대 한 ENC 상태를 가져옵니다.<br /><br /> 사용자 지정 포트 공급자는이 메서드를 구현 하지 않습니다 (항상 반환할 `E_NOTIMPL`).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|사용할 디버그 엔진에 대 한 고유 식별자의 배열을 검색합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)