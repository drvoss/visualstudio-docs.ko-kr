---
title: IDebugFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fb0d969268e7765abe5c3ebdc9fc000a10a3aa0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313446"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 이 인터페이스는 함수를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 식 계산기는 함수를 나타내는 데이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 이 인터페이스의 특수화 인 합니다 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스를 사용 하 여 가져온 [QueryInterface](/cpp/atl/queryinterface) 에 `IDebugObject` 인터페이스입니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 상속 된 메서드 외에도 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugFunctionObject` 인터페이스는 다음 메서드를 노출 합니다.

|메서드|설명|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|기본 데이터 개체를 만듭니다.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|생성자를 사용 하 여 개체를 만듭니다.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|생성자를 사용 하 여 개체를 만듭니다.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|배열 개체를 만듭니다.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|문자열 개체를 만듭니다.|
|[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|함수를 호출 하 고 결과 개체 값을 반환 합니다.|

## <a name="remarks"></a>설명
 이 인터페이스를 구문 분석 트리의 함수를 나타내는 식 계산기를 수 있습니다. `Create` 이 인터페이스에서 메서드는 메서드에 입력된 매개 변수를 나타내는 개체를 생성 하는 데 사용 됩니다. 함수를 호출 하 여 실행할 수 있습니다 합니다 [평가](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 함수의 반환 값을 나타내는 개체를 반환 하는 메서드.

## <a name="requirements"></a>요구 사항
 헤더: ee.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [식 계산 인터페이스](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)