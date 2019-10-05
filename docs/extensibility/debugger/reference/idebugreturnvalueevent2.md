---
title: IDebugReturnValueEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReturnValueEvent2
helpviewer_keywords:
- IDebugReturnValueEvent2
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03f3a46c7213a48b527f2756e5a4915ca59e48f8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345652"
---
# <a name="idebugreturnvalueevent2"></a>IDebugReturnValueEvent2
이 인터페이스의 또는 함수를 단계별로 실행 한 후 디버그 엔진 (DE)에서 (SDM) 세션 디버그 관리자에 게 전송 됩니다.

## <a name="syntax"></a>구문

```
IDebugReturnValueEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE 개 게이트웨이나 단계별 되었습니다에 있는 함수에서 반환 값을 보고 하려면이 인터페이스를 구현 합니다. 합니다 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 이 인터페이스와 동일한 개체에서 인터페이스를 구현 해야 합니다. SDM 사용 [QueryInterface](/cpp/atl/queryinterface) 액세스는 `IDebugEvent2` 인터페이스입니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 DE을 만들어 함수의 반환 값을 보고 하려면이 이벤트 개체를 보냅니다. 이벤트를 사용 하 여 전송 되는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 디버그 중인 프로그램에 연결 될 때 SDM에서 제공 하는 콜백 함수.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서 메서드의 `IDebugReturnValueEvent2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|함수를 나가는 경우의 반환 값을 가져옵니다.|

## <a name="remarks"></a>설명
 호출 하 여 함수에 의해 반환 되는 값을 가져올 수 있습니다 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)합니다. 반환 된 값이 나타나는 합니다 **자동** 창입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)