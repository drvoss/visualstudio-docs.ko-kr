---
title: IDebugModule3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 582c6fa887062986ccd1b66c7f3466b89407bcca
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323750"
---
# <a name="idebugmodule3"></a>IDebugModule3
이 인터페이스에는 기호 및 JustMyCode 상태의 대체 위치를 지 원하는 모듈을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 대체 위치를 지원 하 고 JustMyCode 상태를 사용 하려면이 인터페이스를 구현 하는 디버그 엔진 (DE) (참조를 [Visual Studio 디버거 용어집](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) "JustMyCode"의 정의 대 한).

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 에 대 한 호출 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) 이 인터페이스를 반환 합니다. DE 보냅니다 합니다 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) 인터페이스를 사용 하 여 세션 디버그 관리자 (SDM)에 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 메서드. 또한 호출 [QueryInterface](/cpp/atl/queryinterface) 에 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 인터페이스는이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 메서드 외에도 합니다 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 인터페이스에서이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|기호 및 각 경로 검색 한 결과 검색할 경로의 목록을 반환 합니다.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|로드 하 고 현재 모듈에 대 한 기호를 초기화 합니다.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|모듈 사용자 코드를 나타내는지 여부를 지정 하는 반환 플래그입니다.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|고려할지 여부를 모듈 사용자 코드 여부를 지정 합니다.|

## <a name="remarks"></a>설명
 Visual Studio에는이 인터페이스의 일반적인 소비자입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)