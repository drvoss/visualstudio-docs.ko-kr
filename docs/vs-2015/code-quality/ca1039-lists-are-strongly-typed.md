---
title: 'CA1039: 목록은 강력한 형식 | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3fb1a6255539ded989c5ad9638fc961d606a19f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62559751"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: 목록은 강력한 형식이어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식 구현 <xref:System.Collections.IList?displayProperty=fullName> 하지만 다음 중 하나 이상에 대해 강력한 형식의 메서드를 제공 하지 않습니다.

- IList.Item

- IList.Add

- IList.Contains

- IList.IndexOf

- IList.Insert

- IList.Remove

## <a name="rule-description"></a>규칙 설명
 이 규칙에 필요 <xref:System.Collections.IList> 사용자는 인수를 캐스팅할 필요가 없도록 강력 하 게 제공 하는 구현 형식의 멤버가 <xref:System.Object?displayProperty=fullName> 인터페이스에 의해 제공 되는 기능을 사용할 때를 입력 합니다. <xref:System.Collections.IList> 인터페이스는 인덱스로 액세스할 수 있는 개체의 컬렉션에 의해 구현 됩니다. 이 규칙에서는 구현 하는 형식이 가정 <xref:System.Collections.IList> 보다 강력한 형식의 인스턴스 컬렉션을 관리 하는 <xref:System.Object>합니다.

 <xref:System.Collections.IList> 구현 된 <xref:System.Collections.ICollection?displayProperty=fullName> 고 <xref:System.Collections.IEnumerable?displayProperty=fullName> 인터페이스입니다. 구현 하는 경우 <xref:System.Collections.IList>에 대 한 강력한 형식의 필수 멤버를 제공 해야 <xref:System.Collections.ICollection>합니다. 컬렉션의 개체를 확장 하는 경우 <xref:System.ValueType?displayProperty=fullName>에 대 한 강력한 형식의 멤버를 제공 해야 합니다 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 성능 저하를 방지 하려면 boxing 시킨; 컬렉션의 개체 참조 형식인 경우 필요 하지 않습니다.

 이 규칙을 준수 하는 인터페이스 멤버를 명시적으로 구현 같은 InterfaceName.InterfaceMemberName, 형식에서 이름을 사용 하 여 <xref:System.Collections.IList.Add%2A>입니다. 인터페이스에서 선언 된 데이터 형식을 사용 하는 명시적 인터페이스 멤버입니다. 같은 인터페이스 멤버 이름을 사용 하 여 강력한 형식의 멤버를 구현 `Add`합니다. 공용으로 강력한 형식의 멤버를 선언 및 매개 변수를 선언 하 고 컬렉션에 의해 관리 되는 강력한 형식의 값을 반환 합니다. 강력한 형식 보다 약한 종류를 같은 대체 <xref:System.Object> 고 <xref:System.Array> 인터페이스에서 선언 된 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 명시적으로 구현 <xref:System.Collections.IList> 멤버 앞에서 언급 된 멤버에 대 한 강력한 형식의 대안을 제공 합니다. 올바르게 구현 하는 코드에 대 한는 <xref:System.Collections.IList> 인터페이스 정보와 필요한 강력한 형식의 멤버를 다음 예제를 참조 하세요.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 새 컬렉션을 확장 하는 형식이 강력한 형식을 결정 하는 위치에 연결된 된 목록 같은 새 개체 기반 컬렉션을 구현 하는 경우이 규칙에서 경고를 표시 합니다. 이러한 형식은이 규칙을 준수 하 고 강력한 형식의 멤버를 노출 해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 형식에서에서 `YourType` 확장 <xref:System.Collections.CollectionBase?displayProperty=fullName>처럼 모든 강력한 형식의 컬렉션을 해야 합니다. 사실은 <xref:System.Collections.CollectionBase> 의 명시적 구현을 제공 합니다 <xref:System.Collections.IList> 인터페이스를 합니다. 따라서 강력한 형식의 멤버에만 제공 해야 합니다 <xref:System.Collections.IList> 고 <xref:System.Collections.ICollection>입니다.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1035: ICollection 구현에 강력한 형식의 멤버가](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: 열거자는 강력한 형식 이어야 합니다.](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>참고 항목
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
