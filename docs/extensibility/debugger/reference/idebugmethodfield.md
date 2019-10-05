---
title: IDebugMethodField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a4b8557226ad010968772562aa787472f159900
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324098"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
이 인터페이스는 메서드를 설명합니다.

## <a name="syntax"></a>구문

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자를 구현 하는 동일한 개체에서이 인터페이스를 구현 합니다 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스입니다. 이 인터페이스는 메서드를 제공 하는 특수화입니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 사용 하 여 [QueryInterface](/cpp/atl/queryinterface) 에서이 인터페이스를 가져올 수 합니다 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 반환 `FIELD_TYPE_METHOD`합니다. 또한 메서드 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), 및 [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)를 모두 반환 합니다 `IDebugMethodField` 인터페이스입니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 메서드 외에도 합니다 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 및 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스에서이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|메서드의 매개 변수에 대 한 열거자를 만듭니다.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|메서드를 포함 하는 개체의 "this"이 포인터를 가져옵니다.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|메서드의 모든 로컬 변수에 대 한 열거자를 만듭니다.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|메서드는 선택한 지역 변수에 대 한 열거자를 만듭니다.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|특정 사용자 지정 특성 정의 되었는지 여부를 결정 합니다.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|메서드는 정적 지역 변수에 대 한 열거자를 만듭니다.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|메서드의 전역 컨테이너를 가져옵니다.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|메서드를 호출 하는 데 필요한 각 인수의 형식에 대 한 열거자를 만듭니다.|

## <a name="remarks"></a>설명
 메서드 매개 변수 뿐만 아니라 지역 변수를 포함할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)