---
title: 식 계산 (Visual Studio 디버깅 SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f2a84f01168dd01921d933a80fe052c1a6c6447
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562213"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>식 계산(Visual Studio 디버깅 SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

중단 모드에서 IDE 프로그램의 여러 변수가 포함 된 간단한 식을 계산할 수 있어야 합니다. 이를 위해 디버그 엔진 (DE) 구문 분석 하 고 IDE의 창 중 하나에 입력 한 식을 계산할 수 있어야 합니다.  
  
 식을 사용 하 여 만들어집니다 합니다 [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 되며 메서드 결과 표시 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스입니다.  
  
 **IDebugExpression2** DE 및 호출 인터페이스를 구현 해당 **EvalAsync** 반환 하는 메서드를 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 표시 하기 위해 IDE는 IDE에서 식 계산의 결과입니다. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 조사식 창 또는 지역 창에는 식의 값을 입력 하는 구조체를 반환 합니다.  
  
 디버그 패키지 또는 세션 디버그 관리자 (SDM) 호출 [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 하거나 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 가져오려는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 나타내는 인터페이스 평가의 결과입니다. `IDebugProperty2` 에 이름, 형식 및 식의 값을 반환 하는 메서드가 있습니다. 이 정보는 다양 한 디버거 창에 표시 됩니다.  
  
## <a name="using-expression-evaluation"></a>식 계산을 사용 하 여  
 식 계산을 사용 하려면 구현 해야 합니다는 [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드와 모든 메서드는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 다음 표에 나와 있는 것 처럼 인터페이스입니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|비동기적으로 식을 계산합니다.|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|비동기 식 평가 종료 합니다.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|동기적으로 식을 계산합니다.|  
  
 동기 및 비동기 계산의 구현이 필요 합니다 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 메서드. 비동기 식 계산의 구현이 필요 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
