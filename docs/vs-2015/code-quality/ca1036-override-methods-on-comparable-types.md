---
title: 'CA1036: 비교 가능한 형식에 메서드를 재정의 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 49a4e64767497e4a1098bda9f5ee4e0eec8151f5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65682809"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: 비교 가능한 형식에 메서드를 재정의하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|범주|Microsoft.Design|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 Public 또는 protected 형식이 구현 하는 <xref:System.IComparable?displayProperty=fullName> 인터페이스를 재정의 하지 않습니다 <xref:System.Object.Equals%2A?displayProperty=fullName> 또는 같음, 같지 않음, 보다 작음 또는 보다 큰에 대 한 언어별 연산자를 오버 로드 하지 않습니다. 인터페이스의 구현을 상속 하는 경우 규칙 위반을 보고 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 사용자 지정 정렬 순서를 정의 하는 형식을 구현 합니다 <xref:System.IComparable> 인터페이스입니다. <xref:System.IComparable.CompareTo%2A> 메서드 형식의 두 인스턴스에 대 한 적절 한 정렬 순서를 나타내는 정수 값을 반환 합니다. 이 규칙을 정렬 순서를 설정 하는 형식을 식별합니다 즉,이 일반적인 의미를 같음, 같지 않음, 보다 작거나 보다 큰 적용 되지 않습니다. 구현을 제공 하는 경우 <xref:System.IComparable>, 일반적으로 수행 해야 재정의할 수도 <xref:System.Object.Equals%2A> 와 일치 하는 값을 반환할 수 있도록 <xref:System.IComparable.CompareTo%2A>입니다. 재정의 하는 경우 <xref:System.Object.Equals%2A> 코딩 및 연산자 오버 로드를 지 원하는 언어로 일관 된 연산자를 제공 해야 <xref:System.Object.Equals%2A>합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 재정의 <xref:System.Object.Equals%2A>합니다. 프로그래밍 언어가 연산자 오버 로드를 지 원하는 경우에 다음 연산자를 제공 합니다.

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  C#에서는 이러한 연산자를 나타내는 데 사용 되는 토큰은 다음과 같습니다: = =,! =, \<, 및 >입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 누락 된 연산자로 위반이 발생 하며 Visual Basic.NET을 사용한 경우 처럼 프로그래밍 언어가 연산자 오버 로드를 지원 하지 않습니다 하는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다. Op_Equality 연산자를 구현 하는 경우 이해 되지 않는 응용 프로그램 컨텍스트에서 이외의 같음 연산자에서 발생 하면이 규칙에서 경고를 표시 하지 않아도 안전 이기도 합니다. 그러나 해야 항상 op_Equality 통해 및 Object.Equals를 재정의 하는 경우 = = 연산자입니다.

## <a name="example"></a>예제
 다음 예제에서는 올바르게 구현 하는 형식을 포함 <xref:System.IComparable>합니다. 관련 된 다양 한 규칙을 충족 하는 메서드를 식별 하는 코드 주석을 <xref:System.Object.Equals%2A> 하며 <xref:System.IComparable> 인터페이스입니다.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>예제
 다음 응용 프로그램의 동작을 테스트 합니다 <xref:System.IComparable> 앞에 나온를 구현 합니다.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [같음 연산자](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
