---
title: 'CA1035: ICollection 구현에 강력한 형식의 멤버가 있습니다.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d9e74daa464a55a543b5eb8c189c9ddf1295301
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236020"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: ICollection 구현에 강력한 형식의 멤버가 있습니다.

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|범주|Microsoft.Design|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인
공용 또는 보호 된 형식이를 <xref:System.Collections.ICollection?displayProperty=fullName> 구현 하지만에 <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>강력한 형식의 메서드를 제공 하지 않습니다. 강력한 형식의 버전 <xref:System.Collections.ICollection.CopyTo%2A> 은 두 개의 매개 변수를 허용 해야 하며 <xref:System.Array?displayProperty=fullName> 또는 배열을 <xref:System.Object?displayProperty=fullName> 첫 번째 매개 변수로 사용할 수 없습니다.

## <a name="rule-description"></a>규칙 설명
이 규칙에서는 <xref:System.Collections.ICollection> 사용자가 인터페이스에서 제공 하는 기능을 사용할 때 <xref:System.Object> 형식으로 인수를 캐스팅할 필요가 없도록 강력한 형식의 멤버를 제공 하기 위한 구현이 필요 합니다. 이 규칙에서는을 구현 <xref:System.Collections.ICollection> 하는 형식에서 보다 <xref:System.Object>강력한 형식의 인스턴스 컬렉션을 관리 하는 것으로 가정 합니다.

 <xref:System.Collections.ICollection>는 <xref:System.Collections.IEnumerable?displayProperty=fullName> 인터페이스를 구현합니다. 컬렉션의 개체가 확장 <xref:System.ValueType?displayProperty=fullName>된 경우에는에 대 한 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 강력한 형식의 멤버를 제공 하 여 boxing으로 인해 발생 하는 성능 저하를 방지 해야 합니다. 컬렉션의 개체가 참조 형식일 경우에는 필요 하지 않습니다.

강력한 형식의 인터페이스 멤버를 구현 하려면 형식의 이름을 `InterfaceName.InterfaceMemberName`사용 하 여 ( <xref:System.Collections.ICollection.CopyTo%2A>예:) 인터페이스 멤버를 명시적으로 구현 합니다. 명시적 인터페이스 멤버는 인터페이스에서 선언 된 데이터 형식을 사용 합니다. 인터페이스 멤버 이름 (예: <xref:System.Collections.ICollection.CopyTo%2A>)을 사용 하 여 강력한 형식의 멤버를 구현 합니다. 강력한 형식의 멤버를 public으로 선언 하 고, 매개 변수 및 반환 값을 컬렉션에서 관리 되는 강력한 형식으로 선언 합니다. 강력한 형식은 인터페이스에 의해 선언 된 및 <xref:System.Object> <xref:System.Array> 와 같은 약한 형식을 대체 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 인터페이스 멤버를 명시적으로 구현 합니다 (로 <xref:System.Collections.ICollection.CopyTo%2A>선언). 로 `CopyTo`선언 된 공용 강력한 형식의 멤버를 추가 하 고 강력한 형식의 배열을 첫 번째 매개 변수로 사용 하도록 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
새 컬렉션을 확장 하는 형식에서 강력한 형식을 결정 하는 이진 트리와 같은 새 개체 기반 컬렉션을 구현 하는 경우에는이 규칙에서 경고를 표시 하지 않습니다. 이러한 형식은이 규칙을 준수 하 고 강력한 형식의 멤버를 노출 해야 합니다.

## <a name="example"></a>예제
다음 예제에서는를 구현 <xref:System.Collections.ICollection>하는 올바른 방법을 보여 줍니다.

[!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>관련 규칙
[CA1038: 열거자는 강력한 형식 이어야 합니다.](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

[CA1039: 목록은 강력한 형식입니다.](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>참고 항목

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>