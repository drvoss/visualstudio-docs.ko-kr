---
title: IDebugPointerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc6939296fa2bfa59aad1824529f8b708a4cd5cb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308854"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
이 인터페이스에 대 한 포인터 형식을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자에 대 한 포인터를 나타내는 데이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 사용 하 여 [QueryInterface](/cpp/atl/queryinterface) 에서이 인터페이스를 가져올 수 합니다 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 반환 `FIELD_TYPE_POINTER`합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 메서드 외에도 합니다 `IDebugField` 및 `IDebugContainerField` 인터페이스에서이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|반환 된 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 포인터의 대상을 설명 하는 합니다.|

## <a name="remarks"></a>설명
 C에서 /C++에 대 한 포인터 배열 표기법을 사용 하 여 사용 하는 경우 컨테이너가 될 수 있습니다. 예를 들어 `char *pString`하십시오 `pString` 에 대 한 포인터 형식이 `char`합니다. `pString[3]` 컨테이너에 대 한 포인터는 형식이 `char` 해당 컨테이너의 네 번째 요소를 참조 하는 합니다.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)