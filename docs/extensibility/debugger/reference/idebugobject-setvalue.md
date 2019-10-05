---
title: IDebugObject::SetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9c6590c45027eb3dce28e2dbac182a967e87d59
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318945"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
연속 된 일련의 바이트에서 개체의 값을 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>매개 변수
`pValue`\
[in] 새 값을 나타내는 바이트 배열입니다.

`nSize`\
[in] 크기 (바이트)에서 값입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 배열의 값이 복사 됩니다 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체를 기존 값을 대체 합니다. 새 값의 크기는 기존 값 보다 작거나 클 수 있습니다. 이 `IDebugObject` null 참조일 수 없습니다.

## <a name="see-also"></a>참고자료
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)