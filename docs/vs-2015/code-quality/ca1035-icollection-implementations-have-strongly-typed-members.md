---
title: 'CA1035: ICollection 구현에 강력한 형식의 멤버가 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6eda1bc311c39d0ec1da9667ac078c22183e2bd0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62535751"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: ICollection 구현에 강력한 형식의 멤버가 있습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식이 구현 <xref:System.Collections.ICollection?displayProperty=fullName> 에 대 한 강력한 형식의 메서드를 제공 하지 않습니다 하지만 <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>합니다. 강력한 형식된 버전 <xref:System.Collections.ICollection.CopyTo%2A> 두 개의 매개 변수를 수락 해야 하 고 사용할 수 없습니다는 <xref:System.Array?displayProperty=fullName> 또는 배열을 <xref:System.Object?displayProperty=fullName> 첫 번째 매개 변수로 합니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙에 필요 <xref:System.Collections.ICollection> 사용자는 인수를 캐스팅할 필요가 없도록 강력 하 게 제공 하는 구현 형식의 멤버가 <xref:System.Object> 인터페이스에 의해 제공 되는 기능을 사용할 때를 입력 합니다. 이 규칙에서는 구현 하는 형식이 가정 <xref:System.Collections.ICollection> 는 보다 강력한 형식의 인스턴스 컬렉션을 관리 하도록 <xref:System.Object>합니다.

 <xref:System.Collections.ICollection>는 <xref:System.Collections.IEnumerable?displayProperty=fullName> 인터페이스를 구현합니다. 컬렉션의 개체를 확장 하는 경우 <xref:System.ValueType?displayProperty=fullName>에 대 한 강력한 형식의 멤버를 제공 해야 합니다 <xref:System.Collections.IEnumerable.GetEnumerator%2A> boxing 하 여 발생 하는 성능 저하를 방지 하려면. 이 컬렉션의 개체 참조 형식인 경우 필요 하지 않습니다.

 인터페이스 멤버의 강력한 형식된 버전을 구현 하려면 인터페이스 멤버를 명시적으로 구현 형식에서 이름을 사용 하 여 `InterfaceName.InterfaceMemberName`와 같은 <xref:System.Collections.ICollection.CopyTo%2A>합니다. 인터페이스에서 선언 된 데이터 형식을 사용 하는 명시적 인터페이스 멤버입니다. 같은 인터페이스 멤버 이름을 사용 하 여 강력한 형식의 멤버를 구현 <xref:System.Collections.ICollection.CopyTo%2A>합니다. 공용으로 강력한 형식의 멤버를 선언 및 매개 변수를 선언 하 고 컬렉션에 의해 관리 되는 강력한 형식의 값을 반환 합니다. 강력한 형식 보다 약한 종류를 같은 대체 <xref:System.Object> 고 <xref:System.Array> 인터페이스에서 선언 된 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 인터페이스 멤버를 명시적으로 구현 (로 선언 <xref:System.Collections.ICollection.CopyTo%2A>). 로 선언 된 강력한 형식의 공용 멤버를 추가 `CopyTo`, 강력한 형식의 배열을 첫 번째 매개 변수로 있습니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 같은 이진 트리는 새 컬렉션을 확장 하는 형식이 강력한 형식을 결정 하는 새 개체 기반 컬렉션을 구현 하는 경우이 규칙에서 경고를 표시 합니다. 이러한 형식은이 규칙을 준수 하 고 강력한 형식의 멤버를 노출 해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 구현 하는 올바른 방법은 <xref:System.Collections.ICollection>합니다.

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1038: 열거자는 강력한 형식 이어야 합니다.](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: 목록은 강력한 형식](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>참고 항목
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
