---
title: IDebugModule2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b621ae3b1408bc4af371243a1c34909117d40576
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323930"
---
# <a name="idebugmodule2"></a>IDebugModule2
이 인터페이스는 모듈을 나타냅니다-프로그램에서 실행 파일 단위 이므로, DLL 등입니다.

## <a name="syntax"></a>구문

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE) 모듈을 나타내는 하 고 해당 모듈에 대 한 정보에 대 한 액세스를 제공 하기에이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 에 대 한 호출 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) 이 인터페이스를 반환 합니다. DE 보냅니다 합니다 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) 인터페이스를 사용 하 여 세션 디버그 관리자 (SDM)에 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 메서드.

 이 인터페이스에서 반환 될 수도 있습니다는 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조 (에 대 한 호출에서 반환 된 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).

- [다음](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) 또한이 인터페이스를 반환 합니다 ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) 반환 된 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) 인터페이스).

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugModule2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|가져옵니다 합니다 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 는이 모듈에 설명 합니다.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|사용되지 않습니다. 사용 하지 마세요. 이 모듈의 기호를 다시 로드합니다.|

## <a name="remarks"></a>설명
 모듈 정보를 표시할 합니다 **모듈** IDE의 창.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)