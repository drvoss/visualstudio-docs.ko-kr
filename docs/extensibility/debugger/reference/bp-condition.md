---
title: BP_CONDITION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e20db594fcc00f641634bfaae8d5342d4b520d7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337433"
---
# <a name="bpcondition"></a>BP_CONDITION
중단점이 실행 되는 조건을 설명 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _BP_CONDITION {
    IDebugThread2* pThread;
    BP_COND_STYLE  styleCondition;
    BSTR           bstrContext;
    BSTR           bstrCondition;
    UINT           nRadix;
} BP_CONDITION;
```

```csharp
public struct BP_CONDITION {
    public IDebugThread2 pThread;
    public uint          styleCondition;
    public string        bstrContext;
    public string        bstrCondition;
    public uint          nRadix;
};
```

## <a name="members"></a>멤버
`pThread`\
합니다 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 중단점이 포함 된 응용 프로그램에 대 한 활성 스레드를 나타내는 개체입니다.

`styleCondition`\
값을 [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) 이 중단점 조건의 스타일을 설명 하는 열거형입니다.

`bstrContext`\
중단점의 위치입니다.

`bstrCondition`\
중단점의 발생 조건입니다.

`nRadix`\
모든 숫자 정보를 평가 하는 데 사용할 기 수입니다.

## <a name="remarks"></a>설명
이 구조체의 멤버인 합니다 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 하 고 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조입니다.

이 구조를 매개 변수로 전달 되는 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) 하 고 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) 메서드.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
