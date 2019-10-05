---
title: IDebugPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb489cddf090bf9958dee57f424ba009eb2c2209
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326841"
---
# <a name="idebugport2"></a>IDebugPort2
이 인터페이스는 시스템에서 디버그 포트를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 사용자 지정 포트 공급자 컴퓨터에서 디버그 포트를 나타내는 데이 인터페이스를 구현 합니다.

 포트에서 송신 포트 이벤트를 지 원하는 경우 해당 구현 해야 합니다는 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 지원에 대 한 인터페이스를 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> 에서 제공 하는 인터페이스를 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) 인터페이스입니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 에 대 한 호출 [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) 하거나 [포트 추가](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 요청 된 포트를 나타내는이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugPort2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|포트 이름을 반환합니다.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|포트 식별자를 반환합니다.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|(있는 경우) 포트를 만드는 데 요청을 반환 합니다.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|이 포트에 대 한 포트 공급자를 반환합니다.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|프로세스의 식별자를 지정 된 프로세스에는 인터페이스를 반환 합니다.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|포트에서 실행 중인 모든 프로세스를 열거 합니다.|

## <a name="remarks"></a>설명
 로컬 포트는 모든 프로세스 및 로컬 컴퓨터에서 실행 중인 프로그램에 대 한 액세스를 제공 합니다. 다른 포트는 Windows CE 기반 장치에 직렬 케이블 연결 또는 DCOM이 아닌 컴퓨터에 네트워크 연결을 나타낼 수 있습니다. `IDebugPort2` 인터페이스는 이름 및 포트의 식별자를 찾을 포트에서 실행 중인 모든 프로세스를 열거 하는 데 사용 됩니다. 시작 하 고 포트에서 프로세스를 종료 하는 기능에서 구현 되는 `IDebugPortEx2` 인터페이스입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)