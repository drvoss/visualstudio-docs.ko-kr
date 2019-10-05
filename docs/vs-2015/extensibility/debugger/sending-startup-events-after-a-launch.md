---
title: 시작 후 시작 이벤트 보내기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caf36e6713e49bb1470cd720ba2d04f689abba43
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436673"
---
# <a name="sending-startup-events-after-a-launch"></a>시작 후 시작 이벤트 보내기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버그 엔진 (DE) 프로그램에 연결 된 후 디버그 세션에 다시 일련의 시작 이벤트를 보냅니다.  
  
 디버그 세션에 다시 전송 하는 시작 이벤트는 다음과 같습니다.  
  
- 엔진 생성 이벤트입니다.  
  
- 프로그램 생성 이벤트입니다.  
  
- 스레드 생성 및 모듈 로드 이벤트입니다.  
  
- 로드 완료 이벤트를 전송한 코드가 로드 및 실행할 준비가 되 면 모든 코드가 실행 되기 전에  
  
  > [!NOTE]
  > 이 이벤트가 계속 되 면 전역 변수 초기화 되 고 시작 루틴 실행 됩니다.  
  
- 가능한 다른 스레드 생성 및 모듈 로드 이벤트입니다.  
  
- 항목 지점 이벤트는 프로그램에 도달 했습니다 해당 주 진입점와 같은 신호를 보냅니다 **Main** 또는 `WinMain`합니다. 이 이벤트는 DE 이미 실행 중인 프로그램에 연결 하는 경우 일반적으로 전송 되지 않습니다.  
  
  프로그래밍 방식으로 DE 전송 세션 디버그 관리자 SDM ()는 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 뒤에 엔진이 생성 이벤트를 나타내는 인터페이스를 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 프로그램 생성 이벤트를 나타내는입니다.  
  
  일반적으로 뒤에 하나 이상의 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 스레드 생성 이벤트 및 [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) 모듈 로드 이벤트입니다.  
  
  코드 로드 및 실행할 준비가 되었지만 경우는 DE SDM을 보내는 코드를 실행 하기 전에 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 부하 완료 이벤트입니다. 마지막으로 프로그램을 이미 실행 하지 않는 경우는 DE 보냅니다는 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 항목 시점 이벤트, 신호 프로그램에서 해당 주 진입점에 도달 하 고 디버깅 하는 것에 대 한 준비가 되었습니다.  
  
## <a name="see-also"></a>참고 항목  
 [실행 제어](../../extensibility/debugger/control-of-execution.md)   
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)
