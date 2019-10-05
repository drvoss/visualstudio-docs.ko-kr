---
title: BP_ERROR_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dca7dcac5dc7ccf4d30d9b61165771ba464bbcf9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351838"
---
# <a name="bperrorresolutioninfo"></a>BP_ERROR_RESOLUTION_INFO
위치, 프로그램 및 스레드를 포함 하 여 오류 중단점을 해상도 설명 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>멤버
`dwFields`\
값을 조합 합니다 [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) 채워진이 구조의 필드를 지정 하는 열거형입니다.

`bpResLocation`\
합니다 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) 중단점 해결 위치를 지정 하는 공용 구조체입니다.

`pProgram`\
합니다 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 중단점 오류가 발생 한 응용 프로그램을 나타내는 개체입니다.

`pThread`\
합니다 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 중단점 오류를 발생 시킨 응용 프로그램이 실행 되는 스레드를 나타내는 개체입니다.

`bstrMessage`\
모든 경고 또는 오류 메시지에서이 오류 해결 결과 포함 하는 문자열입니다.

`dwType`\
값을 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) 중단점 오류 형식을 지정 하는 열거형입니다.

## <a name="remarks"></a>설명
이 구조에서 반환 되는 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) 메서드.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
