---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01853df78bfe731ea4b7159f7b3ebe352f3c5eaa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337681"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
에 대 한 검색 정보를 지정 된 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다.

## <a name="syntax"></a>구문

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="fields"></a>필드
`FIF_FULLNAME`\
초기화/사용 된 `bstrFullName` 필드를 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 구조입니다.

`FIF_NAME`\
초기화/사용 된 `bstrName` 필드에 `FIELD_INFO` 구조입니다.

`FIF_TYPE`\
초기화/사용 된 `bstrType` 필드에 `FIELD_INFO` 구조입니다.

`FIF_MODIFIERS`\
초기화/사용 된 `bstrModifiers` 필드에 `FIELD_INFO` 구조입니다.

## <a name="remarks"></a>설명
이러한 값을 인수로 전달도 됩니다는 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) 의 필드를 지정 하는 메서드는 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 구조는 초기화할.

이러한 값에도 사용 됩니다 합니다 `dwFields` 의 멤버는 `FIELD_INFO` 에 유효 하 고 사용 되는 필드는 구조체.

이러한 플래그는 비트과 결합 될 수 `OR`입니다.

## <a name="requirements"></a>요구 사항
헤더: sh.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
