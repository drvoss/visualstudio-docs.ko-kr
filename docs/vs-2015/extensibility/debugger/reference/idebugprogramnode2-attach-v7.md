---
title: IDebugProgramNode2::Attach_V7 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08028f2b03f3ea36cc72172ca8f9de31740b49f3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417903"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

사용 되지 않습니다. 사용 하지 마세요.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```csharp  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pMDMProgram`  
 [in] 합니다 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 연결할 프로그램을 나타내는 인터페이스입니다.  
  
 `pCallback`  
 [in] 합니다 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM에 디버그 이벤트를 보내는 데 사용할 인터페이스입니다.  
  
 `dwReason`  
 [in] 값을 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) 연결에 대 한 이유를 지정 하는 열거형입니다.  
  
## <a name="return-value"></a>반환 값  
 구현을 항상 반환 `E_NOTIMPL`합니다.  
  
## <a name="remarks"></a>설명  
  
> [!WARNING]
> 일부로 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)],이 메서드는 더 이상 사용 하 고 항상 반환 `E_NOTIMPL`합니다. 참조 된 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 노드는 경우 프로그램에 연결할 수 없습니다를 나타내기 위해 또는 프로그램 노드 프로그램을 설정 하는 경우 다른 방법에 대 한 인터페이스 `GUID`합니다. 그렇지 않으면 구현 된 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드.  
  
## <a name="prior-to-visual-studio-2005"></a>Visual Studio 2005 이전  
 이 메서드는 디버그 중인 프로그램의 주소 공간에서 실행 되는 DE 하는 경우에 구현 해야 합니다. 그렇지 않으면이 메서드에서 반환 해야 `S_FALSE`합니다.  
  
 이 메서드를 호출 하는 경우에 DE 전송 해야 합니다는 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) 이미이 인스턴스에 대 한 전송 되지 않은 경우 이벤트 개체를 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 인터페이스와 [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 하 고 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 이벤트 개체입니다. [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) 이벤트 개체는 다음 경우를 `dwReason` 매개 변수는 `ATTACH_REASON_LAUNCH`합니다.  
  
 DE 호출 해야 합니다는 [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 메서드는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 에서 제공 하는 개체를 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 이벤트 개체를 해당 프로그램의 GUID를 저장 해야 합니다 인스턴스 데이터에 `IDebugProgram2` 는 DE 구현한 개체입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
