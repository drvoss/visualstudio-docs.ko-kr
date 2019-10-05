---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: faa2767e54e9821c7b3270fa60f5be232a2c232f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325762"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
이 메서드는 메모리 주소에 메서드 위치 및 오프셋을 변환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>매개 변수
`upstrFullyQualifiedMethodPlusOffset`\
[in] 문자열로 표현 된 메서드 위치와 오프셋을 합니다.

`pSymbolProvider`\
[in] 기호 공급자로 표현 되는 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 개체입니다.

`pAddress`\
[in] 로 표현 된 메서드 내에서 주소를 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체입니다.

`pBinder`\
[in] 바인더로 표현 되는 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 개체입니다.

`ppProperty`\
[out] 반환 된 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 메모리 주소를 나타내는 인터페이스입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 예를 들어 중단점을 설정 하는 반환 된 주소를 사용할 수 있습니다.

 이름이 `upstrFullyQualifiedMethodPlusOffset`,이 매개 변수는 부분적으로 정규화 된 메서드 이름이 전달 될 수 있습니다. 이 경우 선택한 방법은 둘러싸는 것 `pAddress`입니다. 이 매개 변수를 해석 하는 방법을 하는 것은 식 계산기 및 지 원하는 언어의 구현에 달려 있습니다.

## <a name="see-also"></a>참고자료
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)