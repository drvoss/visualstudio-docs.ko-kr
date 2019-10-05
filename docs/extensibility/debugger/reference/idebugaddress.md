---
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653d2424d21a18e7053f66e0a74214ecc25d97da
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317916"
---
# <a name="idebugaddress"></a>IDebugAddress
이 인터페이스는 항목의 주소를 나타냅니다. 기호 처리기에서 반환 됩니다.

## <a name="syntax"></a>구문

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자 개체의 주소를 나타내는 데이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 여러 인터페이스에서 여러 메서드는이 인터페이스를 반환합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 다음 메서드를 구현합니다.

|메서드|설명|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|검색을 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 개체 및 해당 위치를 설명 하는 구조입니다.|

## <a name="remarks"></a>설명
 기호 공급자를 나타내는 개체 및 해당 위치 (예: 함수, 메서드 또는 클래스)는 특정 범위 내에서이 인터페이스를 반환 합니다. 이 인터페이스에서 반환 되어 기호 공급자 및 식의 다양 한 메서드에 전달할 계산기입니다. 일반적으로 기호 공급자는이 인터페이스의 내용을 해석 해야 하는 유일한 엔터티입니다.

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)