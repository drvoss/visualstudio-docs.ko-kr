---
title: 컨트롤 프로그램 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8102bc488d5c74f751fb93584016aa6904fbe2d9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438079"
---
# <a name="program-control"></a>프로그램 제어
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio에서 다음 단계별 실행의 모든 디버깅 및 루틴을 계속 프로그램 수준에서 발생 합니다.  
  
- 특정 프레임 환경에서 실행 될 다음 명령으로 컴퓨터를 설정, 다음 문 설정  
  
- 즉, 단계별 실행 모드를 종료 하려면 계속 실행  
  
- 다음 명령으로 단계별 실행  
  
- 현재 단계별 실행 모드를 사용 하 여 계속합니다.  
  
- 프로그램에 포함 된 스레드를 일시 중단  
  
- 프로그램에 포함 된 스레드 재개  
  
> [!NOTE]
> 호출 스택 보기는 스레드 수준에서 구현 됩니다. 스레드에 대 한 호출 스택을 볼 때 프레임 정보 열거의 모든 메서드를 구현 해야 합니다 [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 인터페이스입니다.  
  
## <a name="methods-of-program-control"></a>프로그램 제어 메서드  
 다음 표에서의 메서드를 보여 줍니다 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 최소로 작동 디버그 엔진 (DE) 및 실행 제어를 위해 구현 되어야 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|중지 된 상태에서 프로그램에 포함 된 모든 스레드의 실행을 계속 합니다. 실행 제어에 필요합니다.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|중지 된 상태에서 프로그램에 포함 된 모든 스레드의 실행을 계속 합니다. 실행 제어에 필요합니다.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|지정 된 스레드에서 단계를 수행합니다. 실행 중인 프로그램에 포함 된 다른 모든 스레드를 계속 합니다. 실행 제어에 필요합니다.|  
  
 다중 스레드 프로그램의 경우 구현 해야 합니다 [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 메서드와의 모든 메서드는 [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)
