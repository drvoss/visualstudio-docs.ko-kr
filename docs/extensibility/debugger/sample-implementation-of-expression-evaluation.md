---
title: 식 계산의 구현 샘플 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0135c8dd61ca2505c1458bc157b574e6bcbee09a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315079"
---
# <a name="sample-implementation-of-expression-evaluation"></a>식 계산의 샘플 구현
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 에 대 한는 **Watch** 창 식, Visual Studio 호출 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 생성 하는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 개체입니다. `IDebugExpressionContext2::ParseText` 식 계산기 (EE) 및 호출 인스턴스화합니다 [구문 분석](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 가져오려는 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 개체입니다.

 `IDebugExpressionEvaluator::Parse` 다음 작업을 수행 합니다.

1. [C++ 만] 오류가 있는지 확인 하는 식 구문 분석 합니다.

2. 클래스를 인스턴스화합니다 (호출 `CParsedExpression` 이 예제의)를 실행 하는 `IDebugParsedExpression` 인터페이스 및 구문 분석할 식 클래스에 저장 합니다.

3. 반환 된 `IDebugParsedExpression` 에서 인터페이스를 `CParsedExpression` 개체입니다.

> [!NOTE]
> 이 예제에서는 MyCEE 샘플에서는 식 계산기 계산에서 구문 분석을 분리 하지 않습니다.

## <a name="managed-code"></a>관리 코드
 다음 코드의 구현을 보여 줍니다. `IDebugExpressionEvaluator::Parse` 관리 코드에서. 이 버전의 메서드를 구문 분석 하는 지연 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 구문 분석에 대 한 코드를 동시에 평가 하는 대로 (참조 [조사식 평가](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>관리 되지 않는 코드
다음 코드는 구현의 `IDebugExpressionEvaluator::Parse` 비관리 코드에서. 이 메서드는 도우미 함수를 호출 `Parse`, 식 및 오류에 대 한 검사를 구문 분석 하지만이 메서드는 결과 값을 무시 합니다. 공식적인 평가으로 지연 됩니다 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 평가 하는 동안 식을 구문 분석 되는 (참조 [조사식 평가](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>참고자료
- [조사식 창 식 평가](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [조사식 평가](../../extensibility/debugger/evaluating-a-watch-expression.md)