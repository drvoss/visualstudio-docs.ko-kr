---
title: 식 계산기 구현 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66a1a0cb78036982923d20e39a3a4c32b288e459
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326206"
---
# <a name="implement-an-expression-evaluator"></a>식 계산기를 구현 합니다.
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 식을 평가 하 여 디버그 엔진 (DE), 기호 공급자 (SP), 바인더 개체 및 식 계산기 (EE) 간에 복잡 한 상호 작용입니다. 이러한 네 가지 구성 요소는 하나의 구성 요소에 의해 구현 되 고 다른 사용 하는 인터페이스에서 연결 됩니다.

 EE는 문자열의 형태로 DE에서 식 사용 및 구문 분석 하거나이 확인 합니다. EE는 독일에서 사용 되는 다음 인터페이스를 실행 합니다.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE 기호 및 개체의 값을 검색할 DE, 제공한 바인더 개체를 호출 합니다. EE는 DE에 의해 구현 되는 다음 인터페이스를 사용 합니다.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  실행 되는 EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)합니다. `IDebugProperty2` 지역 변수, 기본, 또는 후에 적절 한 정보를 표시 하는 Visual Studio로 개체와 같은 식 평가의 결과 설명 하는 메커니즘을 제공 합니다 **지역**, **시청** , 또는 **Immediate** 창입니다.

  SP 때 지정 되는 EE는 DE 하 여 정보에 대 한 요청입니다. SP 주소 및 다음 인터페이스 및 해당 파생 항목 같은 필드를 설명 하는 인터페이스를 실행 합니다.

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE 이러한 인터페이스를 모두 사용합니다.

## <a name="in-this-section"></a>단원 내용
 [식 계산기 구현 전략](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) 식 (EE) 계산기 구현 전략에 대해 3 단계 프로세스를 정의 합니다.

## <a name="see-also"></a>참고자료
- [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)