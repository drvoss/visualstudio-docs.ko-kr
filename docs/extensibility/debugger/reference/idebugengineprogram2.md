---
title: IDebugEngineProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 221ab8fd00bc7d98745fdd5cc03dd72b9919b4b2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345133"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
이 인터페이스는 다중 스레드 디버깅을 지원 합니다.

## <a name="syntax"></a>구문

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진을 다중 스레드의 동시 디버깅을 지원 하기 위해이 인터페이스를 구현 합니다. 이 인터페이스를 구현 하는 동일한 개체에서 구현 됩니다 합니다 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스입니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 사용 하 여 [QueryInterface](/cpp/atl/queryinterface) 에서이 인터페이스를 가져올 수는 `IDebugProgram2` 인터페이스입니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugEngineProgram2`합니다.

|메서드|설명|
|------------|-----------------|
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|이 프로그램에서 실행 중인 모든 스레드를 중지 합니다.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|실행 (또는 실행에 대 한 감시 중지)에 대 한 감시 지정한 스레드에서 발생 합니다.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|허용 하거나 허용 하지 않습니다 프로그램이 중지 하는 경우에 특정 스레드에서 발생 되는 식 계산.|

## <a name="remarks"></a>설명
 이 인터페이스에 대 한 응답에서을 호출 하는 visual Studio는 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트 프로그램의 "보기에 대 한 스레드 단계" 및 "에 대 한 식 평가에서 스레드 보기" 상태를 설정 하 고 있습니다. [중지](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 가 호출 될 때마다 프로그램이 중지;이 방법을 사용 하면 프로그램 모든 스레드를 종료 하기.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)