---
title: IDebugClassField::EnumConstructors | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94a73b5f46e3e6319fef0ac2134966c4a4944279
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349630"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
이 클래스의 생성자에 대 한 열거자를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>매개 변수
`cMatch`\
[in] 값을 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) 열거형에는 생성자의 형식을 지정 하는 열거형입니다.

`ppEnum`\
[out] 반환 된 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 생성자의 목록을 나타내는 개체입니다. 생성자는 없을 경우 null 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 하거나 생성자 없음 S_FALSE를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 열거형의 각 요소는 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) constructor 메서드를 설명 하는 개체입니다.

 생성자 목록은 일반적으로 컴파일러에 의해 제공 된 기본 생성자를 포함 되지 않습니다.

## <a name="see-also"></a>참고자료
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)