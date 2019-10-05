---
title: IDebugField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80def3f9c3d270ebd6f2217f6ce39f07ef27b119
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337517"
---
# <a name="idebugfield"></a>IDebugField
이 인터페이스는 필드를, 즉, 기호 또는 형식에 대 한 설명을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자는 모든 필드에 대 한 기본 클래스와이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 이 인터페이스는 모든 필드에 대 한 기본 클래스입니다. 반환 값에 따라 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md),이 인터페이스를 사용 하 여 더욱 특수화 된 인터페이스를 반환할 수 있습니다 [QueryInterface](/cpp/atl/queryinterface)합니다. 또한 많은 인터페이스 반환 `IDebugField` 다양 한 메서드에서 개체입니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugField`합니다.

|메서드|설명|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|기호 또는 형식에 대 한 표시할 수 있는 정보를 가져옵니다.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|필드의 종류를 가져옵니다.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|필드의 형식을 가져옵니다.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|필드의 컨테이너를 가져옵니다.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|필드의 주소를 가져옵니다.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|바이트에 있는 필드의 크기를 가져옵니다.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|확장 필드에 대 한 정보를 가져옵니다.|
|[Equal](../../../extensibility/debugger/reference/idebugfield-equal.md)|두 필드를 비교합니다.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|기호 또는 형식에 대 한 형식에 관계 없이 정보를 가져옵니다.|

## <a name="remarks"></a>설명
 형식은 C 언어에 해당 `typedef`합니다.

 다음에서 C++ 언어 예제 `weather` 형식인 클래스 및 `sunny` 하 고 `stormy` 기호:

```cpp
class weather;
weather sunny;
weather stormy;
```

 필드 기호를 나타냅니다 여부 형식을 호출 하 여 확인할 수 있습니다 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 를 검토 하는 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 결과입니다. 경우는 `FIELD_KIND_TYPE` 비트가 설정 되는 필드 형식에 경우에 `FIELD_KIND_SYMBOL` 비트가 이며 기호.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)