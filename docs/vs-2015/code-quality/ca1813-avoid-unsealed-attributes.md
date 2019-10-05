---
title: 'CA1813: 봉인 되지 않은 특성 방지 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0624ff6ed890b6f0c14f3a03fe774c422334737d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690287"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: 봉인되지 않은 특성을 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|범주|Microsoft.Performance|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 공용 형식에서 상속 <xref:System.Attribute?displayProperty=fullName>추상 클래스가 아니며 봉인 (`NotInheritable` Visual basic에서).

## <a name="rule-description"></a>규칙 설명
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 클래스 라이브러리는 사용자 지정 특성을 검색하는 메서드를 제공합니다. 기본적으로 이러한 메서드는 특성 상속 계층 구조를 검색 예를 들어 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> 지정 된 특성 유형 또는 지정된 된 특성 형식이 확장 하는 모든 특성 형식 검색 합니다. 특성을 봉인 상속 계층을 통해 검색을 제거 하 고 성능을 향상 시킬 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하 고, 특성 형식을 봉인 또는 추상 확인 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 경고를 표시 하지 않아도 안전 합니다. 특성 계층을 정의 하는 및 특성을 봉인할 수 없거나 abstract로 만들 경우에 이렇게 해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 충족 하는 사용자 지정 특성을 보여 줍니다.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1019: 특성 인수의 접근자를 정의 합니다.](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: 특성을 attributeusageattribute로 표시](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>참고 항목
 [특성](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
