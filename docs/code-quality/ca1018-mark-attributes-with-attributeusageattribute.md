---
title: 'CA1018: AttributeUsageAttribute로 특성을 표시하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 82a1ed8610ce84279f5fde3b802d976a3e766d99
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236245"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: AttributeUsageAttribute로 특성을 표시하세요.

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|범주|Microsoft.Design|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인
사용자 지정 특성에 특성이없습니다.<xref:System.AttributeUsageAttribute?displayProperty=fullName>

## <a name="rule-description"></a>규칙 설명
사용자 지정 특성을 정의 하는 경우를 사용 <xref:System.AttributeUsageAttribute> 하 여 해당 특성을 표시 하 여 소스 코드에서 사용자 지정 특성을 적용할 수 있는 위치를 지정 합니다. 특성의 의미 및 용도에 따라 코드에서의 유효한 위치가 결정됩니다. 예를 들어 라이브러리에서 각 형식을 유지 관리 하 고 개선할 책임이 있는 사용자를 식별 하는 특성을 정의할 수 있으며 해당 책임은 항상 형식 수준에서 할당 됩니다. 이 경우 컴파일러는 클래스, 열거형 및 인터페이스에서 특성을 사용 하도록 설정 해야 하지만 메서드, 이벤트 또는 속성에 대해 사용 하도록 설정 하면 안 됩니다. 조직 정책 및 절차에서는 어셈블리에 대 한 특성을 사용할지 여부를 결정 합니다.

열거형 <xref:System.AttributeTargets?displayProperty=fullName> 은 사용자 지정 특성에 대해 지정할 수 있는 대상을 정의 합니다. 를 생략 <xref:System.AttributeUsageAttribute>하면 사용자 지정 특성은 <xref:System.AttributeTargets> 열거형 `All` 값에 정의 된 모든 대상에 대해 유효 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면를 사용 <xref:System.AttributeUsageAttribute>하 여 특성의 대상을 지정 합니다. 다음 예제를 참조하세요.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
메시지를 제외 하는 대신이 규칙 위반 문제를 해결 해야 합니다. 특성이 상속 <xref:System.AttributeUsageAttribute>된 경우에도 특성은 코드 유지 관리를 간소화 하기 위해 제공 되어야 합니다.

## <a name="example"></a>예제
다음 예제에서는 두 개의 특성을 정의 합니다. `BadCodeMaintainerAttribute`<xref:System.AttributeUsageAttribute> 문을 잘못 생략 하 고 `GoodCodeMaintainerAttribute` 이 섹션의 앞부분에서 설명한 특성을 올바르게 구현 합니다. 속성 `DeveloperName` 은 CA1019 디자인 규칙 [에 필요 합니다. 특성 인수](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) 에 대 한 접근자를 정의 하며 완전성을 위해 포함 됩니다.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>관련 규칙
[CA1019: 특성 인수의 접근자를 정의 합니다.](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

[CA1813: 봉인 되지 않은 특성 방지](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>참고 항목

- [특성](/dotnet/standard/design-guidelines/attributes)