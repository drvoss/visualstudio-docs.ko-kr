---
title: IDebugPointerField::GetDereferencedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fef8ee4e584703338afd09e5303ac184f28b3a49
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331620"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
이 메서드는이 포인터 개체가 가리키는 개체의 형식을 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>매개 변수
`ppField`\
[out] 반환 된 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 대상 개체의 형식을 설명 하는 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 예를 들어, 합니다 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) 개체는 정수를 가리킵니다 합니다 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 이 메서드에서 반환 되는 형식을 해당 정수 형식에 설명 합니다.

## <a name="see-also"></a>참고자료
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)