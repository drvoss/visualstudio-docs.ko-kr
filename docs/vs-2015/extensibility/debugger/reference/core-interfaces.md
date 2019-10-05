---
title: 핵심 인터페이스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94703f13eba0c58aad24597bc65beeea862e79e5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179221"
---
# <a name="core-interfaces"></a>Core 인터페이스
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

다음 인터페이스는 디버거를 사용 하 여 확장에 대 한 핵심 인터페이스는 [!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)]합니다.  
  
## <a name="discussion"></a>토론  
 이러한 인터페이스는 디버그 엔진 (DE)을 만들려면 주로 사용 됩니다. 여기에 범주별으로 구성 됩니다.  
  
- [중단점](#Breakpoints)  
  
- [컨텍스트](#Contexts)  
  
- [핵심 서버](#CoreServer)  
  
- [디버그 엔진](#DebugEngines)  
  
- [문서](#Documents)  
  
- [이벤트](#Events)  
  
- [식](#Expressions)  
  
- [메모리](#Memory)  
  
- [모듈](#Modules)  
  
- [포트](#Ports)  
  
- [프로세스](#Processes)  
  
- [프로그램](#Programs)  
  
- [Properties](#Properties)  
  
- [스택 프레임](#StackFrames)  
  
- [스레드](#Threads)  
  
- [형식 시각화 도우미](#TypeVisualizers)  
  
  인터페이스를 구현할 수 있는 엔터티는:  
  
- 디버그 엔진 (DE)  
  
- 포트 공급자 (PS)  
  
- 식 계산기 (EE)  
  
- Visual Studio (VS)  
  
## <a name="Breakpoints"></a> 중단점  
 이러한 인터페이스와 관련 된 중단점의 추적을 구현 합니다.  
  
|인터페이스|에 의해 구현|설명|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|메모리 위치에 바인딩된 중단점을 나타냅니다.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|중단점 메모리 위치에 바인딩될 때는 DE 하 여 전송 합니다.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|중단점 요청에 대 한 문서 체크섬을 나타냅니다.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|DE 보낸 중단점 메모리 위치에 바인딩될 실패 한 경우.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|중단점에 도달한 경우는 DE 하 여 전송 합니다.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|중단점에 대 한 요청을 나타냅니다. 보류 중인 중단점을 만드는 데 사용 합니다.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|중단점에 대 한 요청을 나타냅니다. 보류 중인 중단점을 만드는 데 사용 합니다.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|중단점에 바인딩하는 데 사용 하는 정보를 나타냅니다.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|메모리 위치에서 중단점을 바인딩 해제할 때는 독일에서 전송 합니다.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|잘못 된 중단점을 나타냅니다 (반환한 `IDebugBreakpointErrorEvent2`).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|잘못 된 중단점에 대 한 해결 정보를 나타냅니다.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|함수에 중단점 설정 되어 있는 위치를 나타냅니다.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|바인딩될;에 있는 중단점을 나타냅니다. 바인딩된 중단점을 만드는 데 사용 합니다.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|한 바인딩된 중단점 집합에 대해 열거형을 나타냅니다.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|메모리 위치에 바인딩되지 못했습니다 중단점의 집합에 대해 열거형을 나타냅니다.|  
  
## <a name="Contexts"></a> 컨텍스트  
 이러한 인터페이스는 다양을 한 디버깅 중인 프로그램 내에서 컨텍스트를 나타냅니다.  
  
|인터페이스|에 의해 구현|Description|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|코드 명령의 시작 위치를 나타냅니다.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|확장 된 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 모듈 및 프로세스 인터페이스를 검색할 수 있도록 하는 인터페이스입니다.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|문서의 위치를 나타냅니다.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|식을 계산 하는 컨텍스트를 나타냅니다.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|메모리 바이트의 컬렉션의 시작 위치를 나타냅니다.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|중단점 또는 예외에서 스택 프레임 컨텍스트를 나타냅니다.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|중단점 또는 예외에서 스택 프레임 컨텍스트를 나타냅니다.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|코드 컨텍스트 집합을 통해 열거형을 나타냅니다.|  
  
## <a name="CoreServer"></a> 핵심 서버  
 이러한 인터페이스는 프로그램을 디버깅 중인 컴퓨터를 나타냅니다. 이러한 구현한 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 디버그 엔진을 호출할 수 있습니다.  
  
|인터페이스|에 의해 구현|Description|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|컴퓨터에 대 한 정보 뿐만 아니라 포트 및 포트 공급자에 대 한 액세스를 제공합니다.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|나타냅니다는 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) 는 원격 디버깅을 지원 합니다.|  
  
## <a name="DebugEngines"></a> 디버그 엔진  
 이러한 인터페이스는 디버그 엔진 및 관련 된 이벤트를 나타냅니다.  
  
|인터페이스|에 의해 구현|설명|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|사용자 지정 디버그 엔진을 나타냅니다.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|JustMyCode 기호와 예외의 로드를 지 원하는 사용자 지정 디버그 엔진을 나타냅니다.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|각 새 인스턴스의 DE 보낸 디버깅 작업을 처리할 준비가 된 것을 나타냅니다.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|시작 프로그램을 지 원하는 사용자 지정 디버그 엔진을 나타냅니다.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|여러 디버그 엔진을 처리 하는 프로그램 노드를 나타냅니다.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|SDM 스레드, 프로그램 또는 스택 프레임에서 디버그 엔진에 인터페이스를 얻을 수 있는 방법을 제공 합니다.|  
  
## <a name="Documents"></a> 문서  
 이러한 인터페이스는 문서 (소스 파일) 및 해당 관련된 요소를 나타냅니다.  
  
|인터페이스|에 의해 구현|Description|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|DE 보낸 문서를 열 수를 요청 합니다.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|문서에서 디스어셈블된 명령의 스트림을 나타냅니다.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|이름과 클래스 ID (CLSID)를 지정 하는 독일에서 제공 하는 문서를 나타냅니다.|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|디버그 문서에 대해 체크섬을 나타내며 체크섬 구성 요소 간에 전달 수 있습니다.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|문서 컨텍스트를 특정 문 및 코드 컨텍스트에 해당 하는 문서 내의 위치를 나타냅니다.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|문서 내의 일반적인 위치를 나타냅니다.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|문자 오프셋으로 소스 파일의 위치를 나타냅니다.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|DE 제공한 텍스트 문서를 나타냅니다 (에서 파생 된 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), 실제 텍스트를 제공 합니다.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|메모리에 있는 소스 파일에 변경 내용을 지정 하는 독일에서 전송 합니다.|  
  
## <a name="Events"></a> 이벤트  
 이러한 인터페이스는 DE 및 세션 디버그 관리자 (SDM) 간에 전송 되는 모든 이벤트를 나타냅니다.  
  
|인터페이스|에 의해 구현|Description|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|DE 보낸 문서를 열 수를 요청 합니다.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|기호 로드 하는 동안 메시지 표시줄 (SDM) 상태를 설정 하려면 세션 디버그 관리자에 게이 인터페이스를 전송 하는 디버그 엔진 (DE).|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|프로그램의 중단을 완료 되는 DE 보낸 합니다.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|중단점이 바인딩된 경우는 DE 보낸 합니다.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|중단점을 바인딩할 못하면는 DE 보낸 합니다.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|중단점에 도달한 경우는 DE 하 여 전송 합니다.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|중단점 바인딩 해제할 때는 DE 하 여 전송 합니다.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|특정 위치에서 중지 해야 하는지 여부를 결정 하는 독일에서 전송 합니다.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|메모리에 있는 소스 파일에 변경 내용을 지정 하는 독일에서 전송 합니다.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|각 새 인스턴스의 DE 보낸 디버깅 작업을 처리할 준비가 된 것을 나타냅니다.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|DE 보낸 디버깅 중인 프로그램을 첫 번째 명령을 실행할 준비가 되었다고 표시 합니다.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|사람이 읽을 수 있는 오류 메시지를 제공 하는 오류를 반환할 수 있습니다, 다른 이벤트 인터페이스에서 사용 되는 인터페이스입니다.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE, PS|다른 모든 이벤트 인터페이스 파생 되는 기본 인터페이스입니다.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|이벤트 (특정 이벤트 인터페이스를 구현 하는 개체로 나타남) 전송 되는 SDM을 구현한 인터페이스를 나타냅니다.|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|디버그 중인 프로그램에서 예외가 발생 하면는 DE 보낸 합니다.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|비동기 식 계산이 완료 되 면는 독일에서 전송 합니다.|  
|IDebugFindSymbolEvent2||사용되지 않습니다. 사용 하지 마세요.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|가로챈된 예외에 대 한 처리가 완료 되는 DE 보낸 합니다.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|DE 보낸 프로그램 로드가 완료 된 경우.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|사용자에 게 정보 메시지는 DE IDE을 표시 하 여 전송 합니다.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|모듈 로드 되거나 언로드될 때는 독일에서 전송 합니다.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|신호는 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 디버거 UI를 기호 수 없다는 시작한 실행 파일에 대 한 사용자에 게 알립니다.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|임의의 문자열 IDE 표시 하도록 독일에서 전송 합니다.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS, DE|모든 수신기 포트 이벤트를 통신 포트를 통해 보내집니다.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|프로세스를 만들 때 DE 또는 포트에서 전송 합니다.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|프로세스 제거 될 때 DE 또는 포트에 의해 전송 합니다.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|프로그램을 만든 경우 DE 또는 포트에서 전송 합니다.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|프로그램 제거 될 때 DE 또는 포트에서 전송 합니다.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|기본 동작을 재정의 하는 디버그 엔진을 사용 하도록 설정 된 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] UI 디버그 세션을 종료 하는 경우.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|프로그램의 이름을 변경 하는 경우 디버그 엔진 (DE)에서 (SDM) 세션 디버그 관리자에 게 전송 합니다.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|DE 때 새 속성을 보낸 (나타내는 `IDebugProperty2` 인터페이스) 만들었습니다.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|속성 메뉴가 제거 될 때는 DE 보낸 합니다.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|반환 값을 올바르게 표시할 수 있도록 부족 또는 함수를 단계별로 실행할 때는 DE 하 여 전송 합니다.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|디버그 엔진 메트릭 설정을 읽을 수 원격으로 합니다.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|DE 보낸, 조치 안팎으로 명령을 사용 하는 단계를 완료 하는 경우.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|DE 보낸 모듈의 기호를 로드 하는 성공 여부를 나타냅니다.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|스레드를 만들 때는 DE 하 여 전송 합니다.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|DE 보낸 때 스레드가 제거 되었습니다.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|스레드 이름 변경 된 경우는 DE 보낸 합니다.|  
  
## <a name="Expressions"></a> 식  
 이러한 인터페이스는 특정 컨텍스트에서 계산 되도록 식을 나타냅니다.  
  
|인터페이스|에 의해 구현|설명|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|계산할 식을 나타냅니다. 가져온 합니다 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스입니다.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|식을 계산 되는 컨텍스트를 나타냅니다. 가져온 합니다 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스입니다.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|비동기 식 계산이 완료 되 면는 독일에서 전송 합니다.|  
  
## <a name="Memory"></a> 메모리  
 이러한 인터페이스는 메모리의 바이트 시퀀스를 나타냅니다.  
  
|인터페이스|에 의해 구현|Description|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|읽거나 쓸 수 있는 메모리의 바이트 시퀀스를 나타냅니다.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|바이트 시퀀스의 메모리에서 위치를 나타냅니다.|  
  
## <a name="Modules"></a> 모듈  
 이러한 인터페이스는 실행 파일에 해당 하는 모듈을 나타내는 또는 합니다. DLL 파일입니다.  
  
|인터페이스|에 의해 구현|Description|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|단일 실행 파일 또는 DLL을 나타냅니다.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|나타냅니다는 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 는 기호를 지원 합니다.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|모듈 로드 되거나 언로드될 때는 독일에서 전송 합니다.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|PDB 파일에 포함 된 원본 서버 정보를 나타냅니다.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|알려진 된 모듈의 집합에 대해 열거형을 나타내면를 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)합니다.|  
  
## <a name="Ports"></a> 포트  
 이러한 인터페이스는 포트 및 포트 공급자를 나타냅니다.  
  
|인터페이스|에 의해 구현|Description|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS, PS|로컬 컴퓨터의 기본 포트를 나타냅니다.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|요청에 DCOM을 사용 하는 디버그 엔진을 사용 하도록 설정 된 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 방화벽이 원격 디버깅을 차단 하지는 않아야 하는 UI입니다.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS, PS|포트를 나타냅니다.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|모든 수신기 포트 이벤트를 통신 포트를 통해 보내집니다.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|시작 하 고 프로세스를 종료할 수 있는 포트를 나타냅니다.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|등록 된 포트를 사용 하 여 프로그램의 등록을 취소 하는 데 사용 현재 디버깅 중인 프로그램을 추적 하는 포트를 허용 합니다.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|포트를 선택 하기 위한 사용자 지정된 UI를 나타냅니다.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|새 포트를 만들거나 있는 포트에 대 한 요청을 나타냅니다.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|포트의 공급자를 나타냅니다.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|유지할 수 있는 포트의 공급자를 나타내는 만든 포트에 대 한 (디스크에 저장) 정보입니다.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|사용 하도록 설정 합니다 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] UI 내에서 텍스트를 표시 하는 **전송 정보** 의 섹션을 **프로세스에 연결** 대화 상자.|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|대상 컴퓨터에 대 한 정보를 쿼리할 수 있습니다.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS, PS|포트의 집합에 대해 열거형을 나타냅니다.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|포트 공급자 집합을 통해 열거형을 나타냅니다.|  
  
## <a name="Processes"></a> 프로세스  
 이러한 인터페이스는 프로세스를, 하나 이상의 응용 프로그램을 포함 하는 단일 실행 파일을 나타냅니다.  
  
|인터페이스|에 의해 구현|Description|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|컴퓨터에서 실행 되는 프로세스를 나타냅니다.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|적극적으로 지 원하는 프로세스를 나타내는 디버깅 (계속 해 서 단계를 대체 하는 데, 및에서 메서드를 실행 합니다 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|프로세스를 만들 때 DE 또는 포트에서 전송 합니다.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|프로세스 제거 될 때 DE 또는 포트에 의해 전송 합니다.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|세션에 연결 된 추적 해야 하는 프로세스를 나타냅니다.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|포트에서 프로세스 집합의 열거형을 나타냅니다.|  
  
## <a name="Programs"></a> 프로그램  
 이러한 인터페이스는 프로그램을 실행의 실제 실행 파일 또는 모듈에 해당 하지 않는 논리 단위를 나타냅니다.  
  
|인터페이스|에 의해 구현|Description|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|나타냅니다는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 동시에 디버깅 하 고 다른 프로그램과 함께에서 작동 해야 합니다.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|실행 논리 단위를 나타냅니다.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|프로그램을 만든 경우 DE 또는 포트에서 전송 합니다.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|프로그램 제거 될 때 DE 또는 포트에서 전송 합니다.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|나타냅니다는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 여러 디버그 엔진에서 처리할 수 있습니다.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|나타냅니다는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 는 세션에 연결 된 추적 수 있어야 합니다.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|나타냅니다는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 는 이전에 실행 중인 프로세스에 대 한 정보를 반환할 수 있습니다.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|디버깅할 수 있는 프로그램을 나타냅니다.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|프로그램 노드를를 연결 된 프로그램에 연결 하지 못했습니다. 알림을 받을 수 있습니다.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|SDM는 독일에 의해 제어 프로그램에 대 한 DE를 쿼리 하는 방법을 제공 합니다.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|디버깅 중 표시할 SDM을 사용 하 여 프로그램을 등록 하려면 DEs를 사용한입니다.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|나타냅니다는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 스레드 또는 프로세스 경계를 넘어 인터페이스를 마샬링할 수입니다.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|프로그램 집합의 열거형을 나타냅니다.|  
  
## <a name="Properties"></a> 속성  
 이러한 인터페이스는 속성을, 식 평가의 결과 일반적으로 특정 컨텍스트와 연결 된 값을 나타냅니다.  
  
|인터페이스|에 의해 구현|설명|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|나타냅니다는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 사용자 지정 방식으로 해당 값을 표시할 수 있는 합니다.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|스택 프레임, 문서 또는 식 평가의 결과 값을 나타냅니다.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|나타냅니다는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 지 원하는 임의의 긴 문자열입니다.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|DE 때 새 속성을 보낸 (나타내는 합니다 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스) 만들었습니다.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|속성 메뉴가 제거 될 때는 DE 보낸 합니다.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|특정 스택 프레임 외부에 존재할 수 있는 속성에 대 한 참조를 나타냅니다.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|세트에 대 한 열거형을 나타내면 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 변수, 레지스터, 매개 변수 및 식을 설명 하는 구조입니다.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|세트에 대 한 열거형을 나타내면 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조입니다.|  
  
## <a name="StackFrames"></a> 스택 프레임  
 이러한 인터페이스는 스택 프레임을 컨텍스트를 나타내는에 중단점 또는 예외가 발생 했습니다.  
  
|인터페이스|에 의해 구현|Description|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|컨텍스트를 나타냅니다에 중단점 또는 예외가 발생 했습니다.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|나타냅니다는 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 예외를 가로채는 처리할 수 있습니다.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|집합에 대해 열거형을 나타내면 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) 구조 함수를 지정 하는 특정 스택 프레임에 도착 하는 데 사용 되는 시퀀스를 호출 합니다.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|세트에 대 한 열거형을 나타내면 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 스택 프레임을 설명 하는 구조입니다.|  
  
## <a name="Threads"></a> 스레드  
 이러한 인터페이스는 스레드와 관련 된 이벤트를 나타냅니다.  
  
|인터페이스|에 의해 구현|Description|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|실행 스레드를를 나타냅니다.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|스레드를 만들 때는 DE 하 여 전송 합니다.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|DE 보낸 때 스레드가 제거 되었습니다.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|스레드 이름 변경 된 경우는 DE 보낸 합니다.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|스레드의 집합에 대해 열거형을 나타냅니다.|  
  
## <a name="TypeVisualizers"></a> 형식 시각화 도우미  
 이러한 인터페이스는 형식 시각화 도우미에 대 한 지원을 제공합니다. 이러한 인터페이스는 식 계산기에서 일반적으로 구현 됩니다.  
  
|인터페이스|에 의해 구현|Description|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|형식 시각화 도우미에 표시 되는 바이트 배열을 나타냅니다.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|형식 시각화 도우미에 전달할 데이터에 대 한 액세스를 가져오기 위한 메서드를 제공 합니다.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|에 대 한 액세스를 제공 하는 속성을 나타내면 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 구현 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [API 참조](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [사용자 지정 디버그 엔진 만들기](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
