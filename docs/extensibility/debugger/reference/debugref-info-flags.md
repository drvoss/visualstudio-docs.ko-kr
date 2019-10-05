---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1adab87ed09ca2ff16d837da084d8cc0b76956fe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318362"
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
디버그 참조 개체에 대 한 검색 정보를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>필드
`DEBUGREF_INFO_NAME`\
초기화/사용 된 `bstrName` 구조의 필드입니다.

`DEBUGREF_INFO_TYPE`\
초기화/사용 된 `bstrType` 구조의 필드입니다.

`DEBUGREF_INFO_VALUE`\
초기화/사용 된 `bstrValue` 구조의 필드입니다.

`DEBUGREF_INFO_ATTRIB`\
초기화/사용 된 `dwAttrib` 구조의 필드입니다.

`DEBUGREF_INFO_REFTYPE`\
초기화/사용 된 `dwRefType` 구조의 필드입니다.

`DEBUGREF_INFO_REF`\
초기화/사용 된 `pReference` 구조의 필드입니다.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
값 필드는이 형식의 개체에 대 한 사용 가능한 경우 자동 확장 값을 포함 해야 합니다.

`DEBUGREF_INFO_NONE`\
플래그가 설정 되어 있는지를 나타냅니다.

`DEBUGREF_INFO_ALL`\
플래그 마스크를 나타냅니다.

## <a name="remarks"></a>설명
이러한 플래그에 전달 되는 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) 및 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) 의 필드를 나타내는 방법을 합니다 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조는 초기화할 합니다.

에 사용 되는 합니다 `dwFields` 의 멤버는 `DEBUG_REFERENCE_INFO` 구조 반환 되 면 유효 하 고 사용 되는 필드는 구조체.

이러한 값을 비트 결합할 수 있습니다 `OR`합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
