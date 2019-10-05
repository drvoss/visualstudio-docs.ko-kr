---
title: 시작 후 연결 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7a1ff749d340110707296c9d4958d13a3faa952
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350926"
---
# <a name="attach-after-a-launch"></a>시작 후 연결
프로그램 시작 디버그 세션 언급된 프로그램에 디버그 엔진 (DE)를 연결할 준비가 된 것입니다.

## <a name="design-decisions"></a>디자인 결정
 통신 공유 되는 주소 공간 내에서 쉽게 이기 때문에 두 가지 디자인 방법 간에 선택 해야 합니다: 디버그 세션을 DE 사이의 통신을 설정 합니다. 또는 DE와 프로그램 간의 통신을 설정 합니다. 다음 중에서 선택 합니다.

- 디버그 세션을 DE 사이의 통신을 설정 하는 것에 있도록 하는 경우 디버그 세션 공동는 DE 만들고 프로그램에 연결 하는 DE를 요청 합니다. 이 디자인 유지 디버그 세션 및 DE 함께 주소 공간 및 런타임 환경 및 프로그램의 다른 함께 합니다.

- 하는 경우는 DE와 프로그램 간의 통신을 설정 하는 것을 런타임 환경에서 공동는 DE를 만듭니다. 이 디자인에서 다른 주소 공간 및 DE, 런타임 환경 및 프로그램 SDM을 유지합니다. 이 디자인은 일반적인 스크립트 언어를 실행 하려면 인터프리터를 사용 하 여 구현 되는 DE입니다.

    > [!NOTE]
    > DE 프로그램에 연결 하는 방법을 하는 것은 구현에 따라 다릅니다. DE와 프로그램 간의 통신 구현에 따라 다릅니다 이기도합니다.

## <a name="implementation"></a>구현
 프로그래밍 방식으로 세션 디버그 관리자 SDM ()를 처음 받을 때 합니다 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 호출을 실행 하도록 프로그램을 나타내는 개체를 [연결](../../extensibility/debugger/reference/idebugprogram2-attach.md) 메서드를 전달는 [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) SDM 돌아가기 디버그 이벤트를 전달 하는 데 개체 이상입니다. 합니다 `IDebugProgram2::Attach` 메서드를 호출 합니다 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드. SDM 받는 방법에 대 한 자세한 내용은 합니다 `IDebugProgram2` 인터페이스를 참조 하십시오 [포트에 알림](../../extensibility/debugger/notifying-the-port.md)합니다.

 디버그 중인 프로그램 DE 프로그램과 동일한 주소 공간에서 실행 해야 하는 경우:는 DE 일반적으로 스크립트를 실행 하는 인터프리터의 일부 이므로 합니다 `IDebugProgramNodeAttach2::OnAttach` 메서드가 반환 되는 `S_FALSE`합니다. `S_FALSE` 반환 연결 프로세스가 완료 되었는지 나타냅니다.

 그러나 경우는 DE에서에서 실행 되는 SDM의 주소 공간: 합니다 `IDebugProgramNodeAttach2::OnAttach` 메서드가 반환 `S_OK`, 또는 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 인터페이스에 전혀 구현 되지 않습니다는 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 디버깅할 프로그램에 연결 된 개체입니다. 이 경우에 [연결](../../extensibility/debugger/reference/idebugengine2-attach.md) 결국 메서드는 연결 작업이 완료 합니다.

 후자의 경우에 호출 해야 합니다는 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 메서드를 `IDebugProgram2` 에 전달 된 개체를 `IDebugEngine2::Attach` 메서드, 저장소를 `GUID` 로컬 프로그램에서 개체 및이 반환 `GUID` 때를 `IDebugProgram2::GetProgramId` 이 개체에서 메서드 호출 이후에 됩니다. `GUID` 다양 한 디버그 구성에서 프로그램을 고유 하 게 식별 하는 데 사용 됩니다.

 경우는 `IDebugProgramNodeAttach2::OnAttach` 메서드 반환 `S_FALSE`, `GUID` 를 해당 메서드에 전달 되는 프로그램에 사용할 이므로 합니다 `IDebugProgramNodeAttach2::OnAttach` 설정 하는 메서드를 `GUID` 로컬 프로그램 개체에.

 프로그램 및 시작 이벤트를 보낼 준비가 이제는 DE 연결 됩니다.

## <a name="see-also"></a>참고자료
- [프로그램에 직접 연결](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [포트에 알림](../../extensibility/debugger/notifying-the-port.md)
- [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)