---
title: 'CA1000: 정적 멤버를 제네릭 형식으로 선언 하지 마세요. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ef6c98c2808e639570b51d485df90bbdab72c43
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646357"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: 정적 멤버를 제네릭 형식으로 선언하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에 노출 되는 제네릭 형식에 `static` `Shared` (Visual Basic) 멤버가 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명
 제네릭 형식의 `static` 멤버를 호출 하는 경우 형식에 대해 형식 인수를 지정 해야 합니다. 유추를 지원하지 않는 제네릭 인스턴스 멤버를 호출할 때는 멤버에 형식 인수를 지정해야 합니다. 이러한 두 경우에 형식 인수를 지정 하는 구문은 서로 다르며 다음 호출에서 보여 주는 것 처럼 쉽게 혼동 됩니다.

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

 일반적으로 멤버를 호출할 때 형식 인수를 지정 하지 않아도 되도록 이전 선언 모두를 피해 야 합니다. 이로 인해 제네릭의 멤버를 호출 하기 위한 구문이 제네릭이 아닌의 구문과 다릅니다. 자세한 내용은 [CA1004를 참조 하세요. 제네릭 메서드는 ](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md) 형식 매개 변수를 제공 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 정적 멤버를 제거 하거나 인스턴스 멤버로 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 쉽게 이해 하 고 사용할 수 있는 구문에서 제네릭을 제공 하면 새 라이브러리의 도입 률을 배우고 늘리는 데 필요한 시간이 단축 됩니다.

## <a name="related-rules"></a>관련 규칙
 [CA1005: 제네릭 형식의 매개 변수를 과도 하 게 사용 하지 않습니다 ](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: 컬렉션은 제네릭 인터페이스를 구현 해야 ](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1002: 제네릭 목록을 노출 하지 않습니다 ](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: 멤버 시그니처에 제네릭 형식을 중첩 하지 마세요 ](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: 제네릭 메서드는 형식 매개 변수를 제공 해야 ](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 제네릭 이벤트 처리기 인스턴스를 사용 ](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 적절 한 ](../code-quality/ca1007-use-generics-where-appropriate.md) 제네릭을 사용 합니다.

## <a name="see-also"></a>관련 항목:
 [제네릭](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
