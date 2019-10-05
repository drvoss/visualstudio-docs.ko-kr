---
title: IDebugPointerObject::Dereference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 381c6f392cccb398497204cc5772c5f9a00fd5b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331652"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
가리키는 개체를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>매개 변수
`dwIndex`\
[in] 개체의 시작 부분에서 간단한 바이트 오프셋을 지정 합니다.

`ppObject`\
[out] 반환 된 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 있으면를 가리키는 plus 오프셋을 나타내는 개체를 개체.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다. 이 개체가 다른 개체를 가리키지 않을 경우 E_FAIL을 반환 합니다.

## <a name="remarks"></a>설명
 기본 형식 또는 클래스 또는 구조체와 같은 보다 복잡 한 형식을 가리키는 개체가 수 있습니다.

## <a name="see-also"></a>참고자료
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)