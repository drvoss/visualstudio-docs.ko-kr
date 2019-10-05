---
title: IDebugExpressionContext2::ParseText | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 170183924c31933f77903a89851c15c463c326e6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325906"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
이후 평가 대 한 텍스트 형태로 식을 구문 분석합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2** ppExpr,
    BSTR*               pbstrError,
    UINT*               pichError
);
```

```csharp
int ParseText(
    string                pszCode,
    enum_PARSEFLAGS       dwFlags,
    uint                  nRadix,
    out IDebugExpression2 ppExpr,
    out string            pbstrError,
    out uint              pichError
);
```

## <a name="parameters"></a>매개 변수
`pszCode`\
[in] 구문 분석할 식입니다.

`dwFlags`\
[in] 플래그의 조합 된 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) 구문 분석을 제어 하는 열거형입니다.

`nRadix`\
[in] 숫자 정보를 구문 분석 하는 데 사용할 기 수 `pszCode`입니다.

`ppExpr`\
[out] 반환 된 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) 바인딩 및 평가 되지 않은 구문 분석된 된 식을 나타내는 개체입니다.

`pbstrError`\
[out] 식에 오류가 포함 된 오류 메시지를 반환 합니다.

`pichError`\
[out] 오류 메시지의 문자 인덱스를 반환 `pszCode` 식에 오류가 포함 되어 있습니다.

## <a name="return-value"></a>반환 값
성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
이 메서드를 호출 하는 경우 디버그 엔진 (DE) 식을 구문 분석 하 고 올바른지 유효성을 검사 해야 합니다. 합니다 `pbstrError` 고 `pichError` 식이 유효 하지 않은 경우 매개 변수를 채울 수 있습니다.

Note 구문 분석만 식이 계산 됩니다. 이후의 호출을 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 하거나 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 메서드 구문 분석 된 식을 계산 합니다.

## <a name="example"></a>예제
다음 예제에서는 간단한에 대 한이 메서드를 구현 하는 방법을 보여 줍니다 `CEnvBlock` 노출 하는 개체를 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스입니다. 이 예제에서는 환경 변수의 이름으로 구문 분석할 식으로 간주 하 고 해당 변수에서 값을 검색 합니다.

```cpp
HRESULT CEnvBlock::ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2 **ppExpr,
    BSTR               *pbstrError,
    UINT               *pichError)
{
    HRESULT hr = E_OUTOFMEMORY;
    // Create an integer variable with a value equal to one plus
    // twice the length of the passed expression to be parsed.
    int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;
    // Allocate a character string of the same length.
    char *pszAnsiCode = (char *) malloc(iAnsiLen);

    // Check for successful memory allocation.
    if (pszAnsiCode) {
        // Map the wide-character pszCode string to the new pszAnsiCode character string.
        WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);
        // Check to see if the app can succesfully get the environment variable.
        if (GetEnv(pszAnsiCode)) {

            // Create and initialize a CExpression object.
            CComObject<CExpression> *pExpr;
            CComObject<CExpression>::CreateInstance(&pExpr);
            pExpr->Init(pszAnsiCode, this, NULL);

            // Assign the pointer to the new object to the passed argument
            // and AddRef the object.
            *ppExpr = pExpr;
            (*ppExpr)->AddRef();
            hr = S_OK;
        // If the program cannot succesfully get the environment variable.
        } else {
            // Set the errror message and return E_FAIL.
            *pbstrError = SysAllocString(L"No such environment variable.");
            hr = E_FAIL;
        }
        // Free the local character string.
        free(pszAnsiCode);
    }
    return hr;
}
```

## <a name="see-also"></a>참고자료
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
