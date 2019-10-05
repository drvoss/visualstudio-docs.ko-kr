---
title: 'CA2202: 개체를 여러 번 삭제하지 마십시오.'
ms.date: 07/16/2019
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c7fa7756383426f990e18225995a768de9fefbd
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231733"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: 개체를 여러 번 삭제하지 마십시오.

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|범주|Microsoft.Usage|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

메서드 구현에는 같은 개체에 대 한 여러 호출 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 을 발생 시킬 수 있는 코드 경로 또는 일부 형식에 대 한 Close () 메서드와 같은 Dispose와 동일한 개체가 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명

올바르게 구현 <xref:System.IDisposable.Dispose%2A> 된 메서드는 예외를 throw 하지 않고 여러 번 호출할 수 있습니다. 그러나이는 보장 되지 않으며,를 생성 하지 않도록 <xref:System.ObjectDisposedException?displayProperty=fullName> 하려면 개체에 대해 <xref:System.IDisposable.Dispose%2A> 를 두 번 이상 호출 하면 안 됩니다.

## <a name="related-rules"></a>관련 규칙

- [CA2000: 범위를 벗어나기 전에 개체를 삭제 하십시오.](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 코드 경로 <xref:System.IDisposable.Dispose%2A> 에 관계 없이 개체에 대해 한 번만 호출 되도록 구현을 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

이 규칙에서는 경고를 표시해야 합니다. 개체의 <xref:System.IDisposable.Dispose%2A> 를 안전 하 게 호출할 수 있는 것으로 알려진 경우에도 나중에 구현이 변경 될 수 있습니다.

## <a name="example"></a>예제

중첩 `using` 된 문`Using` (Visual Basic)은 CA2202 경고 위반을 일으킬 수 있습니다. 중첩 된 내부 `using` 문의 IDisposable 리소스가 외부 `using` 문의 리소스를 포함 하는 경우 중첩 된 리소스의 `Dispose` 메서드는 포함 된 리소스를 해제 합니다. 이러한 상황이 발생 하면 외부 `Dispose` `using` 문의 메서드는 해당 리소스를 두 번 삭제 하려고 시도 합니다.

다음 예제 <xref:System.IO.Stream> 에서 외부 using 문으로 만든 개체는 개체가 포함 `stream` 된 <xref:System.IO.StreamWriter> 개체의 Dispose 메서드에 있는 using 문 끝에서 해제 됩니다. 외부 `using` 문의`stream` 끝에 개체를 두 번 해제 합니다. 두 번째 릴리스는 CA2202를 위반 하는 것입니다.

```csharp
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>예제

이 문제 `try` 를 해결 하려면 외부 / `using` 문 대신 블록을 `finally` 사용 합니다. 블록에서 `stream` 리소스가 null이 아닌지 확인 합니다. `finally`

```csharp
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    stream?.Dispose();
}
```

> [!TIP]
> 위의 구문은 null [조건부 연산자입니다.](/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-) `?.`

## <a name="see-also"></a>참고 항목

- <xref:System.IDisposable?displayProperty=fullName>
- [삭제 패턴](/dotnet/standard/design-guidelines/dispose-pattern)