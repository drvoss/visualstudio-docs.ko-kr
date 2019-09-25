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
ms.openlocfilehash: 3fdd20df37586e50b5236872f1d84de48d08c87a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233533"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: GC.SuppressFinalize를 올바르게 호출하세요.

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|범주|Microsoft. 사용법|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

이 규칙의 위반은 다음과 같은 경우에 발생할 수 있습니다.

- 및의 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 구현인 메서드는를 호출 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>하지 않습니다.

- 및 호출 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>의 구현이 아닌 메서드입니다.

- 을 호출 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> 하 고 [이C#()](/dotnet/csharp/language-reference/keywords/this) 또는 [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)이외의 항목을 전달 하는 메서드입니다.

## <a name="rule-description"></a>규칙 설명

메서드 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 를 사용 하면 개체를 가비지 수집에 사용할 수 있게 되기 전에 언제 든 지 리소스를 해제할 수 있습니다. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 메서드가 호출 되 면 개체의 리소스를 해제 합니다. 이렇게 하면 종료 하지 않아도 됩니다. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>는를 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> 호출 하 여 가비지 수집기가 개체의 종료자를 호출 하지 않도록 해야 합니다.

종료 자가 다시 구현 <xref:System.IDisposable> 하 고 호출 하지 않아도 되는 파생 된 형식에 대해를 호출 하는 것을 방지 하려면 종료자 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>를 사용 하지 않는 봉인 되지 않은 형식에서

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 다음을 수행 합니다.

- 메서드가의 <xref:System.IDisposable.Dispose%2A>구현인 경우에는에 대 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>한 호출을 추가 합니다.

- 메서드가의 <xref:System.IDisposable.Dispose%2A>구현이 아닌 경우에 대 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> 한 호출을 제거 하거나 형식의 <xref:System.IDisposable.Dispose%2A> 구현으로 이동 합니다.

- [이C#()](/dotnet/csharp/language-reference/keywords/this) 또는 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)를 전달 하도록에 대 한 모든 호출을 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

의도적으로를 사용 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> 하 여 다른 개체의 수명을 제어 하는 경우에만이 규칙에서 경고를 표시 하지 않습니다. 의 <xref:System.IDisposable.Dispose%2A> 구현에서를 호출 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>하지 않는 경우에는이 규칙에서 경고를 표시 하지 마세요. 이 경우 종료를 표시 하지 않으면 성능이 저하 되 고 이점이 없습니다.

## <a name="example-that-violates-ca1816"></a>CA1816을 위반 하는 예제

이 코드는를 호출 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>하지만 [이 (C#)](/dotnet/csharp/language-reference/keywords/this) 또는 [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)를 전달 하지 않는 메서드를 보여 줍니다. 결과적으로이 코드는 규칙 CA1816를 위반 합니다.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>CA1816를 만족 하는 예제

이 예제에서는 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> [이 (C#)](/dotnet/csharp/language-reference/keywords/this) 또는 [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)를 전달 하 여 올바르게 호출 하는 메서드를 보여 줍니다.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>관련 규칙

- [CA2215: Dispose 메서드는 기본 클래스 dispose를 호출 해야 합니다.](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216: 삭제 가능한 형식은 종료자를 선언 해야 합니다.](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>참고 항목

- [Dispose 패턴](/dotnet/standard/design-guidelines/dispose-pattern)