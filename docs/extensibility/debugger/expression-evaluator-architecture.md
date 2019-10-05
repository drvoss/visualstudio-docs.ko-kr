---
title: 식 계산기 아키텍처 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42c52e3d6b71b58668a05434e9ca8f65eb3e7832
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353754"
---
# <a name="expression-evaluator-architecture"></a>식 계산기 아키텍처
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 Visual Studio 디버그 패키지 있습니다 의미 전용 언어 통합 필수 식 계산기 (EE) 인터페이스를 설정 하 고 공용 언어 런타임 기호 공급자 (SP) 및 바인더 인터페이스를 호출 해야 합니다. SP 및 바인더 개체를 현재 실행 주소와 함께 식이 계산 되는 컨텍스트입니다. 이러한 인터페이스를 만들고 사용 하는 정보는 EE의 아키텍처의 주요 개념을 나타냅니다.

## <a name="overview"></a>개요

### <a name="parse-the-expression"></a>식을 구문 분석
 프로그램을 디버깅 하는 여러 가지 이유가 있지만 항상 디버그 중인 프로그램 (사용자가 배치 중단점 또는 예외로 인해 발생 하나) 중단점에서 중지 된 경우 식 평가 됩니다. 에 표시 된 대로 Visual Studio의 스택 프레임을 가져오는 경우 지금은는 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 디버그 엔진 (DE)에서 인터페이스입니다. Visual Studio 호출 [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 가져오려고 합니다 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스입니다. 이 인터페이스는 식을 계산할 수 있습니다; 컨텍스트를 나타냅니다. [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 평가 프로세스의 진입점입니다. 이 시점까지 모든 인터페이스는 DE 여 구현 됩니다.

 때 `IDebugExpressionContext2::ParseText` 가 호출 되는 DE 중단점이 발생 한 원본 파일의 언어와 관련 된 EE를 인스턴스화합니다 (의 DE도 인스턴스화합니다을 SH이 시점에서). EE은 표현 합니다 [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) 인터페이스입니다. 그런 다음 호출 하는 DE [구문 분석](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 평가 위해 준비 된 (텍스트 형태로) 식을 구문 분석 된 식으로 변환할 합니다. 이 구문 분석 된 식으로 표시 됩니다는 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 인터페이스입니다. 식은은 일반적으로 구문 분석 되 고이 시점에서 평가 되지 됩니다.

 DE 구현 하는 개체를 만듭니다는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스를 넣습니다를 `IDebugParsedExpression` 개체를 `IDebugExpression2` 개체를 반환 합니다 `IDebugExpression2` 에서 개체 `IDebugExpressionContext2::ParseText`.

### <a name="evaluate-the-expression"></a>식 평가
 Visual Studio에서 호출 하거나 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 또는 [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 구문 분석 된 식을 계산할 수 있습니다. 두이 방법 모두 호출 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` 메서드를 호출 하는 동안 즉시 `IDebugExpression2::EvaluateAsync` 백그라운드 스레드를 통해 메서드 호출) 구문 분석된 된 식을 평가 하 고 반환는 [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 구문 분석 된 식의 형식과 값을 나타내는 인터페이스입니다. `IDebugParsedExpression::EvaluateSync` 제공 된 SH, 주소 및 바인더를 사용 하 여 구문 분석된 된 식을 나타내는 실제 값을 변환 하는 `IDebugProperty2` 인터페이스입니다.

### <a name="for-example"></a>예
 실행 중인 프로그램에 중단점이 적중 된 후 사용자가 변수를 보려면 선택 합니다 **간략 한 조사식** 대화 상자. 이 대화 상자에는 변수의 이름, 해당 값 및 해당 형식을 보여 줍니다. 일반적으로 사용자 값을 변경할 수 있습니다.

 경우는 **간략 한 조사식** 대화 상자를 표시, 검사 되 고 변수 이름을 텍스트로 보내집니다 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)합니다. 반환 합니다.는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 변수,이 경우 구문 분석된 된 식을 나타내는 개체입니다. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 호출을 생성 한 다음는 `IDebugProperty2` 이름 뿐만 아니라 변수의 값 및 형식을 나타내는 개체입니다. 표시 되는이 정보는 것입니다.

 사용자가 해당 변수의 값을 변경 하면 [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) 프로그램 다시 시작 될 때 사용 되므로 메모리에 변수의 값을 변경 하는 새 값을 사용 하 여 라고 실행 합니다.

 참조 [표시 지역](../../extensibility/debugger/displaying-locals.md) 변수의 값을 표시 하는이 프로세스에 대 한 자세한 내용은 합니다. 참조 [로컬 값을 변경](../../extensibility/debugger/changing-the-value-of-a-local.md) 변수의 값이 변경 하는 방법에 대 한 자세한 내용은 합니다.

## <a name="in-this-section"></a>단원 내용
 [평가 컨텍스트에](../../extensibility/debugger/evaluation-context.md) 는 DE EE를 호출할 때 전달 되는 인수를 제공 합니다.

 [식 계산기 인터페이스 키](../../extensibility/debugger/key-expression-evaluator-interfaces.md) 함께 평가 컨텍스트에 EE를 작성할 때 필요한 중요 한 인터페이스를 설명 합니다.

## <a name="see-also"></a>참고자료
- [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [로컬 항목 표시](../../extensibility/debugger/displaying-locals.md)
- [로컬 값을 변경](../../extensibility/debugger/changing-the-value-of-a-local.md)