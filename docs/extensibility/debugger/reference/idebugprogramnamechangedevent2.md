---
title: IDebugProgramNameChangedEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b0b1ff52523a91bfa15192de56dfdc6f0f58354
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351196"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
프로그램의 이름을 변경 하는 경우 디버그 엔진 (DE)에서 (SDM) 세션 디버그 관리자에 게 전송 합니다.

## <a name="syntax"></a>구문

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE 프로그램의 이름이 변경 된 보고서에이 인터페이스를 구현 합니다. 합니다 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 이 인터페이스와 동일한 개체에서 인터페이스를 구현 해야 합니다. SDM 사용 [QueryInterface](/cpp/atl/queryinterface) 액세스 하는 **IDebugEvent2** 인터페이스입니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 DE을 만들어 프로그램 이름 변경을 보고 하려면이 이벤트 개체를 보냅니다. DE를 사용 하 여이 이벤트를 전송 합니다 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 디버깅 중인 프로그램에 연결할 때 SDM에서 제공 하는 콜백 함수. 사용자 지정 포트 공급자는이 이벤트를 사용 하 여 인터페이스를 보냅니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll