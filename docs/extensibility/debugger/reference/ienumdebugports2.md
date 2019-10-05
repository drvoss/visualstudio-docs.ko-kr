---
title: IEnumDebugPorts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c24edcd5ef47408cd4c11b3d0548ad34516702a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326514"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
이 인터페이스는 컴퓨터 또는 포트 공급자의 포트를 열거합니다.

## <a name="syntax"></a>구문

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 사용자 지정 포트 공급자 공급 업체에서 만든 포트의 목록을 나타내는 데이 인터페이스를 구현 합니다. Visual Studio 자체 포트 공급자를 지원 하기 위해이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 호출 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) 포트 공급자가 생성 하는 포트 목록을 나타내는이 인터페이스를 가져올 수 있습니다. 호출 [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) 저장 된 포트의 목록을 나타내는이 인터페이스를 가져올 디스크에 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IEnumDebugPorts2`합니다.

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|열거형 시퀀스에서 포트의 지정된 된 수를 검색 합니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|열거형 시퀀스에서 포트를 지정 된 수를 건너뜁니다.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|열거형 시퀀스를 처음으로 다시 설정합니다.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|현재 열거자와 열거 상태가 같은 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|열거자에서 포트 번호를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio 프로세스에 연결 하는 데 사용 되는 포트 목록을 채우는 데이 인터페이스를 사용 합니다.

 디버그 엔진을 일반적으로이 인터페이스를 사용 하지 않습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)