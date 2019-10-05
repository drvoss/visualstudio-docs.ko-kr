---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6579481f44006cc3f77e57a9c9ecbd327c3b7409
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350291"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
이 인터페이스를 열거 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조입니다.

## <a name="syntax"></a>구문

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진 (DE)는 현재 호출 스택을 설명 하는 구조체의 목록을 제공 하기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 Visual Studio 호출 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 중단점 될 때마다이 인터페이스를 가져오려면 예외 또는 중단 발생 디버깅 중인 프로그램입니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IEnumDebugFrameInfo2`합니다.

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|지정된 된 수의 검색 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 열거형 시퀀스에는 구조입니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|지정 된 개수의 건너뜁니다 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 열거형 시퀀스에는 구조입니다.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|열거형 시퀀스를 처음으로 다시 설정합니다.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|현재 열거자와 열거 상태가 같은 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|개수를 가져옵니다 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 열거자 구조입니다.|

## <a name="remarks"></a>설명
 Visual Studio 중단점, 예외 또는 디버그 중인 프로그램에서 사용자 생성 일시 중지를 처리 하는 첫 번째 단계로이 인터페이스를 가져옵니다. 목록을 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조 현재 호출 스택을 나타냅니다, 목록 및 가장 오래 된 함수의 시작 부분에 현재 함수 호출 목록의 끝에서 호출 합니다. 각 `FRAMEINFO` 컨텍스트는 식을 계산할 수 있습니다 하 고 로컬 변수를 살펴 스택 프레임을 나타냅니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)