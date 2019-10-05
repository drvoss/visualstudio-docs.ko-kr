---
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6d8f869e519d9500f1ea8f3bb33a3ee098f5cfd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325411"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
이 인터페이스는 현재 디버그 세션에서 실행 중인 스레드를 열거 합니다.

## <a name="syntax"></a>구문

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE) 프로그램의 스레드 목록을 나타내는 데이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 호출 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) 프로세스에서 실행 중인 모든 프로그램에서 모든 스레드의 목록을 나타내는이 인터페이스를 가져올 수 있습니다. 호출 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 프로그램에서 실행 중인 스레드 목록을 나타내는이 인터페이스를 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IEnumDebugThreads2`합니다.

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|열거형 시퀀스에서 스레드의 지정된 된 수를 검색 합니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|열거형 시퀀스에서 스레드의 지정 된 수를 건너뜁니다.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|열거형 시퀀스를 처음으로 다시 설정합니다.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|현재 열거자와 열거 상태가 같은 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|열거자에서 스레드 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio에는 일반적으로이 인터페이스 업데이트를 가져옵니다 합니다 **스레드** 목록의 첫 번째 스레드가 호출 하기 위해 가져오기에 대 한 창 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)에 [계속](../../../extensibility/debugger/reference/idebugprocess3-continue.md), 및 [단계](../../../extensibility/debugger/reference/idebugprocess3-step.md)합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
