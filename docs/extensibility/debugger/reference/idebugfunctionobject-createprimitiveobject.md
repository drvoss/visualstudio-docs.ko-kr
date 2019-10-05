---
title: IDebugFunctionObject::CreatePrimitiveObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d47f3edfffadc74791d6d6b2267a37319a053d7d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320822"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
간단한 integer와 같은 기본 데이터 개체를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreatePrimitiveObject( 
   OBJECT_TYPE    ot,
   IDebugObject** ppObject
);
```

```csharp
int CreatePrimitiveObject(
   enum_OBJECT_TYPE ot,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>매개 변수
`ot`\
[in] 값을 [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) 만들려면 기본 형식을 나타내는 열거형입니다.

`ppObject`\
[out] 반환 된 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 새로 만든된 개체를 나타내는입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 으로 표현 되는 함수에 매개 변수는 기본 개체를 나타내는 개체를 만들려면이 메서드를 호출 합니다 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 인터페이스입니다. 예를 들어, "myString(5)" 식 문자열을 사용 하는 경우이 메서드는 데 사용할 5 정수를 나타내는 개체를 만듭니다.

## <a name="see-also"></a>참고자료
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)