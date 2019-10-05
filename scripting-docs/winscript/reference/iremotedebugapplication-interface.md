---
title: IRemoteDebugApplication 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a231818def210f7c88ab031059f8561c67b33d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944232"
---
# <a name="iremotedebugapplication-interface"></a>IRemoteDebugApplication 인터페이스
실행 중인 애플리케이션을 나타냅니다. 운영 체제 프로세스에 해당 하는 필요 하지 않습니다. 일반적으로 디버거는 디버깅에 대 한 응용 프로그램 대상 으로합니다. 프로세스 디버그 관리자는 일반적으로 응용 프로그램 개체를 구현합니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IRemoteDebugApplication` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|중단점에서 현재 사용 중인 응용 프로그램을 계속 합니다.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|응용 프로그램이 가능한 한 빨리 디버거를 중단 하면 됩니다.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|이 응용 프로그램에 디버거를 연결합니다.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|응용 프로그램에서 현재 디버거를 연결을 끊습니다.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|현재는 디버거가 응용 프로그램에 연결을 반환.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|디버거 IDE, 실행-out-of-process 응용 프로그램 프로세스에서 개체를 만들려는 응용 프로그램에 대 한 메커니즘을 제공 합니다.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|응용 프로그램 응답 인지 여부를 나타냅니다.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|응용 프로그램을 사용 하 여 연결 된 것으로 알려진 모든 스레드를 열거 합니다.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|이 응용 프로그램 노드의 이름을 반환합니다.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|응용 프로그램을 사용 하 여 연결 하는 모든 노드가 추가 되는 응용 프로그램 노드를 반환 합니다.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|이 응용 프로그램에서 실행 되는 모든 언어에 대 한 전역 식 컨텍스트를 열거 합니다.|