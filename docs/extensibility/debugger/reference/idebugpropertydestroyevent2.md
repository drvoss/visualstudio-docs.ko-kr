---
title: IDebugPropertyDestroyEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5ae38bf190a88b91e61971b724893f35c652785
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120665"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
이 인터페이스는 세션 디버그 관리자 (SDM) 특정 문서와 연결 된 속성 소멸 되려고 할 때 디버그 엔진 (DE)에 의해 보내집니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugPropertyDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE 속성 소멸 된 보고 하기 위해이 인터페이스를 구현 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 해당이 인터페이스와 같은 개체에 대해 인터페이스를 구현 해야 합니다. SDM 사용 하 여 [QueryInterface](/cpp/atl/queryinterface) 액세스로는 `IDebugEvent2` 인터페이스입니다. 이 인터페이스는 DE 스크립트;와 연결 된 속성을 이전에 만든가 경우에 구현 됩니다. IDE에서 관련된 스크립트를 제거 속성을 제거 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 참고 사항  
 DE을 만들어 속성 소멸 된 보고서에이 이벤트 개체를 보냅니다. 이벤트를 사용 하 여 보내집니다는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 디버깅 중인 프로그램에 연결 될 때은 SDM에서 제공 되는 콜백 함수입니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugPropertyDestroyEvent2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|소멸 되도록 속성을 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 에 대 한 설명을 참조 [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) 이유에 대 한 자세한 내용은 이러한 이벤트는 사용 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [코어 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)