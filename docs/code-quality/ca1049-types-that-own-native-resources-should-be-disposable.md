---
title: 'CA1049: 네이티브 리소스가 있는 형식은 삭제 가능해야 합니다.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- cplusplus
ms.openlocfilehash: ef7b72eade7ea8e4486d5c317c06026bb4d0b95f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235737"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: 네이티브 리소스가 있는 형식은 삭제 가능해야 합니다.

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|범주|Microsoft.Design|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

형식은 <xref:System.IntPtr?displayProperty=fullName> 필드 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> , 필드 또는 필드를 참조 하지만는 구현 <xref:System.IDisposable?displayProperty=fullName>하지 않습니다. <xref:System.UIntPtr?displayProperty=fullName>

## <a name="rule-description"></a>규칙 설명

이 규칙 <xref:System.IntPtr>에서는, <xref:System.UIntPtr>및 <xref:System.Runtime.InteropServices.HandleRef> 필드가 관리 되지 않는 리소스에 대 한 포인터를 저장 한다고 가정 합니다. 관리 되지 않는 리소스를 할당 하 <xref:System.IDisposable> 는 형식은 호출자가 요청 시 해당 리소스를 해제 하 고 리소스를 보유 하는 개체의 수명을 단축할 수 있도록 구현 해야 합니다.

관리 되지 않는 리소스를 정리 하기 위한 권장 디자인 패턴은 각각 <xref:System.Object.Finalize%2A?displayProperty=fullName> 메서드와 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 메서드를 사용 하 여 해당 리소스를 해제 하기 위한 암시적 및 명시적 수단을 제공 하는 것입니다. 가비지 수집기는 개체가 더 <xref:System.Object.Finalize%2A> 이상 연결할 수 없는 것으로 확인 된 후 특정 시간에 개체의 메서드를 호출 합니다. 가 <xref:System.Object.Finalize%2A> 호출 된 후 개체를 해제 하려면 추가 가비지 컬렉션이 필요 합니다. <xref:System.IDisposable.Dispose%2A> 메서드를 사용 하면 호출자가 가비지 수집기에 남아 있는 경우 리소스를 해제 하는 대신 요청 시 리소스를 명시적으로 해제할 수 있습니다. 관리 되지 않는 리소스를 정리한 후에 <xref:System.IDisposable.Dispose%2A> 는 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 메서드를 호출 하 여 가비지 수집기가 더 이상 <xref:System.Object.Finalize%2A> 호출할 필요가 없음을 알 수 있도록 해야 합니다. 이렇게 하면 추가 가비지 수집을 수행할 필요가 없으며 개체의 수명입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면을 구현 <xref:System.IDisposable>합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
형식이 관리 되지 않는 리소스를 참조 하지 않는 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다. 그렇지 않으면를 구현 <xref:System.IDisposable> 하는 데 실패 하면 관리 되지 않는 리소스가 사용할 수 없게 되거나 사용할 수 없게 될 수 있으므로이 규칙에서 경고를 표시 하지 마십시오.

## <a name="example"></a>예제
다음 예제에서는 관리 되지 않는 리소스를 <xref:System.IDisposable> 정리 하기 위해를 구현 하는 형식을 보여 줍니다.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>관련 규칙
[CA2115: GC를 호출 합니다. 네이티브 리소스를 사용 하는 경우 KeepAlive](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: GC를 호출 합니다. Gc.suppressfinalize 올바르게](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA2216: 삭제 가능한 형식은 종료자를 선언 해야 합니다.](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA1001: 삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>참고 항목

- [관리되지 않는 리소스 정리](/dotnet/standard/garbage-collection/unmanaged)
- [삭제 패턴](/dotnet/standard/design-guidelines/dispose-pattern)