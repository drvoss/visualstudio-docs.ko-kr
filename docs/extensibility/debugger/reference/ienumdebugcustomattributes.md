---
title: IEnumDebugCustomAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e706999595033ac76508eaa5e3b3f995839ceaea
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321551"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
사용자 지정 특성을 열거합니다.

## <a name="syntax"></a>구문

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 사용자 지정 특성을 지원 하기 위해이 인터페이스를 구현 하는 기호 공급자 (통해 합니다 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) 인터페이스).

## <a name="notes-for-callers"></a>호출자에 대 한 정보
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) 이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IEnumDebugCustomAttributes`합니다.

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|열거형 시퀀스에서 사용자 지정 특성의 지정된 된 수를 검색 합니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|열거형 시퀀스에서 사용자 지정 특성의 지정된 된 수를 건너뜁니다.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|열거형 시퀀스를 처음으로 다시 설정합니다.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|현재 열거자와 열거 상태가 같은 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|열거자의 사용자 지정 특성의 수를 가져옵니다.|

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)