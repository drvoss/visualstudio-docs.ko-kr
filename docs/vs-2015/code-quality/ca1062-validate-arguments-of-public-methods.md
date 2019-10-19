---
title: 'CA1062: public 메서드의 인수 유효성을 검사 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 50044b51a3e576ff7d1c11b19b2f498f99b63019
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663649"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: public 메서드의 인수의 유효성을 검사하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|범주|Microsoft 디자인|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 메서드는 인수가 `null` 인지 여부를 확인 하지 않고 참조 인수 중 하나를 역참조 합니다 (Visual Basic의 `Nothing`).

## <a name="rule-description"></a>규칙 설명
 외부에서 볼 수 있는 메서드에 전달 되는 모든 참조 인수는 `null`에 대해 확인 해야 합니다. 해당 하는 경우 인수를 `null` 하면 <xref:System.ArgumentNullException>을 throw 합니다.

 Public 또는 protected로 선언 되기 때문에 알 수 없는 어셈블리에서 메서드를 호출할 수 있는 경우 메서드의 모든 매개 변수 유효성을 검사 해야 합니다. 메서드가 알려진 어셈블리에 의해서만 호출 되도록 디자인 된 경우 메서드를 internal로 설정 하 고 메서드를 포함 하는 어셈블리에 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 특성을 적용 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 `null`에 대해 각 참조 인수의 유효성을 검사 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 역참조 된 매개 변수가 함수의 다른 메서드 호출에서 유효성을 검사 한 것으로 확인 되는 경우이 규칙에서 경고를 표시 하지 않을 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 메서드와 규칙을 충족 하는 메서드를 보여 줍니다.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>예제
 @No__t_0에서이 규칙은 유효성 검사를 수행 하는 다른 메서드에 매개 변수가 전달 되 고 있음을 감지 하지 않습니다.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>예제
 참조 개체인 필드 또는 속성을 채우는 복사 생성자도 CA1062 규칙을 위반할 수 있습니다. 복사 생성자에 전달 된 복사 된 개체가 `null` `Nothing` (Visual Basic) 될 수 있으므로 위반이 발생 합니다. 위반 문제를 해결 하려면 정적 (Visual Basic에서 공유) 메서드를 사용 하 여 복사한 개체가 null이 아닌 지 확인 합니다.

 다음 `Person` 클래스 예제에서는 `Person` 복사 생성자로 전달 되는 `other` 개체를 `null` 수 있습니다.

```

public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>예제
 다음 수정 된 `Person` 예제에서 복사 생성자에 전달 되는 `other` 개체는 먼저 `PassThroughNonNull` 메서드에서 null 인지 확인 합니다.

```
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException("person");
        return person;
    }
}
```
