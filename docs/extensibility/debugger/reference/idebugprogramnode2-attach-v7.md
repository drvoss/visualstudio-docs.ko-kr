---
title: IDebugProgramNode2::Attach_V7 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea09304d4481ed649f24985b3cabb2a6b1944311
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941635"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> 사용 되지 않습니다. 사용 하지 마세요.

## <a name="syntax"></a>구문

```cpp
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

`pMDMProgram` [in] 합니다 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 연결할 프로그램을 나타내는 인터페이스입니다.

 `pCallback` [in] 합니다 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM에 디버그 이벤트를 보내는 데 사용할 인터페이스입니다.

 `dwReason` [in] 값을 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) 연결에 대 한 이유를 지정 하는 열거형입니다.

## <a name="return-value"></a>반환 값

구현을 항상 반환 `E_NOTIMPL`합니다.

## <a name="remarks"></a>설명

> [!WARNING]
> Visual Studio 2005를 기준으로이 메서드는 더 이상 및 항상 반환 `E_NOTIMPL`합니다. 참조 된 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 노드는 경우 프로그램에 연결할 수 없습니다를 나타내기 위해 또는 프로그램 노드 프로그램을 설정 하는 경우 다른 방법에 대 한 인터페이스 `GUID`합니다. 그렇지 않으면 구현 된 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드.

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