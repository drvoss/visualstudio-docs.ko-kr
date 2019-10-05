---
title: IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d965161f6f0a6aadd8aab89a3001e56c2e807fa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325701"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
이 메서드는 지역 변수, 인수 및 기타 속성 메서드를 포함 하는 속성 개체를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMethodProperty( 
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BOOL                  fIncludeHiddenLocals,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodProperty(
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   int                  fIncludeHiddenLocals,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>매개 변수
`pSymbolProvider`\
[in] 사용할 기호 공급자로 표현 되는 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 개체입니다.

`pAddress`\
[in] 로 표현 하는 코드에서 주소를 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체를 포함 하는 가장 가까운 확인 해야 하는 함수입니다.

`pBinder`\
[in] 사용할 바인더로 표현 되는 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 개체입니다.

`fIncludeHiddenLocals`\
[in] 0이 아닌 값 (`TRUE`) 숨겨진된 지역;를 포함 하는 의미 0 (`FALSE`) 숨겨진된 지역 변수를 생략 하는 의미

`ppProperty`\
[out] 반환 된 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 메서드를 나타내는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 숨겨진된 지역 변수는 일반적으로 컴파일러에서 생성 되는 변수.

## <a name="see-also"></a>참고자료
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)