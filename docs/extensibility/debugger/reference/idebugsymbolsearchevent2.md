---
title: IDebugSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed7108c9e1349b01115bed8a6b2a77a3eaa71f45
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320383"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
이 인터페이스는 디버깅 중인 모듈에 대 한 디버깅 기호가 로드 되었는지 나타내려면 디버그 엔진 (DE)에서 전송 됩니다.

## <a name="syntax"></a>구문

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE 모듈의 기호 로드 된 보고서에이 인터페이스를 구현 합니다. 합니다 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 이 인터페이스와 동일한 개체에서 인터페이스를 구현 해야 합니다. SDM 사용 [QueryInterface](/cpp/atl/queryinterface) 액세스는 `IDebugEvent2` 인터페이스입니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 DE을 만들고이 이벤트 개체를 모듈의 기호 로드 된 보고서를 보냅니다. 이벤트를 사용 하 여 전송 되는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 디버깅 중인 프로그램에 연결할 때 SDM에서 제공 하는 콜백 함수.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 `IDebugSymbolSearchEvent2` 인터페이스는 다음 메서드를 노출 합니다.

|메서드|설명|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|기호 검색 결과 대 한 정보를 검색합니다.|

## <a name="remarks"></a>설명
 이 이벤트는 기호를 로드 하지 못했습니다. 경우에 전송 됩니다. 호출 `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` 모듈에서 모든 기호를 실제로 있는지 확인 하려면이 이벤트의 처리기를 허용 합니다.

 Visual Studio에서 로드 된 기호의 상태를 업데이트 하려면 일반적으로이 이벤트를 사용 합니다 **모듈** 창입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)