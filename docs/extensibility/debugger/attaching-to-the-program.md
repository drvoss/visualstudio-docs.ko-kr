---
title: 프로그램에 연결 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1cc66dbade730409406a7dc3f3208c4d5147fa6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332628"
---
# <a name="attach-to-the-program"></a>프로그램에 연결
적절 한 포트를 사용 하 여 프로그램을 등록 한 후에 디버그 하려는 프로그램에는 디버거를 연결 해야 합니다.

## <a name="choose-how-to-attach"></a>연결 하는 방법 선택
 세션 디버그 관리자 SDM ()를 디버깅 중인 프로그램에 연결 하려고 하는 세 가지가 있습니다.

1. 통해 디버그 엔진에서 실행 되는 프로그램에 대 한 합니다 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 메서드 (예를 들어 해석 된 언어의 일반), SDM 가져옵니다 합니다 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 에서 인터페이스 합니다 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 에 붙는 프로그램에 연결 된 개체입니다. SDM 얻을 수 있는 경우는 `IDebugProgramNodeAttach2` SDM 인터페이스를 호출 합니다 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드. 합니다 `IDebugProgramNodeAttach2::OnAttach` 메서드가 반환 되는 `S_OK` 를 프로그램에 연결 하지 않은 나타내고 다른 시도 프로그램에 연결할 수 있습니다.

2. SDM 얻을 수 있는 경우는 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) SDM 호출에 연결 되 고 프로그램의 인터페이스는 [연결](../../extensibility/debugger/reference/idebugprogramex2-attach.md) 메서드. 이 방식은 일반적인 포트 공급자가 원격으로 실행 하는 프로그램에 대 한 합니다.

3. 프로그램을 통해 연결할 수 없습니다 하는 경우는 `IDebugProgramNodeAttach2::OnAttach` 또는 `IDebugProgramEx2::Attach` 메서드 SDM는 호출 하 여 (아직 로드) 하는 경우 디버그 엔진을 로드 합니다 `CoCreateInstance` 함수 및 호출을 [연결](../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드. 이 방법은 로컬 포트 공급자가 시작한 프로그램에 대 한 일반적인 것입니다.

    호출 하는 사용자 지정 포트 공급자에 대 한도 가능 합니다 `IDebugEngine2::Attach` 의 사용자 지정 포트 공급자 구현에서 메서드를 `IDebugProgramEx2::Attach` 메서드. 일반적으로 경우 사용자 지정 포트 공급자 시작 원격 컴퓨터에서 디버그 엔진입니다.

   세션 디버그 관리자 (SDM) 호출 하는 경우 첨부 파일 이루어집니다 합니다 [연결](../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드.

   프로그램 DE 디버그 해야 하는 응용 프로그램과 동일한 프로세스에서 실행할 경우의 다음 메서드를 구현 해야 합니다 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  후 합니다 `IDebugEngine2::Attach` 메서드가 호출 되 면 구현에서 다음이 단계를 수행 합니다 `IDebugEngine2::Attach` 메서드:

1. 보내기는 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) SDM 이벤트 개체입니다. 자세한 내용은 [이벤트를 보내는](../../extensibility/debugger/sending-events.md)합니다.

2. 호출을 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 메서드는 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 에 전달 된 개체는 `IDebugEngine2::Attach` 메서드.

     반환 된 `GUID` 프로그램을 식별 하는 데 사용 되는 합니다. `GUID` 를 나타내는 로컬 프로그램 DE, 해당 반환 해야 하는 경우 개체에 저장 되어야 합니다는 `IDebugProgram2::GetProgramId` 메서드를 호출 합니다 `IDebugProgram2` 인터페이스입니다.

    > [!NOTE]
    > 구현 하는 경우는 `IDebugProgramNodeAttach2` 프로그램의 인터페이스 `GUID` 에 전달 되는 `IDebugProgramNodeAttach2::OnAttach` 메서드. 이렇게 `GUID` 프로그램에 사용 됩니다 `GUID` 반환한는 `IDebugProgram2::GetProgramId` 메서드.

3. 보내기는 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) SDM을 알리는 이벤트 개체는 로컬 `IDebugProgram2` 는 DE에 프로그램을 나타내는 개체를 만든 합니다. 자세한 내용은 참조 하세요 [이벤트를 보내는](../../extensibility/debugger/sending-events.md)합니다.

    > [!NOTE]
    > 이 다릅니다 `IDebugProgram2` 에 전달 된 개체는 `IDebugEngine2::Attach` 메서드. 이전에 전달 된 `IDebugProgram2` 개체 에서만 포트에서 인식 되 고 별도 개체입니다.

## <a name="see-also"></a>참고자료
- [실행 기반 첨부 파일](../../extensibility/debugger/launch-based-attachment.md)
- [이벤트 전송](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
