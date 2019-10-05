---
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b45cbe8cd1b68e1681b07fcdf1fc715973a11295
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325256"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
이 인터페이스는 모든 가능한 있는 디버그 엔진 (DE)이이 프로그램을 디버깅할 수를 지정 하려면 프로그램 노드에서 사용 됩니다.

## <a name="syntax"></a>구문

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE 또는 사용자 지정 포트 공급자 구현 하는 동일한 개체에서이 인터페이스를 구현 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 특정 프로그램에 사용할 특정 DE를 설정할 수 있습니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 호출 [QueryInterface](/cpp/atl/queryinterface) 에 `IDebugProgramNode2` 인터페이스가이 인터페이스를 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugProgramEngines2`합니다.

|메서드|설명|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|이 프로그램을 디버그할 수 있는 모든 가능한 DEs를 나타냅니다.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|이 프로그램을 디버깅 하는 데는 DE를 선택 합니다.|

## <a name="remarks"></a>설명
 선택 항목을 호출 하 여 등록 된 프로그램 노드는 DE를 사용자가 선택한 후 [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)합니다. 선택한 엔진은 엔진에서 반환한 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)