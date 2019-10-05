---
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ec8b26f422ca39b771a47f8eb60ee862d7d388f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62568371"
---
# <a name="idebugexpression2"></a>IDebugExpression2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스 바인딩 및 평가 대 한 구문 분석 된 식을 준비를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진 (DE)를 구문 분석 된 식을 계산할 준비가 나타낼이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 에 대 한 호출 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 이 인터페이스를 반환 합니다. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 반환 된 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스입니다. 이러한 인터페이스는 디버그 중인 프로그램 일시 중지 된 스택 프레임은 사용할 수 있는 경우에 액세스할 수 있습니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugExpression2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|이 식을 비동기적으로 계산합니다.|  
|[Abort](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|비동기 식 평가 종료 합니다.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|이 식을 동기적으로 계산합니다.|  
  
## <a name="remarks"></a>설명  
 세션 디버그 관리자 (SDM) 호출 하 여 독일에서 스택 프레임을 가져옵니다 프로그램을 중지 하는 경우 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)합니다. SDM 호출 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 가져오려고 합니다 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스입니다. 에 대 한 호출 뒤에 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 만들려는 `IDebugExpression2` 평가할 준비가 구문 분석된 된 식을 나타내는 인터페이스입니다.  
  
 SDM을 호출 하거나 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 실제로 식을 평가 하 고 값을 생성 합니다.  
  
 구현에서 `IDebugExpressionContext2::ParseText`는 DE COM의 사용 `CoCreateInstance` 함수를 식 계산기를 인스턴스화하고 가져오기는 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) 인터페이스 (의 예제를 참조는 `IDebugExpressionEvaluator` 인터페이스). 그런 다음 호출 하는 DE [구문 분석](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 가져오려고는 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) 인터페이스입니다. 이 인터페이스의 구현에서 사용 됩니다 `IDebugExpression2::EvaluateSync` 고 `IDebugExpression2::EvaluateAsync` 평가를 수행 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
