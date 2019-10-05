---
title: 식 계산기 인터페이스 키 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f633d1b3bba5fbd5ecbfb44051740a0bc4bb09f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344224"
---
# <a name="key-expression-evaluator-interfaces"></a>Key 식 계산기 인터페이스
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 평가 컨텍스트에 함께 식 계산기 (EE)를 작성 하는 경우에 다음 인터페이스를 사용 하 여 친숙 한 해야 합니다.

## <a name="interface-descriptions"></a>인터페이스 설명

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     단일 메서드가 [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), 현재 실행 지점을 나타내는 데이터 구조는 가져오는 합니다. 이 데이터 구조는 디버그 엔진 (DE)에 전달 하는 세 인수 중 하나는 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 식을 계산 하는 방법입니다. 이 인터페이스는 일반적으로 기호 공급자에 의해 구현 됩니다.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     에 [바인딩할](../../extensibility/debugger/reference/idebugbinder-bind.md) 메서드 기호의 현재 값을 포함 하는 메모리 영역을 가져옵니다. 모두 포함 하는 메서드를 나타내는 지정는 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 개체 및 나타내는 기호 자체를 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 개체 `IDebugBinder::Bind` 기호의 값을 반환 합니다. `IDebugBinder` DE에서 일반적으로 구현 됩니다.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     단순 데이터 형식을 나타냅니다. 배열 및 메서드를 같은 더 복잡 한 형식을 사용 하 여 파생 [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) 하 고 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 인터페이스를 각각. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 메서드 또는 클래스와 같은 다른 기호를 포함 하는 기호를 나타내는 또 다른 중요 한 파생된 인터페이스입니다. `IDebugField` 기호 공급자 인터페이스 (및 그 파생물) 일반적으로 구현 됩니다.

     `IDebugField` 이름과 기호의 형식을 찾으려고 사용을와 함께 개체 수를 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 개체, 해당 값을 찾는 데 사용할 수 있습니다.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     기호의 실행 시간 값의 실제 비트를 나타냅니다. [바인딩할](../../extensibility/debugger/reference/idebugbinder-bind.md) 사용을 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 기호를 나타내는 반환 하는 개체는 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 개체입니다. 합니다 [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) 메서드는 메모리 버퍼에 기호의 값을 반환 합니다. 일반적으로 DE 메모리의 속성 값을 표시 하려면이 인터페이스를 구현 합니다.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     이 인터페이스는 자체 식 계산기를 나타냅니다. 핵심 메서드는 [구문 분석](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)를 반환 하는 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 인터페이스입니다.

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     이 인터페이스에는 계산할 준비가 구문 분석 된 식을 나타냅니다. 핵심 메서드는 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 값 및 식의 형식을 나타내는 IDebugProperty2 반환 합니다.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     이 인터페이스는 값 및 콘텐츠 형식을 나타내는 및 식 평가의 결과입니다.

## <a name="see-also"></a>참고자료
- [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md)