---
title: BPRESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82a286bea92c778ab150cacdc80d79f8ac283469
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350475"
---
# <a name="bpresifields"></a>BPRESI_FIELDS
중단점을 해결 하는 방법에 대 한 검색할 정보를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="fields"></a>필드
`BPRESI_BPRESLOCATION`\
초기화/사용 합니다 `bpResLocation` (중단점 해결 위치) 필드를 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 구조입니다.

`BPRESI_PROGRAM`\
초기화/사용 된 `pProgram` 필드는 `BP_RESOLUTION_INFO` 구조입니다.

`BPRESI_THREAD`\
초기화/사용 된 `pThread` 필드는 `BP_RESOLUTION_INFO` 구조입니다.

`BPRESI_ALLFIELDS`\
모든 필드를 지정합니다.

## <a name="remarks"></a>설명
에 전달 합니다 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) 의 필드를 표시 하는 방법을 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 구조는 초기화할 합니다.

이러한 플래그는의 필드를 나타내는 데도 `BP_RESOLUTION_INFO` 구조는 유효 하 고 사용 되는 해당 구조를 반환할 때.

이러한 값을 비트 결합할 수 있습니다 `OR`합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
