---
title: IDebugEngine2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c011a530bbd4323546257a40334a4b8a0f57bdb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195906"
---
# <a name="idebugengine2"></a>IDebugEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 인터페이스는 디버그 엔진을 (DE)를 나타냅니다. 중단점을 설정 하 여 예외를 지우면 만들기에서 다양 한 디버깅 세션을 관리 하는 것이 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 이 인터페이스는 사용자 지정 DE 프로그램의 디버깅을 관리 하 여 구현 됩니다. 이 인터페이스는 DE에서 구현 되어야 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 세션 디버그 관리자 (SDM), 예외 관리, 중단점을 만들고, 동기 이벤트는 DE 보낸 응답을 포함 하 여 디버깅 세션을 관리 하려면이 인터페이스를 호출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugEngine2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|DE로 디버깅 중인 모든 프로그램에 대 한 열거자를 만듭니다.|  
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|프로그램에는 장치를 연결합니다.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|DE에서 보류 중인 중단점을 만듭니다.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|DE 지정 된 예외를 처리 하는 방법을 지정 합니다.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|지정된 된 예외를 제거 하 여 디버그 엔진에서 더 이상 처리 합니다.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|IDE는 특정 런타임 아키텍처 또는 언어에 대해 설정한 예외 목록을 제거 합니다.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|DE의 GUID를 가져옵니다.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|지정 된 프로그램 예외적인 종료 되었습니다 하 고는 DE 프로그램에 대 한 모든 참조를 정리 하 고 프로그램을 전송 해야 할 DE 삭제 이벤트를 알립니다.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|이전에 보낸는 DE SDM을 동기식 디버그 이벤트를 수신 되어 처리를 나타내기 위해 SDM에서 호출 됩니다.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|DE의 로캘을 설정 합니다.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|현재는 DE 사용에서 레지스트리 루트를 설정합니다.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|메트릭을 설정합니다.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|이 DE로 디버깅 중인 모든 프로그램 실행 하려고 하는 해당 스레드 중 하나 다음에 실행을 중지를 요청 합니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: Msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
