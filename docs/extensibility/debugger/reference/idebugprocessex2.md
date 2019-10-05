---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c27a03a09a6073ebab8d7a2dd5f60218066d474
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311596"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
이 인터페이스는 세션을 디버그 관리자 (SDM)에 연결 되었거나 프로세스에서 분리 하는 프로세스를 알릴 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 동일한 개체에서이 인터페이스를 구현 하는 사용자 지정 포트 공급자는 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 를 순서 대로 인터페이스:

- 프로세스에 연결 된 세션 추적 지원

- 지원 자동 연결에서 여러 디버그 엔진

  사용자 지정 포트 공급자 선택 하는 경우이 인터페이스를 구현할 수 있습니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보

- SDM 호출 [QueryInterface](/cpp/atl/queryinterface) 에 `IDebugProcess2` 인터페이스가이 인터페이스를 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugProcessEx2`합니다.

|메서드|설명|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|세션에서 프로세스를 디버깅 이제는 프로세스에 알립니다.|
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|세션에서 프로세스를 디버깅 이상는 프로세스에 알립니다.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|디버그 엔진 목록은 프로그램 노드를 추가합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 SDM와 프로세스 간에 개인입니다.

## <a name="requirements"></a>요구 사항
 헤더: Portpriv.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)