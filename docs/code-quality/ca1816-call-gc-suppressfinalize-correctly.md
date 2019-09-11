---
title: 'CA1816: GC.SuppressFinalize를 올바르게 호출하세요.'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2c14f9ed8803c02d1570ac2a3dee82fbdfca5f01
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796782"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: GC.SuppressFinalize를 올바르게 호출하세요.

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|범주|Microsoft. 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인

이 규칙을 위반 하 여 발생할 수 있습니다.

- 구현 하는 메서드 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 호출 하지 않습니다 및 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>합니다.

- 구현의 없는 메서드에 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 호출 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>합니다.

- 호출 하는 메서드 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> 이외의 값을 전달 하 고 [this (C#)](/dotnet/csharp/language-reference/keywords/this) 하거나 [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)합니다.

## <a name="rule-description"></a>규칙 설명

<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 메서드를 사용 하면 사용자 개체를 가비지 수집 되기 전에 언제 든 지 리소스를 해제 합니다. 경우는 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 메서드를 호출할 개체의 리소스를 해제 합니다. 이렇게 하면 종료는 불필요 합니다. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 호출 해야 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> 하므로 가비지 수집기에서 개체의 종료자를 호출 하지 않습니다.

파생된 형식 종료자를 사용 하 여 다시 구현 하지 않아도 못하도록 <xref:System.IDisposable> 계속 호출 해야 종료자 없이 unsealed 형식의 호출 하 고 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

에이 규칙 위반 문제를 해결 합니다.

- 메서드 구현의 경우 <xref:System.IDisposable.Dispose%2A>, 호출을 추가 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>합니다.

- 메서드 구현의 없으면 <xref:System.IDisposable.Dispose%2A>에 대 한 호출을 제거 하거나 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> 형식으로 이동 하거나 <xref:System.IDisposable.Dispose%2A> 구현 합니다.

- 에 대 한 모든 호출을 변경 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> 전달할 [this (C#)](/dotnet/csharp/language-reference/keywords/this) 하거나 [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하는 경우

의도적으로 사용 하는 경우에이 규칙에서 경고를 표시 하지 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> 다른 개체의 수명을 제어 합니다. 구현의 경우에이 규칙에서 경고를 표시 하지 않습니다 <xref:System.IDisposable.Dispose%2A> 호출 하지 않으면 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>합니다. 이 경우 종료 되지 않도록 하는 데 실패 하 고 성능이 저하 됩니다 및 장점을 제공 하지 않습니다.

## <a name="example-that-violates-ca1816"></a>CA1816 위반 하는 예제

이 코드를 호출 하는 메서드를 보여 줍니다 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>를 통과 하지 않지만 [this (C#)](/dotnet/csharp/language-reference/keywords/this) 또는 [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)합니다. 결과적으로,이 코드는 CA1816 규칙을 위반 합니다.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>CA1816 충족 하는 예제

이 예제에서는 메서드를 보여 줍니다는 올바르게 호출 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> 전달 하 여 [this (C#)](/dotnet/csharp/language-reference/keywords/this) 하거나 [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)합니다.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>관련된 규칙

- [CA2215: Dispose 메서드는 기본 클래스 dispose를 호출 해야 합니다.](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216: 삭제 가능한 형식은 종료자를 선언 해야 합니다.](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>참고자료

- [삭제 패턴](/dotnet/standard/design-guidelines/dispose-pattern)