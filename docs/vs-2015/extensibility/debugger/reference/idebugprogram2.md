---
title: IDebugProgram2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 372c119b6a841d7d4b349e85548914f7641b53d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148642"
---
# <a name="idebugprogram2"></a>IDebugProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 프로세스에서 실행 중인 프로그램을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진 (DE) 및 사용자 지정 포트 공급자 프로세스에는 프로그램을 나타내며이 인터페이스를 구현 합니다. 세션 디버그 관리자 (SDM) 정보를 제공 하려면이 인터페이스 구현 [연결](../../../extensibility/debugger/reference/idebugprogram2-attach.md)합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 합니다 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트에 대 한 새 프로그램을이 인터페이스를 반환 합니다. 이 인터페이스에 대 한 많은 메서드 여러 인터페이스를 매개 변수로 사용 됩니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugProgram2`합니다.  
  
|메서드|Description|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|이 프로그램에서 실행 되는 스레드를 열거 합니다.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|프로그램의 이름을 가져옵니다.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|이 프로그램에서 실행 중인 프로세스를 가져옵니다.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|이 프로그램을 종료합니다.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|이 프로그램에 연결 합니다.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|디버그 엔진 (DE) 프로그램에서 분리 하는 경우를 결정 합니다.|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|이 프로그램에서 디버거를 분리합니다.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|이 프로그램에 대 한 전역적으로 고유 식별자를 가져옵니다.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|가져옵니다 속성을 프로그래밍합니다.|  
|[실행](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|중지 된 상태에서이 프로그램 실행을 계속 합니다. 모든 이전 실행 상태가 지워집니다.|  
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|중지 된 상태에서이 프로그램 실행을 계속 합니다. 모든 이전 실행 상태로 유지 됩니다.|  
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|단계를 수행합니다.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|이 프로그램은 다음 실행을 중지 하는 요청 시간 코드의 스레드 실행 중입니다.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|이름 및이 프로그램을 실행 하는 디버그 엔진 (DE)의 식별자를 가져옵니다.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|소스 파일에서 지정된 된 위치에 대 한 코드 컨텍스트 열거합니다.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|이 프로그램에 대 한 메모리 바이트 수를 가져옵니다.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|이 프로그램 또는이 프로그램의 일부에 대 한 디스어셈블리 스트림을 가져옵니다.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|이 프로그램에 로드 되 고 실행 되는 모듈을 열거 합니다.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|이 프로그램에 대 한 편집 및 계속 (ENC) 업데이트를 가져옵니다.<br /><br /> 사용자 지정 디버그 엔진을이 메서드를 구현 하지 않습니다 (항상 반환할 `E_NOTIMPL`).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|이 프로그램에 대 한 코드 경로 열거합니다.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|덤프 파일에 씁니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>설명  
 프로그램은 하나 이상의 응용 프로그램의 프로세스 이루어집니다 하는 동안 특정 런타임 아키텍처에서 실행 되는 스레드 컨테이너입니다.  
  
## <a name="see-also"></a>관련 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [다음](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
