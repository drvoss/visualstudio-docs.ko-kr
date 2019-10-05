---
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5ad1f7a3f954116350e8accbdc9db02d0ac920d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319602"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
이 인터페이스에는 코드 경로의 목록을 나타냅니다.

## <a name="syntax"></a>구문

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE) 코드 경로의 목록을 나타내는 데이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 호출 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) 이 인터페이스를 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IEnumCodePaths2`합니다.

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|열거형 시퀀스에 대 한 코드 경로의 지정된 된 수를 검색 합니다.|
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|열거형 시퀀스에 대 한 코드 경로의 지정 된 수를 건너뜁니다.|
|[Reset](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|열거형 시퀀스를 처음으로 다시 설정합니다.|
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|현재 열거자와 열거 상태가 같은 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|열거자에서 코드 경로 수를 가져옵니다.|

## <a name="remarks"></a>설명
 코드 경로는 프로그램에서 분기 지점 또는 함수 호출을 나타냅니다. 코드 경로 목록이 있는 코드 실행 되었고 경로 나타냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)