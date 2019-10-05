---
title: EVENTATTRIBUTES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3361d27a9e0a4a1f56035c0d2af20d9fa9a9303
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337765"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
이벤트 특성을 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>필드
`EVENT_ASYNCHRONOUS`\
이 이벤트는 비동기 이벤트에 응답 하지 필요 함을 나타냅니다.

`EVENT_SYNCHRONOUS`\
이벤트 동기; 임을 나타냅니다. 이용 하 여 회신 [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)합니다.

`EVENT_STOPPING`\
이 stopping 이벤트를 나타냅니다. 사용 하 여 결합 해야 `EVENT_ASYNCHRONOUS` 또는 `EVENT_SYNCHRONOUS`합니다.

`EVENT_ASYNC_STOP`\
비동기 중지 이벤트를 나타냅니다. 이런 이벤트가 현재입니다. 이 플래그는 자리 표시자만 합니다.

`EVENT_SYNC_STOP`\
동기 중지 이벤트를 나타냅니다 (조합을 `EVENT_SYNCHRONOUS` 고 `EVENT_STOPPING`). 이 값은 중지 이벤트를 보낼 때 디버그 엔진 (DE)에 의해 사용 됩니다. 회신을 호출 하 여 이루어집니다 [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)를 [단계](../../../extensibility/debugger/reference/idebugprogram2-step.md), 또는 [계속](../../../extensibility/debugger/reference/idebugprogram2-continue.md)합니다.

`EVENT_IMMEDIATE`\
IDE에 즉시 하 고 동기적으로 전송 되는 이벤트를 나타냅니다. 이 플래그와 같은 다른 플래그와 함께 결합 `EVENT_ASYNCHRONOUS`, `EVENT_SYNCHRONOUS`, 또는 `EVENT_SYNC_STOP` 이벤트 및 응답 메커니즘 (있는 경우) 라고 팩트 유형을 지정 하는 합니다.

`EVENT_EXPRESSION_EVALUATION`\
이벤트 식 평가의 결과입니다.

## <a name="remarks"></a>설명
이러한 값에 전달 되는 `dwAttrib` 의 매개 변수를 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 메서드.

이러한 값을 비트 결합할 수 있습니다 `OR`합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
