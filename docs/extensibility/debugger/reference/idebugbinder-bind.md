---
title: IDebugBinder::Bind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00d7e63b8a521ee25d2c7d378aeb82d064358ec9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344500"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
이 메서드는 메모리 컨텍스트 또는 기호의 현재 값이 포함 된 개체를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>매개 변수
`pContainer`\
[in] 합니다 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 자식에서 참조를 포함 하는 `pField`합니다.

`pField`\
[in] 합니다 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 기호를 나타내는입니다.

`ppObject`\
[out] 반환 된 `IDebugObject` 기호의 인스턴스를 나타내는입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고자료
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)