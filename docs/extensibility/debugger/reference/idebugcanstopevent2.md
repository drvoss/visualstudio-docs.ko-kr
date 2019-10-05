---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab364b426005c838072fabc1a3c7ed2f7d64ac6a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337335"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
이 인터페이스는 세션 디버그 관리자 (SDM) 현재 코드 위치에서 중지를 요청에 사용 됩니다.

## <a name="syntax"></a>구문

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE) 소스 코드를 한 단계씩 실행을 지원 하기 위해이 인터페이스를 구현 합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 이 인터페이스와 동일한 개체에서 인터페이스를 구현 해야 (SDM 사용 [QueryInterface](/cpp/atl/queryinterface) 액세스 하는 `IDebugEvent2` 인터페이스).

 SDM의 호출을 통신 해야 하는이 인터페이스의 구현을 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) 디버그 엔진에 있습니다. 예를 들어 스레드를 처리 하는 디버그 엔진의 메시지를 게시 하는 메시지를 사용 하 여이 작업을 수행할 수 있습니다 또는이 인터페이스를 구현 하는 개체 수 디버그 엔진에 대 한 참조를 저장 및 콜백할 디버그 엔진에 전달 하는 플래그를 사용 하 여 `IDebugCanStopEvent2::CanStop`입니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 DE이이 메서드는 DE는 계속 실행 하 고는 DE 라는 메시지가 표시 될 때마다 실행 하는 단계별 코드를 통해 보낼 수 있습니다. 이 이벤트를 사용 하 여 보냅니다 합니다 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM를 디버깅 중인 프로그램에 연결할 때 제공한 콜백 함수입니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugCanStopEvent2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|이 이벤트에 대 한 이유를 가져옵니다.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|디버그 중인 프로그램을이 이벤트와 송신 중지 이유를 설명 하는 이벤트의 위치에서 중지, 방금 실행을 계속 지정 합니다.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|이 이벤트의 위치를 설명 하는 문서 컨텍스트를 가져옵니다.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|이 이벤트의 위치를 설명 하는 코드 컨텍스트를 가져옵니다.|

## <a name="remarks"></a>설명
 DE 함수에는 DE 사용자 단계 찾습니다 없는 디버그 정보 또는 디버그 정보 존재 하지만 DE 모르는 경우 해당 위치에 대 한 소스 코드를 표시할 수 있습니다 하는 경우이 인터페이스를 보냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)