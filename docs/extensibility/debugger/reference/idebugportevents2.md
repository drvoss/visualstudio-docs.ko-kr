---
title: IDebugPortEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5690108aaeede2cf15cc5fac927a3dc5ab3855ab
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326724"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
이 인터페이스는 프로세스 및 프로그램 만들기 및 소멸을 특정 포트에서의 수신기를 (일반적으로 세션 디버그 관리자 [SDM] 또는 디버그 엔진)에 게 알립니다. 프로세스 및 포트에서 실행 중인 프로그램의 실시간 보기를 제공 합니다.이 정보를 사용할 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 Visual Studio는 일반적으로 프로그램 생성 및 소멸에 대 한 알림을 수신 하려면이 인터페이스를 구현 합니다. 디버그 엔진을 이러한 포트 이벤트를 수신 하려면이 인터페이스를 구현할 수도 있습니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 모든 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스를 쿼리할 수는 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 인터페이스입니다. 그런 다음 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> 에 대 한 메서드 `IDebugPortEvents2` 에서 호출 되는 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 가져올 인터페이스는 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 인터페이스. 마지막으로 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> 의 메서드를 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 인터페이스를 통해 이벤트를 전송 하기 위해 호출 됩니다 합니다 [이벤트](../../../extensibility/debugger/reference/idebugportevents2-event.md) 메서드.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서 메서드의 `IDebugPortEvents2`합니다.

|메서드|설명|
|------------|-----------------|
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|생성 및 소멸 프로세스 및 포트에서 프로그램을 설명 하는 이벤트를 보냅니다.|

## <a name="remarks"></a>설명
 `IDebugPortEvents2` 에서도 SDM 이미 디버깅 중인 프로세스에서 실행 되는 프로그램을 디버그 합니다.

 이 인터페이스에서 SDM 포트 이벤트 전달 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)