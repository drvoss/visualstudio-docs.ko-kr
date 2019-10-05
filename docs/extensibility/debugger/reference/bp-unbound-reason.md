---
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9de6812f3a61feca8ca8e7153fb281369c3312bd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350561"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
중단점이 바인딩된 없습니다. 이유를 제공 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
typedef DWORD BP_UNBOUND_REASON;
```

```csharp
public enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
```

## <a name="fields"></a>필드
`BPUR_UNKNOWN`\
알 수 없는 이유입니다.

`BPUR_CODE_UNLOADED`\
중단점을 포함 하는 코드는 언로드 되었습니다.

`BPUR_BREAKPOINT_REBIND`\
다른 위치에 다시 바인딩 중단점. 이 편집 후 발생 하 고 중단점 움직이면 또는 더 이상 유효 경로 사용 하 여 파일 중단점이 바인딩될 때 작업을 계속 수 없습니다.

`BPUR_ BREAKPOINT_ERROR`\
중단점이 바인딩된 후 오류에 포함 되도록 결정 됩니다. 이 관리 되는 중단점 조건이 더 이상 유효 합니다.

## <a name="remarks"></a>설명
반환 된 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) 메서드.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
