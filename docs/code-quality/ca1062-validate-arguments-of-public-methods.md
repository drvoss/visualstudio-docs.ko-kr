---
title: 'CA1062: public 메서드의 인수에 대한 유효성을 검사하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8106a4c0244cbd79e88a2bdc50e04ea74627dab4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235332"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: public 메서드의 인수에 대한 유효성을 검사하세요.

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|범주|Microsoft.Design|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

외부에서 볼 수 `null` 있는 메서드는 해당 인수가 (`Nothing` Visual Basic) 인지 여부를 확인 하지 않고 해당 참조 인수 중 하나를 역참조 합니다.

## <a name="rule-description"></a>규칙 설명

외부에서 볼 수 있는 메서드에 전달 되는 모든 참조 인수를 확인 `null`해야 합니다. 적절 한 경우 인수가 인 <xref:System.ArgumentNullException> `null`경우을 throw 합니다.

Public 또는 protected로 선언 되기 때문에 알 수 없는 어셈블리에서 메서드를 호출할 수 있는 경우 메서드의 모든 매개 변수 유효성을 검사 해야 합니다. 알려진 어셈블리만 호출 하도록 메서드를 디자인 한 경우 메서드를 internal로 설정 하 고 메서드를 포함 하는 어셈블리 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 에 특성을 적용 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면에 대해 `null`각 참조 인수의 유효성을 검사 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

역참조 된 매개 변수가 함수의 다른 메서드 호출에서 유효성을 검사 한 것으로 확인 되는 경우이 규칙에서 경고를 표시 하지 않을 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 규칙을 위반 하는 메서드와 규칙을 충족 하는 메서드를 보여 줍니다.

```csharp
using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException("input");
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>예제

참조 개체인 필드 또는 속성을 채우는 복사 생성자도 CA1062 규칙을 위반할 수 있습니다. 복사 생성자에 전달 된 복사 된 개체가 ( `null` `Nothing` Visual Basic) 일 수 있기 때문에 위반이 발생 합니다. 위반 문제를 해결 하려면 정적 (Visual Basic에서 공유) 메서드를 사용 하 여 복사한 개체가 null이 아닌 지 확인 합니다.

다음 `Person` 클래스 예제에서 `Person` 복사 생성자에 `other` 전달 되는 개체는 일 `null`수 있습니다.

```csharp
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

다음 수정 `Person` 된 예제 `other` 에서는 복사 생성자에 전달 된 개체가 먼저 `PassThroughNonNull` 메서드에서 null 인지 확인 합니다.

```csharp
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