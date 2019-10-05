---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ed50d43061ee714f8f892e03bb164f16e2e33d9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346379"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
검색할 메모리 컨텍스트에 대 한 정보를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="fields"></a>필드
`CIF_MODULEURL`\
초기화/사용 된 `bstrModuleUrl` 필드를 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) 구조입니다.

`CIF_FUNCTION`\
초기화/사용 된 `bstrFunction` 필드는 `CONTEXT_INFO` 구조입니다.

`CIF_FUNCTIONOFFSET`\
초기화/사용 된 `posFunctionOffset` 필드는 `CONTEXT_INFO` 구조입니다.

`CIF_ADDRESS`\
초기화/사용 된 `bstrAddress` 필드는 `CONTEXT_INFO` 구조입니다.

`CIF_ADDRESSOFFSET`\
초기화/사용 된 `bstrAddressOffset` 필드는 `CONTEXT_INFO` 구조입니다.

`CIF_ALLFIELDS`\
초기화/사용의 모든 필드는 `CONTEXT_INFO` 구조입니다.

## <a name="remarks"></a>설명
이러한 값을 매개 변수를 전달 됩니다는 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) 의 필드를 나타내려면 메서드는 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) 구조는 초기화할 합니다.

이러한 플래그는의 필드를 나타내는 데도 `CONTEXT_INFO` 구조는 유효 하 고 사용 되는 반환 하는 경우.

비트 OR 연산자를 사용 하 여 이러한 값을 결합할 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
