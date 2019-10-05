---
title: 프로세스 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c45fc70fe61c7221a8042d275dd44d69eb5d11e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351491"
---
# <a name="processes"></a>프로세스
디버거 아키텍처에는 *프로세스*:

- 프로그램의 집합에 대 한 컨테이너입니다. 이 Windows 프로세스 스레드의 집합에 대 한 컨테이너인 밀접 하 게 유사 합니다.

- 이름, 식별자 또는 실제 식별자로 자신을 식별할 수 있습니다.

- 실행 중인 모든 프로그램 (및 해당 스레드)를 열거할 수 있습니다.

- 자체,에서는 실행 중인 포트 및 포함 하는 컴퓨터를 설명할 수 있습니다.

- 하나를 만들 수 있습니다 하거나 자세한 프로그램 종료, 프로그램 또는 프로그램의 중지 합니다.

- 로 표시 됩니다는 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) 인터페이스 프로세스를 시작할 때 만들어집니다. 두 세션 디버그 관리자에서 (SDM) 프로세스를 시작할 또는 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)합니다.

  디버그 패키지를 호출 하 여 프로세스에는 디버그 엔진 (DE)에 연결할 수 [연결](../../extensibility/debugger/reference/idebugprocess2-attach.md)에 모든 가능한 프로그램을 처리할 수 있는 프로세스에서 실행 되는 DE 연결 되었음을 의미 합니다. 예를 들어, 공용 언어 런타임 DE 프로세스에 연결을 하는 경우 관리 코드를 실행 중인 프로그램에만 연결 합니다.

## <a name="see-also"></a>참고자료
- [프로그램](../../extensibility/debugger/programs.md)
- [스레드](../../extensibility/debugger/threads.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [패키지를 디버그 합니다.](../../extensibility/debugger/debug-package.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)