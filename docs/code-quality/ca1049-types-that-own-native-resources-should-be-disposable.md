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
ms.openlocfilehash: 03b8d222fc2349022ef324c9905279677fc86849
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306122"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: 네이티브 리소스가 있는 형식은 삭제 가능해야 합니다.

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|범주|Microsoft.Design|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

형식이 <xref:System.IntPtr?displayProperty=fullName> 필드, <xref:System.UIntPtr?displayProperty=fullName> 필드 또는 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> 필드를 참조 하지만 <xref:System.IDisposable?displayProperty=fullName>을 구현 하지 않습니다.

## <a name="rule-description"></a>규칙 설명

이 규칙에서는 <xref:System.IntPtr>, <xref:System.UIntPtr> 및 <xref:System.Runtime.InteropServices.HandleRef> 필드가 관리 되지 않는 리소스에 대 한 포인터를 저장 한다고 가정 합니다. 관리 되지 않는 리소스를 할당 하는 형식은 호출자가 요청 시 해당 리소스를 해제 하 고 리소스를 보유 하는 개체의 수명을 단축할 수 있도록 <xref:System.IDisposable>을 구현 해야 합니다.

관리 되지 않는 리소스를 정리 하는 데 권장 되는 디자인 패턴은 <xref:System.Object.Finalize%2A?displayProperty=fullName> 메서드와 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 메서드를 사용 하 여 해당 리소스를 해제 하기 위한 암시적 및 명시적 방법을 모두 제공 하는 것입니다. 가비지 수집기는 개체에 더 이상 연결할 수 없는 것으로 확인 된 후 개체의 <xref:System.Object.Finalize%2A> 메서드를 결정 하지 않은 시간에 호출 합니다. @No__t-0이 호출 된 후 개체를 해제 하려면 추가 가비지 컬렉션이 필요 합니다. @No__t-0 메서드를 사용 하면 호출자가 가비지 수집기를 사용 하 여 남은 경우 리소스가 해제 되는 것 보다 먼저 요청 시 리소스를 명시적으로 해제할 수 있습니다. 관리 되지 않는 리소스를 정리한 후 <xref:System.IDisposable.Dispose%2A>은 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 메서드를 호출 하 여 가비지 수집기에서 <xref:System.Object.Finalize%2A>가 더 이상 호출 되지 않음을 알 수 있도록 합니다. 이렇게 하면 추가 가비지 수집을 수행할 필요가 없으며 개체의 수명이 단축 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
이 규칙 위반 문제를 해결 하려면 <xref:System.IDisposable>을 구현 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우
형식이 관리 되지 않는 리소스를 참조 하지 않는 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다. 그렇지 않으면 <xref:System.IDisposable>을 구현 하지 못하면 관리 되지 않는 리소스가 사용할 수 없게 되거나 사용할 수 없게 될 수 있으므로이 규칙에서 경고를 표시 하지 마십시오.

## <a name="example"></a>예제
다음 예제에서는 <xref:System.IDisposable>을 구현 하 여 관리 되지 않는 리소스를 정리 하는 형식을 보여 줍니다.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>관련 규칙
[CA2115: GC를 호출 합니다. 네이티브 리소스를 사용 하는 경우 KeepAlive @ no__t-0

[CA1816: GC를 호출 합니다. Gc.suppressfinalize 올바르게 @ no__t-0

[CA2216: 삭제 가능한 형식은 종료자 @ no__t를 선언 해야 합니다.

[CA1001: 삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>참조

- [관리되지 않는 리소스 정리](/dotnet/standard/garbage-collection/unmanaged)
- [삭제 패턴](/dotnet/standard/design-guidelines/dispose-pattern)