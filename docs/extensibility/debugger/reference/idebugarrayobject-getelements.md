---
title: IDebugArrayObject::GetElements | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 915724fa5790c6b8c9fde2706b1222db239cb4ab
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351790"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
배열의 모든 요소는 열거자를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
[out] 반환 된 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) 모든 요소를 열거할 수 있는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 대신 사용 합니다 [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) 및 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) 요소를 반복 하는 방법입니다.

## <a name="see-also"></a>참고자료
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)