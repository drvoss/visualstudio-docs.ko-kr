---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 580d4d2432a957bae8c590b3590a11b1a0b5e84e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148522"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

프로그램 노드를를 연결 된 프로그램에 연결 하지 못했습니다. 알림을 받을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 이 인터페이스를 구현 하는 동일한 클래스에서 구현 되는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스 연결 작업에 대 한 알림을 받으려면 및 연결 작업을 취소할 수 있는 기회를 제공 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 호출 하 여이 인터페이스를 가져올는 `QueryInterface` 의 메서드는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체입니다. 합니다 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드를 호출 하기 전에 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md) 프로그램 노드 연결 프로세스를 중지할 수 있도록 하는 방법.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 이 인터페이스는 다음 메서드를 구현합니다.  
  
|메서드|Description|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|연결된 프로그램에 연결 하거나 연결 프로세스를 지연 합니다 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 기본 설정된 대신 사용 되지 않는 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) 메서드. 모든 디버그 엔진으로 항상 로드 됩니다는 `CoCreateInstance` 함수, 즉, 디버깅 중인 프로그램의 주소 공간 외부 인스턴스화됩니다.  
  
 경우의 이전 구현을 `IDebugProgramNode2::Attach_V7` 메서드를 설정 합니다 `GUID` 디버깅 중인 프로그램을 다음만의 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드를 구현 해야 합니다.  
  
 이전 구현 하는 경우는 `IDebugProgramNode2::Attach_V7` 제공 된 콜백 인터페이스를 사용 하는 메서드를 해당 기능 구현에 이동 해야 합니다 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드 및 `IDebugProgramNodeAttach2` 인터페이스 하지 않습니다 구현 해야 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Msdbg.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
