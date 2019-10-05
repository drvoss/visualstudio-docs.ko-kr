---
title: 식 계산 컨텍스트 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efaa678b5cbee763fabc9ccaf82c9322176b9102
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315235"
---
# <a name="expression-evaluation-context"></a>식 계산 컨텍스트
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버깅 하는 **식 계산 컨텍스트**:

- 식 계산에 대 한 컨텍스트를 나타냅니다. 일반적으로 평가 컨텍스트 변수, 매개 변수, 함수 및 메서드를 평가 하는 어휘 범위에 해당 합니다. 예를 들어, 스택 프레임을 사용 하 여 연결 하는 식 계산 컨텍스트는 해당 하는 경우 로컬 변수, 메서드 매개 변수 및 클래스 멤버를 평가 하는 것에 대 한 컨텍스트를 제공 합니다.

- 중단점에서 프로그램을 중지 하는 경우 존재 합니다. 식 자체에 지정 된 컨텍스트 내에서 평가 위한 준비 된 구문 분석 된 식을 나타내는 데이터 구조입니다.

     보다 세부적으로 식을 사용 하 여 만들어집니다 합니다 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드. 식을 계산할 때 이름 및 유형의 변수 또는 인수 및 해당 값을 포함 하는 인쇄 가능한 문자열을 생성 합니다. 조사식 창 또는 IDE의 지역 창에서이 문자열이 표시 됩니다.

     지정 된을 `BSTR` 및 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스는 디버그 엔진 (DE)를 만들 수는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 식을 구문 분석 하 여 인터페이스입니다. 지정 된 `IDebugExpression2` 인터페이스는 DE 동기 또는 비동기 식 평가 통해 값을 가져올 수 있습니다. 이름 및 형식의 변수 또는 인수를 함께이 값을 표시 하기 위해 IDE에 전송 됩니다.

## <a name="see-also"></a>참고자료
- [식 계산 인터페이스](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)