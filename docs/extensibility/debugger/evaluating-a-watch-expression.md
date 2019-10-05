---
title: 조사식 창 계산 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d50abb359095a727b56bf40ab0d2c7ab1155d0c6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315547"
---
# <a name="evaluate-a-watch-expression"></a>조사식 평가
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

Visual Studio 조사식 값을 표시할 준비가 되 면 호출한 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)를 호출 하 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)합니다. 이 프로세스 생성을 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 값 및 식의 형식을 포함 하는 개체입니다.

이 구현에서 `IDebugParsedExpression::EvaluateSync`, 식을 구문 분석 되 고 동시에 평가 합니다. 이 구현은 다음 작업을 수행합니다.

1. 구문 분석 하 고 해당 형식과 값을 보유 하는 일반 개체를 생성 하는 식을 계산 합니다. C#,으로 표시 됩니다는 `object` 에서 C++,으로 표시 됩니다는 `VARIANT`합니다.

2. 클래스를 인스턴스화합니다 (호출 `CValueProperty` 이 예제의)를 구현 하는 `IDebugProperty2` 인터페이스 및 클래스의 반환 값을 저장 합니다.

3. 반환 된 `IDebugProperty2` 에서 인터페이스를 `CValueProperty` 개체입니다.

## <a name="managed-code"></a>관리 코드
이 구현의 `IDebugParsedExpression::EvaluateSync` 관리 코드에서. 도우미 메서드 `Tokenize` 는 식 구문 분석 트리를 구문 분석 합니다. 도우미 함수 `EvalToken` 토큰 값으로 변환 합니다. 도우미 함수 `FindTerm` 재귀적으로 구문 분석 트리를 트래버스 호출 `EvalToken` 값을 나타내는 식의 모든 작업 (더하기 또는 빼기)를 적용 및 각 노드에 대 한 합니다.

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT EvaluateSync(
            uint evalFlags,
            uint timeout,
            IDebugSymbolProvider provider,
            IDebugAddress address,
            IDebugBinder binder,
            string resultType,
            out IDebugProperty2 result)
        {
            HRESULT retval = COM.S_OK;
            this.evalFlags = evalFlags;
            this.timeout = timeout;
            this.provider = provider;
            this.address = address;
            this.binder = binder;
            this.resultType = resultType;

            try
            {
                IDebugField field = null;
                // Tokenize, then parse.
                tokens = Tokenize(expression);
                result = new CValueProperty(
                        expression,
                        (int) FindTerm(EvalToken(tokens[0], out field),1),
                        field,
                        binder);
            }
            catch (ParseException)
            {
                result = new CValueProperty(expression, "Huh?");
                retval = COM.E_INVALIDARG;
            }
            return retval;
        }
    }
}
```

## <a name="unmanaged-code"></a>관리 되지 않는 코드
이 구현의 `IDebugParsedExpression::EvaluateSync` 비관리 코드에서. 도우미 함수 `Evaluate` 구문 분석 하 고 반환 하는 식 평가 `VARIANT` 결과 값을 보유 합니다. 도우미 함수 `VariantValueToProperty` 번들의 `VARIANT` 에 `CValueProperty` 개체입니다.

```cpp
STDMETHODIMP CParsedExpression::EvaluateSync(
    in  DWORD                 evalFlags,
    in  DWORD                 dwTimeout,
    in  IDebugSymbolProvider* pprovider,
    in  IDebugAddress*        paddress,
    in  IDebugBinder*         pbinder,
    in  BSTR                  bstrResultType,
    out IDebugProperty2**     ppproperty )
{
    // dwTimeout parameter is ignored in this implementation.
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (paddress == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    VARIANT value;
    BSTR    bstrErrorMessage = NULL;
    hr = ::Evaluate( pprovider,
                     paddress,
                     pbinder,
                     m_expr,
                     &bstrErrorMessage,
                     &value );
    if (hr != S_OK)
    {
        if (bstrErrorMessage == NULL)
            return hr;

        //we can display better messages ourselves.
        HRESULT hrLocal = S_OK;
        VARIANT varType;
        VARIANT varErrorMessage;

        VariantInit( &varType );
        VariantInit( &varErrorMessage );
        varErrorMessage.vt      = VT_BSTR;
        varErrorMessage.bstrVal = bstrErrorMessage;

        CValueProperty* valueProperty = new CValueProperty();
        if (valueProperty != NULL)
        {
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);
            if (SUCCEEDED(hrLocal))
            {
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,
                        reinterpret_cast<void**>(ppproperty) );
            }
        }

        VariantClear(&varType);
        VariantClear(&varErrorMessage); //frees BSTR
        if (!valueProperty)
            return hr;
        valueProperty->Release();
        if (FAILED(hrLocal))
            return hr;
    }
    else
    {
        if (bstrErrorMessage != NULL)
            SysFreeString(bstrErrorMessage);

        hr = VariantValueToProperty( pprovider,
                                     paddress,
                                     pbinder,
                                     m_radix,
                                     m_expr,
                                     value,
                                     ppproperty );
        VariantClear(&value);
        if (FAILED(hr))
            return hr;
    }

    return S_OK;
}
```

## <a name="see-also"></a>참고자료
- [조사식 창 식 평가](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [식 계산의 샘플 구현](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
