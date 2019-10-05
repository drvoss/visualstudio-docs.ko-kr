---
title: 식 평가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39b2af1cdf299b3e3f2c714fa569fa295a4e1d4e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315421"
---
# <a name="evaluate-expressions"></a>식 평가
식에서 전달 하는 문자열에서 만든 합니다 **자동**, **조사식**, **간략 한 조사식**, 또는 **직접 실행** windows. 식을 계산할 때 이름과 변수 또는 인수 및 해당 값의 형식을 포함 하는 인쇄 가능한 문자열을 생성 합니다. 이 문자열은 해당 IDE 창에 표시 됩니다.

## <a name="implementation"></a>구현
 중단점에서 프로그램을 중지 하는 경우 식이 계산 됩니다. 식 자체 표시 되는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스 바인딩 및 지정 된 식 평가 컨텍스트 내에서 평가 위한 준비 된 구문 분석 된 식을 나타냅니다. 스택 프레임을 구현 하 여 디버그 엔진 (DE)를 제공 하는 식 계산 컨텍스트를 결정 합니다 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스입니다.

 사용자 문자열을 지정 및 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스는 디버그 엔진 (DE) 가져올 수는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 사용자 문자열을 전달 하 여 인터페이스를 [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드. 반환 되는 IDebugExpression2 인터페이스를 구문 분석된 된 식을 평가 위한 준비를 포함 합니다.

 사용 하 여 합니다 `IDebugExpression2` 인터페이스는 DE 동기 또는 비동기 식 평가 통해 식의 값을 가져올 수를 사용 하 여 [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)합니다. 이름 및 형식의 변수 또는 인수를 함께이 값을 표시 하기 위해 IDE에 전송 됩니다. 값, 이름 및 형식으로 표시 됩니다는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스입니다.

 식 계산을 사용 하도록 설정 하는 DE 구현 해야 합니다 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 하 고 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스입니다. 동기 및 비동기 계산의 구현이 필요 합니다 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 메서드.

## <a name="see-also"></a>참고자료
- [스택 프레임](../../extensibility/debugger/stack-frames.md)
- [식 계산 컨텍스트](../../extensibility/debugger/expression-evaluation-context.md)
- [작업 디버그](../../extensibility/debugger/debugging-tasks.md)