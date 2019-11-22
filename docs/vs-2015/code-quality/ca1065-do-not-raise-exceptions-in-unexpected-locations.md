---
title: 'CA1065: Do not raise exceptions in unexpected locations | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 439c6b5fc30be2e76eb6c0b6a44b1ec5226633b1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295938"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: 예기치 않은 위치에서 예외를 발생시키지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|범주|Microsoft.Design|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 예외를 throw하지 않아야 하는 메서드가 예외를 throw했습니다.

## <a name="rule-description"></a>규칙 설명
 Methods that are not expected to throw exceptions can be categorized as follows:

- Property Get Methods

- 이벤트 접근자 메서드

- Equals Methods

- GetHashCode Methods

- ToString Methods

- 정적 생성자

- 종료자

- Dispose Methods

- 같음 연산자

- Implicit Cast Operators

  The following sections discuss these method types.

### <a name="property-get-methods"></a>Property Get Methods
 Properties are basically smart fields. Therefore, they should behave like a field as much as possible. Fields do not throw exceptions and neither should properties. If you have a property that throws an exception, consider making it a method.

 The following exceptions are allowed to be thrown from a property get method:

- <xref:System.InvalidOperationException?displayProperty=fullName> and all derivatives (including <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> and all derivatives

- <xref:System.ArgumentException?displayProperty=fullName> (only from indexed get)

- <xref:System.Collections.Generic.KeyNotFoundException> (only from indexed get)

### <a name="event-accessor-methods"></a>이벤트 접근자 메서드
 Event accessors should be simple operations that do not throw exceptions. An event should not throw an exception when you try to add or remove an event handler.

 The following exceptions are allowed to be thrown from an event accesor:

- <xref:System.InvalidOperationException?displayProperty=fullName> and all derivatives (including <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> and all derivatives

- <xref:System.ArgumentException> and derivatives

### <a name="equals-methods"></a>Equals Methods
 The following **Equals** methods should not throw exceptions:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- [M:IEquatable.Equals](https://go.microsoft.com/fwlink/?LinkId=113472)

  An **Equals** method should return `true` or `false` instead of throwing an exception. For example, if Equals is passed two mismatched types it should just return `false` instead of throwing an <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>GetHashCode Methods
 The following **GetHashCode** methods should usually not throw exceptions:

- <xref:System.Object.GetHashCode%2A>

- [M:IEqualityComparer.GetHashCode(T)](https://go.microsoft.com/fwlink/?LinkId=113477)

  **GetHashCode** should always return a value. Otherwise, you can lose items in the hash table.

  The versions of **GetHashCode** that take an argument can throw an <xref:System.ArgumentException>. However, **Object.GetHashCode** should never throw an exception.

### <a name="tostring-methods"></a>ToString Methods
 The debugger uses <xref:System.Object.ToString%2A?displayProperty=fullName> to help display information about objects in string format. Therefore, **ToString** should not change the state of an object and it should not throw exceptions.

### <a name="static-constructors"></a>정적 생성자
 Throwing exceptions from a static constructor causes the type to be unusable in the current application domain. You should have a very good reason (such as a security issue) for throwing an exception from a static constructor.

### <a name="finalizers"></a>종료자
 Throwing an exception from a finalizer causes the CLR to fail fast, which tears down the process. Therefore, throwing exceptions in a finalizer should always be avoided.

### <a name="dispose-methods"></a>Dispose Methods
 A <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> method should not throw an exception. Dispose is often called as part of the clean up logic in a `finally` clause. Therefore, explicitly throwing an exception from Dispose forces the user to add exception handling inside the `finally` clause.

 The **Dispose(false)** code path should never throw exceptions, because this is almost always called from a finalizer.

### <a name="equality-operators--"></a>Equality Operators (==, !=)
 Like Equals methods, equality operators should return either `true` or `false` and should not throw exceptions.

### <a name="implicit-cast-operators"></a>Implicit Cast Operators
 Because the user is often unaware that an implicit cast operator has been called, an exception thrown by the implicit cast operator is completely unexpected. Therefore, no exceptions should be thrown from implicit cast operators.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 For property getters, either change the logic so that it no longer has to throw an exception, or change the property into a method.

 For all other method types listed previously, change the logic so that it no longer must throw an exception.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 It is safe to suppress a warning from this rule if the violation was caused by an exception declaration instead of a thrown exception.

## <a name="related-rules"></a>Related Rules
 [CA2219: exception 절에서 예외를 발생시키지 마십시오.](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>관련 항목:
 [디자인 경고](../code-quality/design-warnings.md)
