---
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50d80242ca516c5fa7f3ad297250e25c782664d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350376"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
이 인터페이스를 구현 하는 개체의 컬렉션을 나타냅니다 합니다 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스입니다.

## <a name="syntax"></a>구문

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자를 구현 하는 개체의 집합을 제공 하 여이 인터페이스는 구현 된 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스입니다. 있어 표준 COM 열거형을 아닌지 확인 합니다 [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) 메서드.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 이 인터페이스는 반환한 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) 하 고 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|다음 집합을 검색 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 열거형 개체입니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|지정된 된 개수의 항목을 건너뜁니다.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|첫 번째 항목을 열거를 다시 설정합니다.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|현재 열거형의 복사본을 검색 합니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|열거형 항목을 검색합니다.|

## <a name="remarks"></a>설명

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)