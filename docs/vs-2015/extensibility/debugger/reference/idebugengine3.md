---
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e43da0b05062c6c7b1c4d3cfe771ff0b93f83a9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195786"
---
# <a name="idebugengine3"></a>IDebugEngine3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

하나 이상의 모듈의 디버깅을 제어 하는 단일 디버그 엔진을 (DE)를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 이 인터페이스는 구현한 사용자 지정 DE (기호를 지 원하는) 경우 JustMyCode 상태를 사용 하도록 설정 합니다. 기호 및 JustMyCode 지 원하는 경우이 인터페이스는 DE에서 구현 되어야 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 이 인터페이스는 세션 디버그 관리자 (SDM) 기호를 로드 하는 위치에 대 한 사용자 옵션에 전달 하 여 호출 됩니다. 인스턴스화된 엔진의 GUID를 설정 하 라고 (이 GUID는 메트릭을 기준으로 엔진 등록 중에서). 또한 SDM JustMyCode 상태를 설정 하 고 지정 된 상태로 디버거에 의해 알려진 모든 예외를 설정 하려면이 인터페이스를 호출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 상속 된 메서드 외에도 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), `IDebugEngine3` 인터페이스는 다음 메서드를 노출 합니다.  
  
|메서드|Description|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|디버깅 기호를 검색 하는 DE는 데 사용할 경로 또는 경로 설정 합니다.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|기호를 로드 아직 발생 하지 않은 모든 모듈에 대 한 기호를 로드 합니다.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|JustMyCode 정보는 DE를 알려 줍니다.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|메트릭을 통해 DE GUID를 설정합니다.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|지정 된 상태로 현재 완료 되지 않은 모든 예외를 설정 합니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
