---
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55e7c73b720e326b823c3038928d7141ea732155
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352905"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
이 인터페이스를 만들고 모든 중단점 유형에 바인딩하는 데 필요한 정보를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 세션 디버그 관리자 SDM ()는 일반적으로이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 디버그 엔진 (DE)에 대 한 호출을 통해이 인터페이스를 받는 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 보류 중인 중단점을 만들기 위해. 에 대 한 호출 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) 는 DE에서이 인터페이스를 검색할 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugBreakpointRequest2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|이 중단점 요청의 중단점 위치 유형을 가져옵니다.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|이 중단점 요청을 설명 하는 중단점 요청 정보를 가져옵니다.|

## <a name="remarks"></a>설명
 프로그램 후 디버깅 중인 로드에 대 한 호출 [바인딩할](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 보류 중인 중단점 프로그램에서 요청 된 위치에 바인딩합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)