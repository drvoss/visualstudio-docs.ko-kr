---
title: BP_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e07110a4ab4aae014f6134130a92dfcb8a31289
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350595"
---
# <a name="bpresolutioninfo"></a>BP_RESOLUTION_INFO
데이터 중단점 또는 코드 중단점에 대 한 바인딩된 중단점 정보를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_RESOLUTION_INFO {
    BPRESI_FIELDS          dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
} BP_RESOLUTION_INFO;
```

```csharp
public struct BP_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
};
```

## <a name="members"></a>멤버
`dwFields`\
플래그의 컬렉션을 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) 채워진 필드를 지정 하는 열거형입니다.

`bpResLocation`\
합니다 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) 코드 또는 데이터에서 중단점의 위치를 지정 하는 구조입니다.

`pProgram`\
합니다 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 중단점 오류가 발생 한 응용 프로그램을 나타내는 개체입니다.

`pThread`\
합니다 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 중단점 오류가 포함 된 응용 프로그램이 실행 되는 스레드를 나타내는 개체입니다.

## <a name="remarks"></a>설명
이 구조는 반환한 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
