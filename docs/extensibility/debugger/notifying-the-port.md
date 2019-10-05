---
title: 포트에 알림 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e7ccb4ab9fc36e08f4094baaf1e6b6eee30b2f8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351511"
---
# <a name="notify-the-port"></a>포트에 게 알림
프로그램을 시작한 후 포트 알려야, 다음과 같습니다.

1. 포트를 새 프로그램 노드를 수신 하면 디버그 세션에 다시 프로그램 생성 이벤트를 보냅니다. 이벤트에는 저마다 프로그램을 나타내는 인터페이스입니다.

2. 디버그 세션에 연결할 수 있는 디버그 엔진 (DE)의 식별자에 대 한 프로그램을 쿼리 합니다.

3. 디버그 세션은 해당 프로그램에 대 한 허용 되는 DEs 목록에는 DE 인지를 확인 합니다. 디버그 세션 디버그 패키지로 전달 된 원래 솔루션의 활성 프로그램 설정에서이 목록을 가져옵니다.

    허용 되는 목록에는 DE 이어야 합니다. 그렇지 않으면는 DE 프로그램에 연결 되지 않습니다.

   프로그래밍 방식으로 포트를 프로그램에 새 노드를 먼저 받으면 만듭니다는 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 프로그램을 나타내는 인터페이스입니다.

> [!NOTE]
> 이 혼동 하지는 `IDebugProgram2` 디버그 엔진 (DE)에 의해 나중에 생성 된 인터페이스입니다.

 전송 포트를 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) COM 사용 하 여 세션 디버그 관리자 SDM ()를 다시 생성 이벤트를 프로그램 `IConnectionPoint` 인터페이스.

> [!NOTE]
> 이 혼동 하지는 `IDebugProgramCreateEvent2` 는 DE에서 나중에 전송 되는 인터페이스입니다.

 포트 이벤트 인터페이스 자체와 함께 보냅니다 합니다 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), 및 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 포트를 나타내는 인터페이스를 처리 하 고 프로그램을 각각. SDM 호출 [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) 프로그램을 디버그할 수 있는 DE의 GUID를 가져오려고 합니다. 처음 가져온 GUID를 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스입니다.

 SDM은 DEs 허용 목록에는 DE 인지를 확인 합니다. SDM은 패키지 디버그로 전달 된 원래 솔루션의 활성 프로그램 설정에서이 목록을 가져옵니다. 허용 되는 목록에는 DE 이어야 합니다. 그렇지 않으면 프로그램에 연결 되지 않습니다.

 DE의 id가 확인 되 면 SDM를 프로그램에 연결할 수 있습니다.

## <a name="see-also"></a>참고자료
- [프로그램 시작](../../extensibility/debugger/launching-a-program.md)
- [시작 후 연결](../../extensibility/debugger/attaching-after-a-launch.md)
- [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)