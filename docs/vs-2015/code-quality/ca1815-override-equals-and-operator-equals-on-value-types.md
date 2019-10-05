---
title: 'CA1815: Equals를 재정의 하 고 값 형식에서 equals 또는 같음 연산자 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e21585a7a56fde2fb46ea86adde92eecfd1a4565
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201689"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: 값 형식에서 Equals 또는 같음 연산자를 재정의하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|범주|Microsoft.Performance|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 공개 값 형식의 재정의 하지 않는 <xref:System.Object.Equals%2A?displayProperty=fullName>, 또는 같음 연산자 (= =) 구현 하지 않습니다. 이 규칙에서 열거형을 확인 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 값 형식, 상속 된 구현에 대 한 <xref:System.Object.Equals%2A> 리플렉션 라이브러리를 사용 하 고 모든 필드의 내용을 비교 합니다. Reflection에는 많은 계산이 요구되며 모든 필드의 일치 여부를 비교하는 것이 불필요할 수 있습니다. 비교 또는 정렬 인스턴스 수를 예상 하거나 해시 테이블 키로 사용 하는 경우에 값 형식 구현 해야 <xref:System.Object.Equals%2A>합니다. 프로그래밍 언어가 연산자 오버로드를 지원하는 경우 같음 및 같지 않음 연산자의 구현도 제공해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 구현을 제공할 <xref:System.Object.Equals%2A>합니다. 가능한 경우 같음 연산자를 구현 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 값 형식의 인스턴스를 서로 비교 하지 않을 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="example-of-a-violation"></a>위반의 예

### <a name="description"></a>Description
 다음 예제에서는이 규칙을 위반 하는 구조체 (값 형식)를 보여 줍니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>수정 하는 방법의 예

### <a name="description"></a>Description
 다음 예제에서는 재정의 하 여 위반을 해결 <xref:System.ValueType.Equals%2A?displayProperty=fullName> 및 같음 연산자를 구현 합니다. (= =,! =) 합니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA2224: 같음 연산자를 오버 로드할 때 equals 재정의](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: ValueType.Equals를 재정의할 때 같음 연산자를 오버로드하십시오.](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: 연산자에는 대칭 오버 로드가 있어야 합니다.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>참고 항목
 <xref:System.Object.Equals%2A?displayProperty=fullName>
