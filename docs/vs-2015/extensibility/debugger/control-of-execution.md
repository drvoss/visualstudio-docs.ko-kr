---
title: 실행 제어 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3ce9f3fc810a1f2fd37166d4272b7c57c07927c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203275"
---
# <a name="control-of-execution"></a>실행 제어
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버그 엔진 (DE) 일반적으로 다음 이벤트 중 하나가으로 보냅니다 마지막 startup 이벤트:  
  
- 새로 시작된 된 프로그램에 연결 하는 경우 항목 지점 이벤트  
  
- 로드 완료 이벤트를 이미 실행 중인 프로그램에 연결 하는 경우  
  
  이러한 두 이벤트는 중지 의미는 DE IDE를 사용 하 여 사용자의 응답을 대기 하는 이벤트가 있습니다. 자세한 내용은 [운영 모드](../../extensibility/debugger/operational-modes.md)합니다.  
  
## <a name="stopping-event"></a>이벤트 중지  
 디버그 세션을 중지 이벤트를 보내는 경우:  
  
1. 프로그램 및 현재 명령 포인터를 포함 하는 스레드는 이벤트 인터페이스에서 가져올 수 있습니다.  
  
2. IDE는 현재 원본 코드 파일 및 위치를 표시 하는 편집기에서 강조 표시를 확인 합니다.  
  
3. 디버그 세션 일반적으로이 첫 번째 중지 이벤트를 호출 하 여 응답 프로그램 **계속** 메서드.  
  
4. 프로그램이 중지 조건을 사례는 DE 디버그 세션에 중단점 이벤트를 보냅니다는 중단점에 도달 하는 등을 발견할 때까지 실행 합니다. 중단점 이벤트는 stopping 이벤트 이며는 DE 다시 사용자 응답을 대기 합니다.  
  
5. 사용자가 한 단계씩 코드 실행, 또는 IDE 함수에서 프로그램을 호출 하려면 디버그 세션을 요청 하는 경우 `Step` (명령, 문 또는 줄) 단계 및 단계의 종류의 단위를 전달 하는 메서드를-즉, 한 단계씩 코드 실행을 넘는 것인지 또는 함수입니다. 단계를 완료 하는 경우는 DE stopping 이벤트는 디버그 세션에 단계 완료 이벤트를 보냅니다.  
  
    또는  
  
    현재 명령 포인터에서 실행을 계속 하 여 사용자가, IDE 프로그램을 호출 하려면 디버그 세션 묻습니다 **Execute** 메서드. 다음 중지 조건을 발견할 때까지 프로그램 실행을 다시 시작 합니다.  
  
    또는  
  
    디버그 세션 호출 프로그램의 특정 중지 이벤트를 무시 하려면 디버그 세션 인 경우 **계속** 메서드. 중지 조건이 발생 했을 때 into, 또는 함수에서 프로그램 된 단계별 실행, 단계를 계속 합니다.  
  
   프로그래밍 방식으로 DE 중지 조건에서 발견 하는 경우 보내는 등의 중지 이벤트 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 하거나 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 이용 하 여 세션 디버그 관리자 SDM) [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 인터페이스입니다. DE 전달 된 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 하 고 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 프로그램 및 현재 명령 포인터를 포함 하는 스레드가 나타내는 인터페이스입니다. SDM 호출 [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 최상위 스택 프레임 및 호출을 가져오는 [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 현재 명령와 관련 된 문서 컨텍스트를 가져오려면 포인터입니다. 이 문서의 컨텍스트에서 일반적으로 소스 코드 파일 이름, 줄 및 열 번호입니다. IDE는 현재 명령 포인터를 포함 하는 소스 코드를 강조 표시할 이러한를 사용 합니다.  
  
   SDM 일반적으로이 첫 번째 중지 이벤트를 호출 하 여 응답 [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)합니다. 프로그램이 실행 한 다음 사례는 DE 보냅니다 중단점에 도달 하는 등 중지 조건을 발견할 때까지 되는 [IDebugBreakpointEvent2 인터페이스](../../extensibility/debugger/reference/idebugbreakpointevent2.md) SDM을 합니다. 중단점 이벤트는 stopping 이벤트 이며는 DE 다시 사용자 응답을 대기 합니다.  
  
   사용자가 한 단계씩 코드 실행, 또는 함수에서 IDE SDM을 호출 하 라는 메시지가 표시 됩니다. 경우 [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md), 전달 된 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (명령, 문 또는 줄) 및 [ STEPKIND](../../extensibility/debugger/reference/stepkind.md), 즉 into, 또는 함수의 한 단계씩 실행 하려면 여부. DE 보내는 단계를 완료 하는 경우는 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) SDM 된 중지 이벤트에 대 한 인터페이스입니다.  
  
   현재 명령 포인터에서 실행을 계속 하 여 사용자가, IDE SDM 호출을 묻습니다 [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)합니다. 다음 중지 조건을 발견할 때까지 프로그램 실행을 다시 시작 합니다.  
  
   디버그 패키지를 호출 하는 SDM 호출 디버그 패키지를 특정 중지 이벤트를 무시 하려면 [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)합니다. 중지 조건이 발생 했을 때 into, 또는 함수에서 프로그램 된 단계별 실행, 단계를 계속 합니다. 계속 하는 방법을 알 수 있도록 프로그램 단계별 실행 상태를 유지 함을 의미 합니다.  
  
   SDM에 게 호출 `Step`, **Execute**, 및 **계속** 은 비동기, SDM 신속 하 게 반환할 호출이 필요 함을 의미 합니다. 경우는 DE 이벤트를 보냅니다 SDM을 중지 하기 전에 동일한 스레드에서 `Step`, **Execute**, 또는 **계속** SDM 중단을 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)
