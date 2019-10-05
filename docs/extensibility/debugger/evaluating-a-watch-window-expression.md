---
title: 조사식 창 식 평가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fe575cf0db9f6f1c2dd15da96d3d0a17648aee4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315513"
---
# <a name="evaluate-a-watch-window-expression"></a>조사식 창 식 평가
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 실행이 일시 중지 하면 Visual Studio 디버그 엔진 (DE) 해당 조사 목록에서 각 식의 현재 값을 확인 하려면를 호출 합니다. DE 각 식을 계산 하 여 식 계산기 (EE) 및 Visual Studio에서 해당 값을 표시 합니다 **조사식** 창입니다.

 다음은 목록 조사식 평가 되는 방식을 대 한 개요입니다.

1. Visual Studio 호출는 DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 식을 평가 하는 데 사용할 수 있는 식 컨텍스트를 가져오려고 합니다.

2. Visual Studio 조사 목록에서 각 식에 대 한 호출 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 식 텍스트를 구문 분석 된 식을 변환 하 합니다.

3. `IDebugExpressionContext2::ParseText` 호출 [구문 분석](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 생성 및 텍스트를 구문 분석의 실제 작업을 수행 하는 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 개체입니다.

4. `IDebugExpressionContext2::ParseText` 만듭니다는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체 및 put를 `IDebugParsedExpression` 개체입니다. 이 I`DebugExpression2` 개체 Visual Studio에 반환 됩니다.

5. Visual Studio 호출 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 구문 분석 된 식을 계산할 수 있습니다.

6. `IDebugExpression2::EvaluateSync` 에 대 한 호출을 전달 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 실제 평가 수행 하 고 생성 하는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Visual Studio에 반환 되는 개체입니다.

7. Visual Studio 호출 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 다음 조사 목록에 표시 되는 식의 값을 가져옵니다.

## <a name="parse-then-evaluate"></a>구문 분석 한 다음 평가
 복잡 한 식을 구문 분석 하는 것은 평가 하는 것 보다 훨씬 더 오래 걸릴 수 있습니다, 되므로 식을 평가 하 여 프로세스 두 단계로 세분화 됩니다. 1) 구문 분석 된 식 및 2) 구문 분석된 된 식을 평가합니다. 이러한 방식으로 평가는 여러 번 나타날 수 있지만 식을 한 번만 구문 분석 해야 합니다. 중간 구문 분석 된 식에는 EE에서 반환 되는 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 에 캡슐화 되며으로 DE에서 반환 하는 개체를 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체입니다. 합니다 `IDebugExpression` 개체를 모두 평가 지연 합니다 `IDebugParsedExpression` 개체입니다.

> [!NOTE]
> Visual Studio에서는이 가정 하는 경우에이 2 단계 프로세스를 준수 하는 EE 필요 없는 EE 구문 분석 하 고 동일한 단계에서 평가할 수 있습니다 때 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 호출 됩니다 (이것이 MyCEE 샘플의 작동 방법, 예를 들어). 언어 복잡 한 식을 형성 되는 경우에 평가 단계에서 구문 분석 단계를 구분 하는 것이 좋습니다. 여러 식을 조사할 때 Visual Studio 디버거 성능을 향상할 수 있습니다이 표시 됩니다.

## <a name="in-this-section"></a>단원 내용
 [식 계산의 샘플 구현을](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) 식 평가 프로세스를 단계별로 MyCEE 샘플을 사용 합니다.

 [조사식 창 계산](../../extensibility/debugger/evaluating-a-watch-expression.md) 를 성공적으로 식 구문 분석 한 후 어떻게 처리 되는지를 설명 합니다.

## <a name="related-sections"></a>관련 단원
 [평가 컨텍스트에](../../extensibility/debugger/evaluation-context.md) 디버그 엔진 (DE) 식 계산기 (EE)를 호출할 때 전달 되는 인수를 제공 합니다.

## <a name="see-also"></a>참고자료
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)