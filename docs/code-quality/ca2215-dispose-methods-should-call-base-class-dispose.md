---
title: 'CA2215: Dispose 메서드는 기본 클래스 Dispose를 호출해야 합니다.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 468b63ca554ea126bbd621a2502e54540e6ed068
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231276"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Dispose 메서드는 기본 클래스 Dispose를 호출해야 합니다.

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|범주|Microsoft.Usage|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인
을 구현 하 <xref:System.IDisposable?displayProperty=fullName> 는 형식은도 구현 <xref:System.IDisposable>하는 형식에서 상속 됩니다. 상속 하는 형식의 <xref:System.IDisposable.Dispose%2A> 메서드는부모형식의메서드를호출하지않습니다.<xref:System.IDisposable.Dispose%2A>

## <a name="rule-description"></a>규칙 설명
형식이 삭제 가능한 형식에서 상속 되는 경우 자체 <xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable.Dispose%2A> 메서드 내에서 기본 형식의 메서드를 호출 해야 합니다. 기본 형식 메서드 Dispose를 호출 하면 기본 형식에서 생성 된 모든 리소스가 해제 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면를 호출 `base`합니다.<xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable.Dispose%2A> 메서드에서

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
을 호출 하는 경우에 `base`는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.<xref:System.IDisposable.Dispose%2A> 규칙 검사 보다 더 깊은 호출 수준에서 발생 합니다.

## <a name="example"></a>예제
다음 예제에서는를 구현 `TypeA` <xref:System.IDisposable>하는 형식을 보여 줍니다.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>예제
다음 예제에서는 형식 `TypeB` `TypeA` 에서 상속 하 고 해당 <xref:System.IDisposable.Dispose%2A> 메서드를 올바르게 호출 하는 형식을 보여 줍니다.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>참고 항목

- <xref:System.IDisposable?displayProperty=fullName>
- [삭제 패턴](/dotnet/standard/design-guidelines/dispose-pattern)