---
title: IEnumDebugPropertyInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbf6e2f5c644f340ca2c1ebba1d53fc026b0534b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322705"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
이 인터페이스를 열거 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조입니다.

## <a name="syntax"></a>구문

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (독일) 특정 속성에 대 한 정보를 나타내는 데이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 호출 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 특정 속성의 자식을 나타내는이 인터페이스를 가져올 수 있습니다. 호출 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) 특정 스택 프레임의 속성을 나타내는이 인터페이스를 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IEnumDebugPropertyInfo2`합니다.

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|지정된 된 수의 검색 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 열거형 시퀀스에는 구조입니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|지정 된 개수의 건너뜁니다 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 열거형 시퀀스에는 구조입니다.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|열거형 시퀀스를 처음으로 다시 설정합니다.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|현재 열거자와 열거 상태가 같은 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|개수를 가져옵니다 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 열거자 구조입니다.|

## <a name="remarks"></a>설명
 일반적으로 속성은 계층 이름, 값, 주소 및 형식을 포함할 수 있는 정보 뿐만 아니라 연결된 속성 개체 또는 스택 프레임에 적절 한 기타 정보입니다. 참조 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 대 한 자세한 내용은 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)