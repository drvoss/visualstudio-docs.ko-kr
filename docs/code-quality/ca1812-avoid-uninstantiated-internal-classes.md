---
title: 'CA1812: 인스턴스화되지 않은 내부 클래스를 사용하지 마세요.'
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f924e9530a7ee43ec2222366141c3af6be2efc29
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233605"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: 인스턴스화되지 않은 내부 클래스를 사용하지 마세요.

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|범주|Microsoft.Performance|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

내부 (어셈블리 수준) 형식은 인스턴스화되지 않습니다.

## <a name="rule-description"></a>규칙 설명

이 규칙은 형식의 생성자 중 하나에 대 한 호출을 찾으려고 시도 하 고 호출을 찾을 수 없는 경우 위반을 보고 합니다.

이 규칙은 다음 형식을 검사 하지 않습니다.

- 값 형식

- 추상 형식

- 열거형

- 대리자

- 컴파일러에서 내보낸 배열 형식

- 인스턴스화할 수 없고 ([ `Shared` Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)) 메서드만을 정의 [`static`](/dotnet/csharp/language-reference/keywords/static) 하는 형식입니다.

분석 중인 어셈블리 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> 에를 적용 하는 경우 friend 어셈블리에서 필드를 사용할 수 있기 때문에이 규칙은 [`internal`](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend))로 표시 된 형식에 플래그를 지정 하지 않습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 형식을 제거 하거나 해당 형식을 사용 하는 코드를 추가 합니다. 형식에 `static` 메서드만 포함 된 경우 다음 중 하나를 형식에 추가 하 여 컴파일러가 기본 public 인스턴스 생성자를 내보내지 않도록 합니다.

- .NET Framework 2.0 이상을 C# 대상으로 하는 형식에 대 한 한정자입니다.`static`

- .NET Framework 버전 1.0 및 1.1를 대상으로 하는 형식의 전용 생성자입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

이 규칙에서는 경고를 표시 하지 않는 것이 안전 합니다. 다음과 같은 상황에서는이 경고를 표시 하지 않는 것이 좋습니다.

- 클래스는와 <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>같은 런타임에 바인딩된 리플렉션 메서드를 통해 만들어집니다.

- 클래스는 런타임 또는 ASP.NET에서 자동으로 생성 됩니다. 자동으로 생성 된 클래스의 몇 가지 예는 <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> 또는 <xref:System.Web.IHttpHandler?displayProperty=fullName>를 구현 하는 클래스입니다.

- 클래스는 [ `new` 제약 조건이](/dotnet/csharp/language-reference/keywords/new-constraint)있는 형식 매개 변수로 전달 됩니다. 다음 예는 rule CA1812 플래그가 지정 됩니다.

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }

    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

## <a name="related-rules"></a>관련 규칙

- [CA1811: 호출 되지 않는 private 코드 방지](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801: 사용 하지 않는 매개 변수 검토](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804: 사용 하지 않는 지역 제거](../code-quality/ca1804-remove-unused-locals.md)