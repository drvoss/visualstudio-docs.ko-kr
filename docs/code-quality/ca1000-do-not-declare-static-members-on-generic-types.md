---
title: 'CA1000: 정적 멤버를 제네릭 형식으로 선언하지 마십시오.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5ec0e60302e1d6bff813a7bf0f39e1b71a6f1653
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548388"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: 정적 멤버를 제네릭 형식으로 선언하지 마십시오.

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 제네릭 형식이 포함 된 `static` (`Shared` Visual Basic의) 멤버입니다.

## <a name="rule-description"></a>규칙 설명
 경우는 `static` 제네릭 형식의 멤버 라고, 형식에 대 한 형식 인수를 지정 해야 합니다. 유추를 지원하지 않는 제네릭 인스턴스 멤버를 호출할 때는 멤버에 형식 인수를 지정해야 합니다. 이러한 두 가지 경우에 형식 인수를 지정 하는 것에 대 한 구문은 서로 다르며 혼동을 대로 다음 호출을 보여 줍니다.

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

 일반적으로 둘 다 이전 선언의 형식 인수는 멤버가 호출 될 때 지정할 필요가 없습니다 있도록 피해 야 합니다. 이 구문에서 제네릭이 아닌 구문은 다르지는 제네릭의 멤버를 호출에 대 한 결과입니다. 자세한 내용은 [CA1004: 제네릭 메서드 형식 매개 변수를 제공 해야](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하 고, 정적 멤버를 제거 또는 인스턴스 멤버를 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하는 경우
 이 규칙에서는 경고를 표시해야 합니다. 새 라이브러리의 도입 률을 높이고 학습에 걸리는 시간이 줄어듭니다 제네릭을 이해 및 사용 하기 쉬운 구문 제공 합니다.

## <a name="related-rules"></a>관련된 규칙
 [CA1005: 제네릭 형식에 매개 변수를 너무 많이 사용하지 마십시오.](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: 컬렉션은 제네릭 인터페이스를 구현해야 합니다.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1002: 제네릭 목록을 노출하지 마십시오.](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: 멤버 시그니처에 제네릭 형식을 중첩하지 마십시오.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: 제네릭 메서드는 형식 매개 변수를 제공해야 합니다.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: 제네릭 이벤트 처리기 인스턴스를 사용하십시오.](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: 적합한 제네릭을 사용하십시오.](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>참고자료
 [제네릭](/dotnet/csharp/programming-guide/generics/index)