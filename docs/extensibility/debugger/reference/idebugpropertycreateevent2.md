---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83a7e0aaae01e21c67a6d030caebb476779779f7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348617"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
이 인터페이스는 특정 문서와 연결 된 속성을 만들 때 세션 디버그 관리자 (SDM)에 디버그 엔진 (DE)에서 전송 됩니다.

## <a name="syntax"></a>구문

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE 속성을 이미 만들었다고 보고 하려면이 인터페이스를 구현 합니다. 합니다 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 이 인터페이스와 동일한 개체에서 인터페이스를 구현 해야 합니다. SDM 사용 [QueryInterface](/cpp/atl/queryinterface) 액세스는 `IDebugEvent2` 인터페이스입니다. 이 인터페이스는 DE에서 로드 되거나 생성 된 스크립트를 사용 하 여 연결 된 속성을 만든 경우 및 해당 스크립트를 IDE에서 표시 해야 하는 경우에 구현 됩니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 DE 만들고이 이벤트 개체 속성이 생성 된 보고서를 보냅니다. 이벤트를 사용 하 여 전송 되는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 디버그 중인 프로그램에 연결 될 때 SDM에서 제공 하는 콜백 함수.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에의 메서드는 `IDebugPropertyCreateEvent2` 인터페이스입니다.

|메서드|설명|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|새 속성을 가져옵니다.|

## <a name="remarks"></a>설명
 속성을 특정 문서 또는 연결 된 스크립트에는 DE을 보낼 수 있습니다이 이벤트는 SDM 업데이트 하기 위해 합니다 **스크립트 문서** 문서의 이름이 있는 창입니다. SDM을 호출 하는 [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) 인수를 사용 하 여 `guidDocument` 를 검색 하는 `VARIANT` 포함 하는 [IUnknown](/cpp/atl/iunknown) 포인터입니다. SDM 호출 [QueryInterface](/cpp/atl/queryinterface) 검색할이 포인터에 대 한 합니다 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 업데이트 하는 데 사용 되는 인터페이스를 **스크립트 문서** 창.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)