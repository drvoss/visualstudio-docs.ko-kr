---
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74202c4342ae5880f277299b6bb94dcdadff26f5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311416"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` 포트 공급자 프로세스에 연결 되지 않음을 안전 하 게 사용자에 게 경고에 의해 구현 됩니다.

## <a name="syntax"></a>구문

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugProcessSecurity`합니다.

|메서드|설명|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|포트 공급자에서 사용자 이름을 가져옵니다.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|디버깅 프로세스에 연결 되지 않음을 안전 하 게 사용자에 게 경고 합니다.|

## <a name="remarks"></a>설명
 경고를 표시 하 고 사용자가 연결 된 프로세스는 안전 하지 않은 간주할 수 있으면 취소 하도록 허용 하려면이 인터페이스를 구현 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [포트](../../../extensibility/debugger/ports.md)
- [포트 공급자](../../../extensibility/debugger/port-suppliers.md)
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)