---
title: IDebugBinder::ResolveRuntimeType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2954b5f2a1ac4dd14485a1b924423ba53fddcb7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315159"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
이 메서드는 개체의 런타임 형식을 결정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ResolveRuntimeType( 
   IDebugObject* pObject,
   IDebugField** ppResolved
);
```

```csharp
int ResolveRuntimeType(
   IDebugObject     pObject,
   out IDebugField  ppResolved
);
```

## <a name="parameters"></a>매개 변수
`pObject`\
[in] 합니다 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 를 해결할 수 있습니다.

`ppResolved`\
[out] 개체의 형식을 반환 합니다는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 컴파일 타임에 개체의 런타임 형식은 항상 알 수는 없습니다. 예를 들어 다형성을 사용 하 여 인수로 전달할 수 있습니다 함수 단추 클래스 등의 기본 클래스로. 실제 인수의 라디오 단추 클래스와 같은 파생된 클래스를 수 있습니다.

## <a name="see-also"></a>참고자료
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)