---
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 352e4bdf6c79dc67f0bf396cb1164e96e80fbf5f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337697"
---
# <a name="fieldinfo"></a>FIELD_INFO
이 구조는 지역 변수, 매개 변수 또는 다른 필드를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>멤버
`dwFields`\
플래그의 조합을 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) 채워지는 멤버를 지정 하는 열거형입니다.

`bstrFullName`\
필드의 전체 이름입니다.

`bstrName`\
필드의 짧은 이름입니다.

`bstrType`\
필드의 형식입니다.

`dwModifiers`\
플래그의 조합을 합니다 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) 필드를 설명 하는 열거형입니다.

## <a name="remarks"></a>설명
이 구조에 전달 되는 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) 메서드 위치에서 채워집니다.

## <a name="requirements"></a>요구 사항
헤더: sh.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
