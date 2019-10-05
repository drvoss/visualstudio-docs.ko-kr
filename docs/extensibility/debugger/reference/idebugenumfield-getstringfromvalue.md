---
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd7466e5390cff747532dca0343680cf359db46a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345083"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
이 메서드는 해당 값을 지정 된 열거형 상수의 이름을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>매개 변수
`value`\
[in] 열거형의 이름을 상수 가져올 값입니다.

`pbstrValue`\
[out] 열거형 상수의 이름을 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE` 값에 연결 된 이름은 또는 오류 코드를 반환 하는 경우.

## <a name="remarks"></a>설명
 동일한 값과 연결 된 이름을 여러 개 있으면 열거형에 정의 된 이름이 반환 됩니다.

## <a name="see-also"></a>참고자료
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)