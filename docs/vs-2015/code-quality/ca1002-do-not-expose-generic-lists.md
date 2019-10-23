---
title: 'CA1002: 제네릭 목록을 노출 하지 않음 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2a1d8ea70ca86cbb2f38afff48fe37b414b70e88
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646311"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: 제네릭 목록을 노출하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 형식에 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 형식인 외부에서 볼 수 있는 멤버가 포함 되어 있거나, <xref:System.Collections.Generic.List%601?displayProperty=fullName> 형식을 반환 하거나, 시그니처에 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 매개 변수가 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.Collections.Generic.List%601?displayProperty=fullName>는 상속 및 상속을 위해 디자인 된 제네릭 컬렉션입니다. <xref:System.Collections.Generic.List%601?displayProperty=fullName>에는 상속 된 클래스의 동작을 보다 쉽게 변경할 수 있도록 하는 가상 멤버가 포함 되어 있지 않습니다. 다음 제네릭 컬렉션은 상속을 위해 디자인 되었으며 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 대신 노출 되어야 합니다.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 형식을 상속을 위해 디자인 된 제네릭 컬렉션 중 하나로 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 경고를 발생 시키는 어셈블리가 재사용 가능한 라이브러리가 아닌 경우에만이 규칙에서 경고를 표시 하지 마십시오. 예를 들어, 제네릭 목록을 사용 하 여 성능을 향상 시킬 수 있는 성능 조정 된 응용 프로그램에서는이 경고를 표시 하는 것이 안전 합니다.

## <a name="related-rules"></a>관련 규칙
 [CA1005: 제네릭 형식의 매개 변수를 과도 하 게 사용 하지 않습니다 ](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: 컬렉션은 제네릭 인터페이스를 구현 해야 ](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: 정적 멤버를 제네릭 형식으로 선언 하지 마세요 ](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: 멤버 시그니처에 제네릭 형식을 중첩 하지 마세요 ](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: 제네릭 메서드는 형식 매개 변수를 제공 해야 ](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 제네릭 이벤트 처리기 인스턴스를 사용 ](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 적절 한 ](../code-quality/ca1007-use-generics-where-appropriate.md) 제네릭을 사용 합니다.

## <a name="see-also"></a>관련 항목:
 [제네릭](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
