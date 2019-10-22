---
title: 'CA1038: 열거자는 강력한 형식 이어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c3a08f4987fe57a94aaee8f3df6129782fd6448c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661760"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: 열거자는 강력한 형식이어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식이 <xref:System.Collections.IEnumerator?displayProperty=fullName>를 구현 하지만 <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> 속성의 강력한 형식의 버전을 제공 하지 않습니다. 다음 형식에서 파생 된 형식은이 규칙에서 제외 됩니다.

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>규칙 설명
 이 규칙에서는 사용자가 인터페이스에서 제공 하는 기능을 사용할 때 반환 값을 강력한 형식으로 캐스팅할 필요가 없도록 <xref:System.Collections.IEnumerator> 구현이 <xref:System.Collections.IEnumerator.Current%2A> 속성의 강력한 형식의 버전을 제공 해야 합니다. 이 규칙에서는 <xref:System.Collections.IEnumerator>을 구현 하는 형식에 <xref:System.Object> 보다 강력한 형식의 인스턴스 컬렉션이 포함 되어 있다고 가정 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 인터페이스 속성을 명시적으로 구현 합니다 (`IEnumerator.Current`로 선언). @No__t_0으로 선언 되 고 강력한 형식의 개체를 반환 하도록 하는 강력한 형식의 공용 속성 버전을 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이진 트리와 같은 개체 기반 컬렉션에서 사용할 개체 기반 열거자를 구현할 때이 규칙의 경고를 표시 하지 않습니다. 새 컬렉션을 확장 하는 형식은 강력한 형식의 열거자를 정의 하 고 강력한 형식의 속성을 노출 합니다.

## <a name="example"></a>예제
 다음 예제에서는 강력한 형식의 <xref:System.Collections.IEnumerator> 형식을 구현 하는 올바른 방법을 보여 줍니다.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1035: ICollection 구현에 강력한 형식의 멤버가 있습니다.](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: 목록은 강력한 형식이어야 합니다.](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>관련 항목:
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
