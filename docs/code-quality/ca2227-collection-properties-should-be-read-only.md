---
title: 'CA2227: 컬렉션 속성은 읽기 전용이어야 합니다.'
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 3d097a67c9a62a6847ff6ab0bb882257c082ca6f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231308"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: 컬렉션 속성은 읽기 전용이어야 합니다.

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|범주|Microsoft.Usage|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인

외부에서 볼 수 있는 쓰기 가능 속성은을 구현 <xref:System.Collections.ICollection?displayProperty=fullName>하는 형식입니다. 이 규칙은 배열, 인덱서 (이름이 ' Item ' 인 속성) 및 권한 집합을 무시 합니다.

## <a name="rule-description"></a>규칙 설명

쓰기 가능한 컬렉션 속성을 통해 사용자는 컬렉션을 완전히 다른 컬렉션으로 바꿀 수 있습니다. 읽기 전용 속성은 컬렉션을 대체 하는 것을 중지 하지만 여전히 개별 멤버를 설정할 수 있도록 합니다. 컬렉션을 대체 하는 것이 목표 인 경우 기본 디자인 패턴은 컬렉션에서 모든 요소를 제거 하는 메서드와 컬렉션을 다시 채우는 메서드를 포함 하는 것입니다. 이 패턴의 <xref:System.Collections.ArrayList.AddRange%2A> 예는 <xref:System.Collections.ArrayList?displayProperty=fullName> 클래스의 및메서드를참조하세요.<xref:System.Collections.ArrayList.Clear%2A>

이진 및 XML serialization은 모두 컬렉션인 읽기 전용 속성을 지원 합니다. 클래스 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 에는을 구현 <xref:System.Collections.ICollection> 하 고 <xref:System.Collections.IEnumerable?displayProperty=fullName> serialize 할 수 있도록 하는 형식에 대 한 특정 요구 사항이 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 속성을 읽기 전용으로 설정 합니다. 디자인에 필요한 경우 컬렉션을 지우고 다시 채우는 메서드를 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

속성이 [DTO (데이터 전송 Object)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) 클래스의 일부인 경우 경고를 표시 하지 않을 수 있습니다.

그렇지 않으면이 규칙에서 경고를 표시 하지 않습니다.

## <a name="example"></a>예제

다음 예제에서는 쓰기 가능한 컬렉션 속성이 있는 형식을 보여 주고 컬렉션을 직접 바꿀 수 있는 방법을 보여 줍니다. 또한 및 `Clear` `AddRange` 메서드를 사용 하 여 읽기 전용 컬렉션 속성을 대체 하는 기본 방법을 보여 줍니다.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>관련 규칙

- [CA1819: 속성은 배열을 반환 해서는 안 됩니다.](../code-quality/ca1819-properties-should-not-return-arrays.md)