---
title: BP_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 31f5153c3a2d0b55829a7743840fe8a791f023d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319219"
---
# <a name="bpflags"></a>BP_FLAGS
중단점을 설정 하는 경우 추가 정보를 지정 하는 데 사용할 수 있는 선택적 플래그를 제공 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>필드
`BP_FLAG_NONE`\
중단점 플래그가 지정합니다.

`BP_FLAG_MAP_DOCPOSITION`\
디버그 엔진 (DE) 문서 위치를 사용 하 여 중단점을 매핑해야를 지정 합니다. 스크립트 기반 소스 파일 등 ASP Active Server Pages ()에서 설정 된 중단점에만 적용 됩니다.

`BP_FLAG_DONT_STOP`\
중단점 디버그 엔진에 의해 처리 되어야 한다는 디버그 엔진 궁극적으로 중지 되지 있습니다 지정 (즉,는 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) 이벤트 개체 보내지 않아야). 이 플래그는 추적점이 들어 있는 기본적으로 사용 하도록 설계 되었습니다.

## <a name="remarks"></a>설명
에 사용 되는 합니다 `dwFlags` 의 멤버는 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 및 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조입니다.

이러한 값을 비트 결합할 수 있습니다 `OR`합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
