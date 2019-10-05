---
title: IDebugObject::SetReferenceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aaef4eb96942789bd3f574e6eeddcd3500ae6ee9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349948"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
이 개체의 참조 값을 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>매개 변수
`pObject`\
[in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 새 참조 값을 나타내는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드를 사용 하면이 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체에 지정 된 개체의 값에 대 한 참조를 `pObject` 이전 참조를 버리는 매개 변수입니다. 참고가 `IDebugObject` 개체 참조 형식이 있어야 합니다.

## <a name="see-also"></a>참고자료
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)