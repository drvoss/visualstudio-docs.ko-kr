---
title: IDebugArrayField::GetElementType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13dabbf61999e8558fe08ecb65169dd43302d98f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320953"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
배열의 요소 형식을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetElementType( 
   IDebugField** ppType
);
```

```csharp
int GetElementType(
   out IDebugField ppType
);
```

## <a name="parameters"></a>매개 변수
`ppType`\
[out] 반환 된 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 요소의 형식을 설명 하는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 합니다 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) 개체 배열의 모든 요소는 동일한 형식으로 가정 합니다.

## <a name="see-also"></a>참고자료
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)