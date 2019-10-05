---
title: 필요한 이벤트 보내기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44ef1bb6c436faaefb309ab62db02ee43a0486ab
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345587"
---
# <a name="send-the-required-events"></a>필요한 이벤트 보내기
필요한 이벤트를 보내는 데이 절차를 따르십시오.

## <a name="process-for-sending-required-events"></a>필요한 이벤트를 전송 하기 위한 프로세스
 다음 이벤트는 필요한 (DE) 엔진 디버그를 만들 때이 순서 및 프로그램에 연결 합니다.

1. 보내기는 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) SDM ()는 DE 프로세스에서 하나 이상의 프로그램 디버깅을 위해 초기화 될 때 세션 디버그 관리자에 게 이벤트 개체입니다.

2. 디버그할 프로그램에 연결 되 면 송신을 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) SDM 이벤트 개체입니다. 이 이벤트는 엔진 디자인에 따라 중지 이벤트를 수 있습니다.

3. 프로세스를 시작할 때 프로그램에 연결 되 면 송신을 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 새 스레드의 IDE에 알리기 위해 SDM 이벤트 개체입니다. 이 이벤트는 엔진 디자인에 따라 중지 이벤트를 수 있습니다.

4. 보내기는 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) SDM 때 디버깅 중인 프로그램이 완료 된 로드 또는 프로그램에 연결 합니다. 완료 되 면 이벤트 개체입니다. 이 이벤트는 stopping 이벤트 여야 합니다.

5. 보내는 응용 프로그램 디버깅을 시작 된 경우는 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) SDM 런타임 아키텍처에서 코드의 첫 번째 명령 실행 될 때 이벤트 개체입니다. 이 이벤트는 항상 중지 이벤트가입니다. 디버깅 세션을 한 단계씩 실행을 IDE이이 이벤트에서 중지 됩니다.

> [!NOTE]
> 다양 한 언어 코드의 시작 부분 (CRT 라이브러리 (_m))에서 미리 컴파일된 외부 함수 또는 전역 이니셜라이저를 사용합니다. 디버깅 중인 프로그램의 언어 요소는 초기 진입점 보다 먼저 이러한 형식 중 하나를 포함,이 코드가 실행 되 고 항목 지점 이벤트가 전송 된 경우 사용자 진입점와 같은 **주** 또는 `WinMain`에 에 도달 했습니다.

## <a name="see-also"></a>참고자료
- [디버그할 프로그램을 사용 하도록 설정](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)