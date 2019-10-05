---
title: 연결 및 프로그램에 분리 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9edbabb078bc46c55431276e9c1fe8d1f807d76f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350906"
---
# <a name="attaching-and-detaching-to-a-program"></a>연결 및 프로그램에 분리
디버거를 연결 메서드 및 적절 한 특성을 사용 하 여 이벤트의 순서를 전송 해야 합니다.

## <a name="sequence-of-methods-and-events"></a>메서드 및 이벤트의 시퀀스

1. 세션 디버그 관리자 (SDM) 호출을 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드.

    디버그 엔진 (DE) 프로세스 모델을 기반으로 합니다 `IDebugProgramNodeAttach2::OnAttach` 메서드 이후에 결정 하는 다음 방법 중 하나를 반환 합니다.

    경우 `S_FALSE` 디버그 엔진에 연결 되는 프로그램에 반환 됩니다. 이 고, 그렇지 합니다 [연결](../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드를 호출 하 여 연결 프로세스를 완료 합니다.

    경우 `S_OK` SDM와 동일한 프로세스에 로드 되는 DE가 반환 됩니다. SDM 다음 작업을 수행합니다.

   1. 호출 [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) 는 DE의 엔진 정보를 가져옵니다.

   2. 배치는 DE를 만듭니다.

   3. 호출 [연결](../../extensibility/debugger/reference/idebugengine2-attach.md)합니다.

2. DE 보냅니다는 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 를 사용 하 여 SDM을 `EVENT_SYNC` 특성입니다.

3. DE 보냅니다는 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 를 사용 하 여 SDM을 `EVENT_SYNC` 특성입니다.

4. DE 보냅니다는 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 를 사용 하 여 SDM을 `EVENT_SYNC_STOP` 특성입니다.

   프로그램에서 분리는 2 단계 프로세스를 단순 다음과 같습니다.

5. SDM 호출 [분리](../../extensibility/debugger/reference/idebugprogram2-detach.md)합니다.

6. DE 보냅니다는 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)합니다.

## <a name="see-also"></a>참고자료
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)