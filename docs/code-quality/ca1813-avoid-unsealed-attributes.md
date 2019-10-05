---
title: 'CA1813: 봉인되지 않은 특성을 사용하지 마세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 12371c34c846991a0ec41f5e9d9588c5bde8e4d6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233591"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: 봉인되지 않은 특성을 사용하지 마세요.

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|범주|Microsoft.Performance|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인

공용 형식이에서 <xref:System.Attribute?displayProperty=fullName>상속 되 고,가 abstract가 아니고, Visual Basic`NotInheritable` 에서 봉인 되지 않습니다.

## <a name="rule-description"></a>규칙 설명

.NET에서는 사용자 지정 특성을 검색 하는 메서드를 제공 합니다. 기본적으로 이러한 메서드는 특성 상속 계층을 검색합니다. 예를 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> 들어는 지정 된 특성 유형 또는 지정 된 특성 유형을 확장 하는 특성 유형을 검색 합니다. 특성을 봉인 하면 상속 계층 구조를 통해 검색이 제거 되 고 성능이 향상 될 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 특성 유형을 봉인 하거나 abstract로 설정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

이 규칙에서는 경고를 표시 하지 않는 것이 안전 합니다. 특성 계층을 정의 하 고 특성을 봉인 하거나 abstract로 설정할 수 없는 경우에만를 표시 하지 않습니다.

## <a name="example"></a>예제

다음 예제에서는이 규칙을 충족 하는 사용자 지정 특성을 보여 줍니다.

[!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
[!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>관련 규칙

- [CA1019: 특성 인수의 접근자를 정의 합니다.](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)
- [CA1018: AttributeUsageAttribute를 사용 하 여 특성 표시](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>참고 항목

- [특성](/dotnet/standard/design-guidelines/attributes)