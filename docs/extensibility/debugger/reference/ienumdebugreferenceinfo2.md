---
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b664b068ac7cd30a7475ab14bfe1b064c98142c2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324398"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
이 인터페이스를 열거 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조입니다.

## <a name="syntax"></a>구문

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE) 메모리에 개체에 대 한 참조에 대 한 지원의 일부로이 인터페이스를 구현합니다. 참조를 지 원하는 경우에이 인터페이스를 구현 해야 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 Visual Studio 호출 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) 이 인터페이스를 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IEnumDebugReferenceInfo2`합니다.

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|지정된 된 수의 검색 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 열거형 시퀀스에는 구조입니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|지정 된 개수의 건너뜁니다 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 열거형 시퀀스에서 구조입니다.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|열거형 시퀀스를 처음으로 다시 설정합니다.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|현재 열거자와 열거 상태가 같은 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|개수를 가져옵니다 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 열거자 구조입니다.|

## <a name="remarks"></a>설명
 대 한 참조는 형식과 주소를 기본적으로 속성은 이름, 형식 및 주소입니다. 대 한 참조를 메모리에 존재 하는 개체가 참조 하는 그대로 유지 합니다. 참조 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 대 한 자세한 내용은 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)