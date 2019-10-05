---
title: 지역 변수의 구현 샘플 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c65ed0e3def028e710255d08ee1fe40080bfde5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315025"
---
# <a name="sample-implementation-of-locals"></a>지역 변수의 샘플 구현
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 다음은 Visual Studio 가져오는 방법을 지역 메서드에 대 한 식 계산기 (EE)의 개요입니다.

1. Visual Studio 디버그 엔진 (DE)를 호출 [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) 가져오려는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 지역 변수를 포함 하 여 스택 프레임의 모든 속성을 나타내는 개체입니다.

2. `IDebugStackFrame2::GetDebugProperty` 호출 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 중단점이 발생 하는 방법에 설명 하는 개체를 가져옵니다. 기호 공급자를 제공 하는 DE ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), 주소 ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)), 및 바인더 ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty` 호출 [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) 제공 된 `IDebugAddress` 가져올 개체를 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 지정된 된 주소를 포함 하는 메서드를 나타내는입니다.

4. 합니다 `IDebugContainerField` 인터페이스에 대 한 쿼리는 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 인터페이스입니다. 메서드의 지역에 대 한 액세스를 제공 하는이 인터페이스입니다.

5. `IDebugExpressionEvaluator::GetMethodProperty` 클래스를 인스턴스화합니다 (호출 `CFieldProperty` 예제의)를 실행 하는 `IDebugProperty2` 메서드의 지역 변수를 나타내는 인터페이스입니다. 합니다 `IDebugMethodField` 개체에 배치 됩니다 `CFieldProperty` 와 함께 개체를 `IDebugSymbolProvider`, `IDebugAddress`, 및 `IDebugBinder` 개체입니다.

6. 경우는 `CFieldProperty` 개체를 초기화할 [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) 라고 하는 `IDebugMethodField` 가져올 개체를 [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) 메서드 자체에 대 한 모든 표시할 수 있는 정보를 포함 하는 구조입니다.

7. `IDebugExpressionEvaluator::GetMethodProperty` 반환 된 `CFieldProperty` 개체는 `IDebugProperty2` 개체입니다.

8. Visual Studio 호출 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 반환 된 `IDebugProperty2` 필터를 사용 하 여 개체 `guidFilterLocalsPlusArgs`를 반환 하는 프로그램 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 메서드의 지역 변수를 포함 하는 개체입니다. 이 열거형에 대 한 호출에 의해 채워진 [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) 하 고 [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)합니다.

9. Visual Studio 호출 [다음](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) 가져오려고 한 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 각 로컬에 대 한 구조입니다. 이 구조에 대 한 포인터를 포함 한 `IDebugProperty2` 로컬에 대 한 인터페이스입니다.

10. Visual Studio 호출 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 각 로컬 지역 변수의 이름, 값 및 형식을 가져오려고 합니다. 이 정보에 표시 되는 **지역** 창입니다.

## <a name="in-this-section"></a>단원 내용
 [GetMethodProperty 구현](../../extensibility/debugger/implementing-getmethodproperty.md) 의 구현을 설명 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)합니다.

 [지역 변수를 열거](../../extensibility/debugger/enumerating-locals.md) 디버그 엔진 (DE) 열거 지역 변수 또는 인수에 대 한 호출을 사용 하는 방법에 대해 설명 합니다.

 [로컬 속성 가져오기](../../extensibility/debugger/getting-local-properties.md) 는 DE 이름, 형식 및 하나 이상의 지역 변수의 값 가져오기에 대 한 호출을 사용 하는 방법에 대해 설명 합니다.

 [로컬 값을 얻으려면](../../extensibility/debugger/getting-local-values.md) 평가 컨텍스트에 제공한 바인더 개체의 서비스 해야 하는 지역 변수의 값을 가져오는 것에 대해 설명 합니다.

 [지역 평가](../../extensibility/debugger/evaluating-locals.md) 지역 평가 방법에 대해 설명 합니다.

## <a name="related-sections"></a>관련 단원
 [평가 컨텍스트에](../../extensibility/debugger/evaluation-context.md) 는 DE 식 계산기 (EE)를 호출할 때 전달 되는 인수를 제공 합니다.

 [MyCEE 샘플](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f) 방법 한 가지 구현을 MyC 언어에 대 한 식 계산기를 만드는 방법을 보여 줍니다.

## <a name="see-also"></a>참고자료
- [로컬 항목 표시](../../extensibility/debugger/displaying-locals.md)