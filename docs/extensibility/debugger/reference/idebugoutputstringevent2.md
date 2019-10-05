---
title: IDebugOutputStringEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d47fe2b329f9f2fb4adb57cdf6e2a6a871299d14
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311893"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
이 인터페이스는 문자열로 출력 하려면 세션 디버그 관리자 (SDM)에 디버그 엔진 (DE)에서 전송 됩니다.

## <a name="syntax"></a>구문

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE에 문자열을 보내는이 인터페이스를 구현 합니다 **출력** IDE의 창. 합니다 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 이 인터페이스와 동일한 개체에서 인터페이스를 구현 해야 합니다. SDM 사용 [QueryInterface](/cpp/atl/queryinterface) 액세스는 `IDebugEvent2` 인터페이스입니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 DE 만들고이 이벤트 개체에 문자열을 보내는 전송 합니다 **출력** 창입니다. 이벤트를 사용 하 여 전송 되는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 디버그 중인 프로그램에 연결 될 때 SDM에서 제공 하는 콜백 함수.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서 메서드의 `IDebugOutputStringEvent2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|표시할 수 있는 메시지를 가져옵니다.|

## <a name="remarks"></a>설명
 예를 들어 비관리 코드에서 문자열 출력을 가져올 수 있습니다 디버깅 중인 프로그램에서 win32 문자열을 보낼 때 `OutputDebugString` 함수입니다. 이 문자열은는 DE 가로채 고으로 SDM로 보내도록 설정 하 여 `IDebugOutputStringEvent2` 이벤트입니다.

 사용 하 여 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) 사용자 응답을 해야 하는 메시지를 보내려고 합니다.

 사용 하 여 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) 응답이 필요 하지 않은 오류 메시지를 보냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)