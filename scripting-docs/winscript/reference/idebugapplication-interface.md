---
title: IDebugApplication 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8229f234f8a8ce607f36c48e070cb3d40a211d45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990830"
---
# <a name="idebugapplication-interface"></a>IDebugApplication 인터페이스
언어 엔진과 호스트에서 사용할 비 원격 디버깅 메서드를 노출합니다.  
  
 상속 된 메서드 외에도 `IRemoteDebugApplication`, `IDebugApplication` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|응용 프로그램의 이름을 설정합니다.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|단일 단계 모드에서 언어 엔진을 호출자에 게 반환를 프로세스 디버그 관리자에 게 알립니다.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|디버거 IDE 통해 표시할 지정된 된 문자열을 발생 합니다.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|기본 디버거 IDE를 시작 하 고 아직 연결 되지 않은 경우이 응용 프로그램에 디버그 세션을 연결 합니다.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|현재 스레드를 차단 하 고 디버거 IDE 중단점에 대 한 알림을 보냅니다.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|이 응용 프로그램을 모든 참조를 해제 하 고 비활성 상태가 발생 합니다.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|응용 프로그램에 대 한 현재 중단 플래그를 반환합니다.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|현재 실행 중인 스레드와 연결 되는 스레드를 반환 합니다.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|지정 된 동기식 디버그 작업에 대 한 비동기 액세스를 제공합니다.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|이 응용 프로그램에는 스택 프레임 열거자 공급자를 추가합니다.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|이 응용 프로그램에서 스택 프레임 열거자 공급자를 제거합니다.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|현재 실행 중인 스레드의 디버거 스레드를 결정 합니다.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|호출자에 게 디버거 스레드에서 코드를 실행 하는 메커니즘을 제공 합니다.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|특정 문서 공급자와 연결 된 새 응용 프로그램 노드를 만듭니다.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|디버거의 일반 이벤트가 발생 `IApplicationDebugger` 인터페이스입니다.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|현재 스레드를 차단 하 고 디버거 IDE 오류에 대 한 알림을 보냅니다.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|(JIT)-just-in-time 디버거에 등록 되어 있는지 확인 합니다.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|JIT 디버거 자동 디버그 호스트에 등록 되어 있는지 확인 합니다.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|이 응용 프로그램 전역 식 컨텍스트 공급자를 추가합니다.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|이 응용 프로그램에서 전역 식 컨텍스트 공급자를 제거합니다.|