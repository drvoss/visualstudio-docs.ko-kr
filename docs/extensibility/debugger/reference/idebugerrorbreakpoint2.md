---
title: IDebugErrorBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2
helpviewer_keywords:
- IDebugErrorBreakpoint2 interface
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f25187b2aa88153fcfd712b9dd4b0f651ba8860
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327796"
---
# <a name="idebugerrorbreakpoint2"></a>IDebugErrorBreakpoint2
이 인터페이스에는 오류 또는 잘못 된 위치, 잘못 된 식, 이유는 보류 중인 중단점에 바인딩되지 (코드 등, 아직 로드 되지 않은) 하는 이유 등 경고 중단점을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugErrorBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진을 중단점에 대 한 지원의 일부로이 인터페이스를 구현합니다. 이 인터페이스는 중단점 바인딩을 사용 하 여 문제를 보고에 사용 됩니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 에 대 한 호출 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) 이 인터페이스를 가져옵니다. 이 인터페이스를 반환할 수도 있습니다 (나타내는 목록의 일부로 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) 인터페이스)를 호출 하 여 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) 하거나 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugErrorBreakpoint2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|오류를 발생 시킨 보류 중인 중단점을 가져옵니다.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|오류를 설명 하는 중단점 오류 해상도를 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [다음](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)