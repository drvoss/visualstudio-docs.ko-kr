---
title: 지원 되는 이벤트 유형 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c4ee45e1a3a7efeb990fcb6f9073420a99dbe7c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351087"
---
# <a name="supported-event-types"></a>지원 되는 이벤트 유형
현재 visual Studio 디버깅 다음 이벤트 유형을 지원합니다.

- 비동기 이벤트

   (SDM)의 세션 디버그 관리자에 게 알림 및 디버깅 중인 응용 프로그램의 상태가 변경 되는 IDE입니다. 이러한 이벤트는 SDM 및 IDE 레저에서 처리 됩니다. 이벤트를 처리 한 후 회신이 없으면 디버그 엔진 (DE)에 전송 됩니다. [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) 하 고 [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) 인터페이스는 비동기 이벤트의 예입니다.

- 동기 이벤트

   SDM 및 디버깅 중인 응용 프로그램의 상태가 변경 되는 IDE에 게 알립니다. 이러한 이벤트와 비동기 이벤트 간의 유일한 차이점은 회신을 이용 하 여 전송 되지 않는다는 합니다 [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) 메서드.

   동기 이벤트를 전송 하는 것은 사용자 DE IDE 수신 하 고 이벤트를 처리 하는 후 처리를 계속 하려면 필요한 경우에 유용 합니다.

- 동기 이벤트를 중지 또는 중지 이벤트

   알림 SDM 및 IDE 디버깅 중인 응용 프로그램 코드를 실행을 중지 했습니다. 메서드를 사용 하 여 중지 이벤트를 보낼 때 [이벤트](../../extensibility/debugger/reference/idebugeventcallback2-event.md)서 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 매개 변수는 필수입니다. 중지 이벤트는 다음 방법 중 하나를 호출 하 여 계속 합니다.

  - [Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    인터페이스 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 하 고 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) 은 중지 이벤트의 예입니다.

  > [!NOTE]
  > 비동기 중지 이벤트 지원 되지 않습니다. 만들어질 비동기 중지 이벤트를 전송 하려면 오류가 발생 합니다.

## <a name="discussion"></a>토론
 이벤트의 실제 구현에 독일의 디자인에 따라 달라 집니다. 전송 된 각 이벤트의 종류는 DE를 디자인할 때 설정 되는 해당 특성에 의해 결정 됩니다. 예를 들어, 하나의 DE 보낼 수 있습니다는 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 중지 이벤트로 보낼 수 있습니다 다른 동안 비동기 이벤트입니다.

 다음 표에서 프로그램 및 스레드 매개 변수는 이벤트 유형 뿐만 아니라는 이벤트에 대 한 필요를 지정 합니다. 모든 이벤트를 동기적 일 수 있습니다. 이벤트가 없습니다 동기 해야 합니다.

> [!NOTE]
> 합니다 [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) 인터페이스는 모든 이벤트에 대 한 필요 합니다.

|이벤트(event)|IDebugProgram2|IDebugThread2|이벤트를 중지합니다.|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|하지만 필수가 아닌 허용|하지만 필수가 아닌 허용|아니요|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|필수|필수|예|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|하지만 필수가 아닌 허용|하지만 필수가 아닌 허용|아니요|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|하지만 필수가 아닌 허용|하지만 필수가 아닌 허용|아니요|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|하지만 필수가 아닌 허용|하지만 필수가 아닌 허용|아니요|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|필수|필수|예|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|필수|필수|아니요|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|허용되지 않음|허용되지 않음|아니요|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|허용되지 않음|허용되지 않음|아니요|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|필수|필수|예|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|하지만 필수가 아닌 허용|하지만 필수가 아닌 허용|가능 여부|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|필수|필수|예|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|하지만 필수가 아닌 허용|하지만 필수가 아닌 허용|가능 여부|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|필수|필수|예|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|필수|필수|예|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|하지만 필수가 아닌 허용|하지만 필수가 아닌 허용|가능 여부|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|필수|하지만 필수가 아닌 허용|아니요|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|하지만 필수가 아닌 허용|하지만 필수가 아닌 허용|아니요|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|필수|하지만 필수가 아닌 허용|아니요|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|필수|하지만 필수가 아닌 허용|아니요|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|필수|하지만 필수가 아닌 허용|아니요|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|필수|하지만 필수가 아닌 허용|아니요|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|하지만 필수가 아닌 허용|하지만 필수가 아닌 허용|아니요|
|IDebugStopCompleteEvent2|필수|필수|예|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|필수|필수|예|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|하지만 필수가 아닌 허용|하지만 필수가 아닌 허용|아니요|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|필수|필수|아니요|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|필수|필수|아니요|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|하지만 필수가 아닌 허용|하지만 필수가 아닌 허용|아니요|

## <a name="see-also"></a>참고자료
- [이벤트 전송](../../extensibility/debugger/sending-events.md)