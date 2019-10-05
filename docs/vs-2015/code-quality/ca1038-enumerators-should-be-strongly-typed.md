---
title: 'CA1038: 열거자는 강력한 형식 이어야 합니다 | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 84b6ae6ef0c63870ad9dc593fd0cf2e166e65397
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62559842"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: 열거자는 강력한 형식이어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식이 구현 <xref:System.Collections.IEnumerator?displayProperty=fullName> 하지만의 강력한 형식된 버전을 제공 하지 않습니다는 <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> 속성입니다. 다음 유형에 서 파생 된 형식은 다음과 같습니다.이 규칙에서 제외

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>규칙 설명
 이 규칙에서는 요구 <xref:System.Collections.IEnumerator> 구현도의 강력한 형식된 버전을 제공할는 <xref:System.Collections.IEnumerator.Current%2A> 속성 사용자 인터페이스에 의해 제공 되는 기능을 사용할 때 반환 값을 강력한 형식으로 캐스팅 하지 않아도 됩니다 있도록 합니다. 이 규칙에서는 구현 하는 형식이 가정 <xref:System.Collections.IEnumerator> 보다 강력한 형식의 인스턴스 컬렉션을 포함 <xref:System.Object>합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 인터페이스 속성을 명시적으로 구현 (로 선언 `IEnumerator.Current`). 로 선언 된 속성의 강력한 형식의 공용 버전 추가 `Current`, 고 강력한 형식의 개체를 반환 하도록 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이진 트리 같은 개체 기반 컬렉션을 사용 하는 개체 기반 열거자를 구현 하는 경우이 규칙에서 경고를 표시 합니다. 새 컬렉션을 확장 하는 강력한 형식의 열거자를 정의 하 고 강력한 형식의 속성을 노출 합니다.

## <a name="example"></a>예제
 다음 예제에서는 강력한 형식의 구현 하는 올바른 방법은 <xref:System.Collections.IEnumerator> 형식입니다.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1035: ICollection 구현에 강력한 형식의 멤버가](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: 목록은 강력한 형식](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>참고 항목
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
