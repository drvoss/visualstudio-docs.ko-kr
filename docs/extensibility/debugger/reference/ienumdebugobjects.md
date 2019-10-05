---
title: IEnumDebugObjects | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dea4b4781fd8026c29436bbd37a6bfa6824e73b3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339477"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 이 인터페이스를 구현 하는 개체의 컬렉션을 나타냅니다 합니다 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스입니다.

## <a name="syntax"></a>구문

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 식 계산기 구현 하는 개체의 집합을 제공 하려면이 인터페이스를 구현 합니다 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스입니다. 있어 표준 COM 열거형을 아닌지 확인 합니다 [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) 메서드.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) 이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|다음 집합을 검색 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 열거형 개체입니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|지정된 된 개수의 항목을 건너뜁니다.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|첫 번째 항목을 열거를 다시 설정합니다.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|현재 열거형의 복사본을 검색 합니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|열거형 항목을 검색합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 배열에 있는 개체 집합을 열거 하는 디버그 엔진을 허용 합니다.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)