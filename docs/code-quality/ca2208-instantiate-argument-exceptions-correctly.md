---
title: 'CA2208: 인수 예외를 올바르게 인스턴스화하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9f9425ab1ea9eadd3bd06d950118ce83ba5c35f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231638"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: 인수 예외를 올바르게 인스턴스화하세요.

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|범주|Microsoft.Usage|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

가능한 원인은 다음과 같습니다.

- 또는에서 <xref:System.ArgumentException>파생 된 예외 형식의 기본 (매개 변수가 없는) 생성자를 호출 합니다.

- 잘못 된 문자열 인수가 이거나, <xref:System.ArgumentException>에서 파생 된 예외 형식의 매개 변수가 있는 생성자에 전달 된 경우

## <a name="rule-description"></a>규칙 설명

기본 생성자를 호출 하는 대신 보다 의미 있는 예외 메시지를 제공할 수 있도록 하는 생성자 오버 로드 중 하나를 호출 합니다. 예외 메시지는 개발자를 대상으로 하며 오류 조건 및 예외를 해결 하거나 방지 하는 방법을 명확 하 게 설명 해야 합니다.

및의 <xref:System.ArgumentException> 두 문자열 생성자와 해당 파생 형식에 대 한 서명은 위치 `message` 및 `paramName` 매개 변수와는 일치 하지 않습니다. 올바른 문자열 인수를 사용 하 여 이러한 생성자가 호출 되었는지 확인 합니다. 시그니처는 다음과 같습니다.

- <xref:System.ArgumentException>(문자열 `message`)
- <xref:System.ArgumentException>(string `message`, string `paramName`)
- <xref:System.ArgumentNullException>(문자열 `paramName`)
- <xref:System.ArgumentNullException>(string `paramName`, string `message`)
- <xref:System.ArgumentOutOfRangeException>(문자열 `paramName`)
- <xref:System.ArgumentOutOfRangeException>(string `paramName`, string `message`)
- <xref:System.DuplicateWaitObjectException>(문자열 `parameterName`)
- <xref:System.DuplicateWaitObjectException>(string `parameterName`, string `message`)

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 메시지, 매개 변수 이름 또는 두 가지를 모두 사용 하는 생성자를 호출 하 고 인수가 호출 되는의 <xref:System.ArgumentException> 형식에 적합 한지 확인 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

올바른 문자열 인수를 사용 하 여 매개 변수가 있는 생성자를 호출 하는 경우에만이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예제

다음 코드에서는의 <xref:System.ArgumentNullException>인스턴스를 잘못 인스턴스화하는 생성자를 보여 줍니다.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

다음 코드는 생성자 인수를 전환 하 여 이전 위반을 수정 합니다.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>관련 규칙

- [CA1507: 문자열 대신 nameof 사용](ca1507.md)