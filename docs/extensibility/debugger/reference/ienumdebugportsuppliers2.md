---
title: IEnumDebugPortSuppliers2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39d9d9462fe1951f01927b9180fa8a99aee535be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326385"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
이 인터페이스는 포트 공급자를 열거합니다.

## <a name="syntax"></a>구문

```
IEnumDebugPortSuppliers2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 Visual Studio의 포트 공급 업체 목록을 나타내는 데이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 호출 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) 포트 공급자의 목록을 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IEnumDebugPortSuppliers2`합니다.

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|열거형 시퀀스에서 포트 공급자의 지정된 된 수를 검색 합니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|열거형 시퀀스에서 포트 공급자의 지정된 된 수를 건너뜁니다.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|열거형 시퀀스를 처음으로 다시 설정합니다.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|현재 열거자와 열거 상태가 같은 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|열거자에서 포트 공급 업체의 수를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스를 가져올 일반적으로 디버그 엔진을 설치 하지 필요가 없습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)