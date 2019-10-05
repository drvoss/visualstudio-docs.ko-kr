---
title: IDebugProgram2::Step | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8030bd45850a2b81e3cfb03a83497bba77c4515c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325291"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
단계를 수행합니다.

> [!NOTE]
> 이 메서드는 사용 되지 않습니다. 사용 된 [단계](../../../extensibility/debugger/reference/idebugprocess3-step.md) 메서드 대신 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

## <a name="parameters"></a>매개 변수
`pThread`\
[in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 단계별 중인 스레드를 나타내는 개체입니다.

`sk`\
[in] 값을 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) 단계의 종류를 지정 하는 열거형입니다.

`step`\
[in] 값을 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) 지정 열거형 단계의 단위 (예를 들어, 문 또는 명령).

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 발생 한 경우 모든 스레드 동기화 또는 스레드 간 통신, 특정 스레드에서 단계별로 실행할 때 프로그램의 다른 스레드를 실행 해야 합니다.

> [!WARNING]
> Stopping 이벤트 또는 직접 (동기) 이벤트를 전송 하지 마십시오 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 이 호출을 처리 하는 동안 그렇지 않은 경우 디버거가 중단 될 수 있습니다.

## <a name="see-also"></a>참고자료
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)