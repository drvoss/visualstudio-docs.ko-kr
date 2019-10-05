---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d080b3073ffc13b90870b40a16a353634f4aa0cf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352016"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

디버그 엔진 (DE) 프로그램을 중지 하는 경우이 선택적 이벤트 (SDM) 세션 디버그 관리자에 게 보낼 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항

이 인터페이스는 Visual Studio 2005에 도입 되었습니다. 이전 릴리스에서 비동기 중지를 지원 하지 않았습니다.

- [중지](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 다중 프로세스 또는 다중 프로그램 시나리오에서 SDM에 의해 호출 됩니다. 한 프로그램 중지 이벤트를 보내면 SDM, SDM을 너무 중지 하려면 다른 프로그램을 요청 합니다.

중지는 비동기적으로 프로그램을 중지 하는 SDM을 알리는 데 사용 됩니다. SDM 인터프리터 디버그 엔진에 대 한 유용 알리는, 코드 없이 디버깅 내에서 실행 되는 경우에 따라에 있는 프로그램을 [중지](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) 동기적으로 완료할 수 없습니다. 반환 해야 하는 경우 디버그 엔진을 원하는이 비동기 알림을 사용할 `S_ASYNC_STOP` 에서 [중지](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)합니다.

## <a name="requirements"></a>요구 사항

헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll