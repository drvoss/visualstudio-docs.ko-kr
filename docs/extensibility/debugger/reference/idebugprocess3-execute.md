---
title: IDebugProcess3::Execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b4b854c752bc7b1f66687074fbfe86286fc48fb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314009"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
계속 중지 된 상태에서이 프로세스를 실행 합니다. 이전 실행 상태 (예: 단계)를 지우고 다시 실행 프로세스를 시작 합니다.

> [!NOTE]
> 이 메서드를 대신 사용 해야 [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>매개 변수
`pThread`\
[in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 스레드의 실행을 나타내는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 다른 프로세스의 스레드 중지 된 상태에서 실행을 시작할 때이 메서드는이 프로세스에서 호출 됩니다. 이 또한 메서드는 사용자가 선택 합니다 **시작** 명령을 합니다 **디버그** IDE의 메뉴. 이 메서드의 구현을 호출 처럼 간단할 수 있습니다 합니다 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 프로세스에서 현재 스레드에서 메서드.

> [!WARNING]
> Stopping 이벤트 또는 직접 (동기) 이벤트를 전송 하지 마십시오 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 이 호출을 처리 하는 동안 그렇지 않은 경우 디버거가 중단 될 수 있습니다.

## <a name="see-also"></a>참고자료
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)