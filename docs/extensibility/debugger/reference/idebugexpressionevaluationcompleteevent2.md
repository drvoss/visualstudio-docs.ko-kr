---
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5af187e04096fdd16dc5a371f49953fae2e61621
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325726"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
이 인터페이스는 비동기 식 계산이 완료 되 면 세션 디버그 관리자 (SDM)에 디버그 엔진 (DE)에서 전송 됩니다.

## <a name="syntax"></a>구문

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 호출 하 여 시작 하는 식 평가의 보고서 완료 하기 위해이 인터페이스를 구현 하는 DE [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)합니다. 합니다 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 이 인터페이스와 동일한 개체에서 인터페이스를 구현 해야 합니다. SDM 사용 [QueryInterface](/cpp/atl/queryinterface) 액세스는 `IDebugEvent2` 인터페이스입니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 DE을 만들고이 이벤트 개체는 식 평가의 완료를 보고를 보냅니다. 이벤트를 사용 하 여 전송 되는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 디버깅 중인 프로그램에 연결할 때 SDM에서 제공 하는 콜백 함수.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugExpressionEvaluationCompleteEvent2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|원래 식을 가져옵니다.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|식 평가의 결과를 가져옵니다.|

## <a name="remarks"></a>설명
 DE 평가 성공 여부에 관계 없이이 이벤트를 전송 해야 합니다.

 평가 하지 못한 경우에 `DEBUG_PROPINFO_VALUE` 및 `DEBUG_PROPINFO_ATTRIB` 플래그를 설정할 수는 합니다 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 에서 반환 되는 구조 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (합니다 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 는 DE 하 여 개체를 만들어 반환 합니다 `IDebugExpressionEvaluationCompleteEvent2` 이벤트 평가 실패 한 경우).

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)