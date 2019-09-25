---
title: 'CA2224: 같음 연산자를 오버로드할 때 Equals를 재정의하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 72bcf01b9c0613bb390ac9adbbba2fb176db13bd
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231211"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: 같음 연산자를 오버로드할 때 Equals를 재정의하세요.

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|범주|Microsoft.Usage|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

Public 형식은 같음 연산자를 구현 하지만는 재정의 <xref:System.Object.Equals%2A?displayProperty=fullName>하지 않습니다.

## <a name="rule-description"></a>규칙 설명

같음 연산자는 구문상 편리 하 게 <xref:System.Object.Equals%2A> 메서드 기능에 액세스 하는 방법입니다. 같음 연산자를 구현 하는 경우 해당 논리는의 <xref:System.Object.Equals%2A>해당 논리와 동일 해야 합니다.

코드가 C# 이 규칙을 위반 하는 경우 컴파일러에서 경고를 발생 시킵니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 같음 연산자의 구현을 제거 하거나를 재정의 <xref:System.Object.Equals%2A> 하 고 두 메서드가 같은 값을 반환 하도록 해야 합니다. 같음 연산자에서 일관 되지 않은 동작이 발생 하지 않는 경우 기본 클래스의 메서드를 <xref:System.Object.Equals%2A> <xref:System.Object.Equals%2A> 호출 하는의 구현을 제공 하 여 위반을 해결할 수 있습니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

같음 연산자가의 <xref:System.Object.Equals%2A>상속 된 구현과 동일한 값을 반환 하는 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다. 이 문서의 예제에는이 규칙에서 경고를 안전 하 게 표시 하지 않을 수 있는 형식이 포함 되어 있습니다.

## <a name="examples-of-inconsistent-equality-definitions"></a>일치 하지 않는 같음 정의의 예

다음 예제에서는 일치 하는 정의가 일치 하지 않는 형식을 보여 줍니다. `BadPoint`같음 연산자의 사용자 지정 구현을 제공 하 여 같음의 의미를 변경 하지만 동일 하 게 동작 <xref:System.Object.Equals%2A> 하도록를 재정의 하지는 않습니다.

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

다음 코드에서는의 `BadPoint`동작을 테스트 합니다.

[!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

이 예제는 다음과 같은 출력을 생성합니다.

```txt
a =  ([0] 1,1) and b = ([1] 2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? No
b == bcopy ? Yes
```

다음 예제에서는 기술적으로이 규칙을 위반 하지만 일관 되지 않은 방식으로 동작 하지 않는 형식을 보여 줍니다.

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

다음 코드에서는의 `GoodPoint`동작을 테스트 합니다.

[!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

이 예제는 다음과 같은 출력을 생성합니다.

```txt
a =  (1,1) and b = (2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? Yes
b == bcopy ? Yes
```

## <a name="class-example"></a>클래스 예제

다음 예제에서는이 규칙을 위반 하는 클래스 (참조 형식)를 보여 줍니다.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

다음 예에서는를 재정의 <xref:System.Object.Equals%2A?displayProperty=fullName>하 여 위반을 수정 합니다.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>구조 예제

다음 예제에서는이 규칙을 위반 하는 구조체 (값 형식)를 보여 줍니다.

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

다음 예에서는를 재정의 <xref:System.ValueType.Equals%2A?displayProperty=fullName>하 여 위반을 수정 합니다.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>관련 규칙

[CA1046: 참조 형식에 같음 연산자를 오버 로드 하지 마십시오.](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: 연산자 오버 로드에는 대체 이름이 있습니다.](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: 연산자에는 대칭 오버 로드가 있어야 합니다.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218: Equals를 재정의할 때 GetHashCode 재정의](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231: ValueType.Equals를 재정의할 때 같음 연산자를 오버로드하십시오.](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)