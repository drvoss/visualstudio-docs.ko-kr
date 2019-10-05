---
title: IDebugMethodField::GetThis | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 426fc0c74b44b1f137752814f9b6aaeff150baa8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324060"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
가져옵니다 합니다 `this` (`Me` 에서 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) 메서드를 포함 하는 개체의 포인터입니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>매개 변수
`ppClass`\
[out] 반환 된 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) "this"이 포인터를 나타내는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 개체 지향 언어의 경우 일반적으로 클래스는 현재 인스턴스화에 대 한 암시적된 포인터 이 이라고 `this` 에서 C#/C++ 와 `Me` 에서 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]합니다.

## <a name="see-also"></a>참고자료
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)