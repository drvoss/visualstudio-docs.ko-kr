---
title: 'CA1800: 불필요하게 캐스트하지 마세요.'
ms.date: 10/26/2017
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 85d168e97f422a3965096a334cb2a448406604f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233837"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: 불필요하게 캐스트하지 마세요.

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|범주|Microsoft.Performance|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인
메서드는 해당 인수 또는 지역 변수 중 하나에 대해 중복 캐스트를 수행 합니다.

이 규칙에의 한 전체 분석을 수행 하려면 디버깅 정보를 사용 하 여 테스트 된 어셈블리를 빌드해야 하며 연결 된 프로그램 데이터베이스 (.pdb) 파일을 사용할 수 있어야 합니다.

## <a name="rule-description"></a>규칙 설명
중복 캐스팅을 수행하면 성능이 저하됩니다. 특히 간단한 반복 문에서 캐스팅이 수행될 때 더욱 그러합니다. 명시적 중복 캐스트 작업의 경우 캐스트 결과를 지역 변수에 저장 하 고 중복 캐스트 작업 대신 지역 변수를 사용 합니다.

연산자를 사용 하 여 실제 캐스트를 수행 하기 전에 캐스팅이 성공할 지 여부를 테스트 하는 경우에는 `as` 연산자의 결과를 테스트 하는 것이 좋습니다. C# `is` 이는 `is` 연산자가 수행 하는 암시적 캐스트 연산 없이 동일한 기능을 제공 합니다. 또는 C# 7.0 이상에서는 [패턴 일치](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) 를 사용 하 `is` 여 연산자를 사용 하 여 형식 변환을 확인 하 고 식을 한 단계에서 해당 형식의 변수로 캐스트 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 캐스트 작업 수를 최소화 하도록 메서드 구현을 수정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
성능이 중요 하지 않은 경우이 규칙에서 경고를 표시 하지 않거나 규칙을 완전히 무시 해도 안전 합니다.

## <a name="examples"></a>예
다음 예제에서는 C# `is` 연산자를 사용 하 여 규칙을 위반 하는 메서드를 보여 줍니다. 두 번째 메서드는 연산자 `is` `as` 의 결과에 대 한 테스트를 사용 하 여 연산자의 결과에 대 한 테스트로 연산자를 대체 하 여 규칙을 충족 시킵니다. 세 번째 메서드는 형식 변환에 성공 하 `is` 는 경우 [패턴 일치](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) 를 사용 하 여 원하는 형식의 변수를 만드는 방법으로 규칙을 충족 하기도 합니다.

[!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

다음 예제에서는 규칙을 위반 하 `start_Click`는 중복 된 명시적 캐스팅이 여러 개 있고 지역 변수에 캐스트를 저장 하 여 규칙을 `reset_Click`충족 하는 메서드를 여러 개 포함 하는 메서드를 보여 줍니다.

[!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
[!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>참고 항목

- [as (C# 참조)](/dotnet/csharp/language-reference/keywords/as)
- [is (C# 참조)](/dotnet/csharp/language-reference/keywords/is)