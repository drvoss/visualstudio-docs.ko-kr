---
title: 평가 컨텍스트에 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6a3d74c26b6ca94e0a4052df4810e407313a6cd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315499"
---
# <a name="evaluation-context"></a>평가 컨텍스트
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 에 전달 되 면 디버그 엔진 (DE) 식 계산기 (EE), 세 개의 인수를 호출 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 다음 표에 나와 있는 것 처럼 찾기 및 평가, 기호에 대 한 컨텍스트를 결정 합니다.

## <a name="arguments"></a>인수

|인수|설명|
|--------------|-----------------|
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) 기호를 식별 하는 데 사용할 기호 처리기 (SH)를 지정 하는 인터페이스입니다.|
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) 현재 실행 지점을 지정 하는 인터페이스입니다. 이 인터페이스는 실행 중인 코드를 포함 하는 메서드를 찾습니다.|
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 값과 이름이 지정 된 기호의 형식이 발견 하는 인터페이스입니다.|

 `IDebugParsedExpression::EvaluateSync` 반환 합니다는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 결과 값 및 해당 형식을 나타내는 인터페이스입니다.

## <a name="see-also"></a>참고자료
- [Key 식 계산기 인터페이스](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [로컬 항목 표시](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)