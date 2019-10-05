---
title: IDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97fd6c328b15c8e41dbbc2b4e45bfc4285b4273f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319023"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 이 인터페이스는 기호 및 식의 값을 캡슐화 하는 바인더 만드는 개체를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 식 계산기를 개체가이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 이 인터페이스는 식 계산기 구문 분석 된 식에서 사용 하는 모든 개체에 대 한 기본 클래스입니다. 호출 하 여 반환 되는 [바인딩할](../../../extensibility/debugger/reference/idebugbinder-bind.md) 메서드. [QueryInterface](/cpp/atl/queryinterface) 이 인터페이스에서 보다 특수화 된 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugObject`합니다.

|메서드|설명|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|개체의 크기를 가져옵니다.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|연속 된 일련의 바이트로으로 개체의 값을 가져옵니다.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|연속 된 일련의 바이트에서 개체의 값을 설정 합니다.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|이 개체의 참조 값을 설정합니다.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|개체의 값의 주소를 나타내는 메모리 컨텍스트를 가져옵니다.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|디버그 엔진의 주소 공간에서 관리 되는 개체의 복사본을 만듭니다.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|이 개체는 null 참조 인지 테스트 합니다.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|이 개체를 비교합니다.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|이 개체가 읽기 전용인 경우를 결정 합니다.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|투명 프록시 개체 인지 확인 합니다.|

## <a name="remarks"></a>설명
 식 계산기 구문 분석 트리에 개체를 나타내는 기본 클래스와이 인터페이스를 사용 합니다.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [식 계산 인터페이스](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)