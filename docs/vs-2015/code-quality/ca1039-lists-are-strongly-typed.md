---
title: 'CA1039: 목록은 강력한 형식입니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8845fb8bcd08f076ddc3c509a37948cf008e0623
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661809"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: 목록은 강력한 형식이어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식은 <xref:System.Collections.IList?displayProperty=fullName>를 구현 하지만 다음 중 하나 이상의 강력한 형식의 메서드를 제공 하지 않습니다.

- IList. 항목

- IList. 추가

- IList. Contains

- IList. IndexOf

- IList. Insert

- IList. 제거

## <a name="rule-description"></a>규칙 설명
 이 규칙에서는 사용자가 인터페이스에서 제공 하는 기능을 사용할 때 인수를 <xref:System.Object?displayProperty=fullName> 형식으로 캐스팅할 필요가 없도록 <xref:System.Collections.IList> 구현이 강력한 형식의 멤버를 제공 해야 합니다. @No__t_0 인터페이스는 인덱스에서 액세스할 수 있는 개체의 컬렉션에 의해 구현 됩니다. 이 규칙에서는 <xref:System.Collections.IList>을 구현 하는 형식에서 <xref:System.Object> 보다 강력한 형식의 인스턴스 컬렉션을 관리 하는 것으로 가정 합니다.

 <xref:System.Collections.IList> <xref:System.Collections.ICollection?displayProperty=fullName> 및 <xref:System.Collections.IEnumerable?displayProperty=fullName> 인터페이스를 구현 합니다. @No__t_0를 구현 하는 경우 <xref:System.Collections.ICollection>에 필요한 강력한 형식의 멤버를 제공 해야 합니다. 컬렉션의 개체가 <xref:System.ValueType?displayProperty=fullName> 확장 하는 경우 boxing으로 인해 발생 하는 성능 저하를 방지 하기 위해 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 강력한 형식의 멤버를 제공 해야 합니다. 컬렉션의 개체가 참조 형식일 경우에는 필요 하지 않습니다.

 이 규칙을 준수 하려면 <xref:System.Collections.IList.Add%2A>와 같이 InterfaceMemberName 형식의 이름을 사용 하 여 인터페이스 멤버를 명시적으로 구현 합니다. 명시적 인터페이스 멤버는 인터페이스에서 선언 된 데이터 형식을 사용 합니다. 인터페이스 멤버 이름 (예: `Add`)을 사용 하 여 강력한 형식의 멤버를 구현 합니다. 강력한 형식의 멤버를 public으로 선언 하 고, 매개 변수 및 반환 값을 컬렉션에서 관리 되는 강력한 형식으로 선언 합니다. 강력한 형식은 <xref:System.Object>와 같은 약한 형식이 나 인터페이스에서 선언 된 <xref:System.Array>를 대체 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 <xref:System.Collections.IList> 멤버를 명시적으로 구현 하 고 앞에서 언급 한 멤버에 대 한 강력한 형식의 대안을 제공 합니다. @No__t_0 인터페이스를 올바르게 구현 하 고 필요한 강력한 형식의 멤버를 제공 하는 코드의 경우 다음 예제를 참조 하세요.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 새 컬렉션을 확장 하는 형식에서 강력한 형식을 결정 하는 연결 된 목록과 같은 새 개체 기반 컬렉션을 구현 하는 경우에는이 규칙의 경고를 표시 하지 않습니다. 이러한 형식은이 규칙을 준수 하 고 강력한 형식의 멤버를 노출 해야 합니다.

## <a name="example"></a>예제
 다음 예제에서 형식은 강력한 형식의 모든 컬렉션을 `YourType` <xref:System.Collections.CollectionBase?displayProperty=fullName>를 확장 합니다. @No__t_0는 <xref:System.Collections.IList> 인터페이스의 명시적 구현을 제공 합니다. 따라서 <xref:System.Collections.IList> 및 <xref:System.Collections.ICollection>에 대해서만 강력한 형식의 멤버를 제공 해야 합니다.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>관련 규칙
 [CA1035: ICollection 구현에 강력한 형식의 멤버가 있습니다.](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: 열거자는 강력한 형식이어야 합니다.](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>관련 항목:
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
