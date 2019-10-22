---
title: 'CA1049: 네이티브 리소스가 있는 형식은 삭제 가능 해야 합니다. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aaaf95346c51e2cb5cadb01a39e482bb508bc764
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668902"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: 네이티브 리소스가 있는 형식은 삭제 가능해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|범주|Microsoft 디자인|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 형식이 <xref:System.IntPtr?displayProperty=fullName> 필드, <xref:System.UIntPtr?displayProperty=fullName> 필드 또는 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> 필드를 참조 하지만 <xref:System.IDisposable?displayProperty=fullName>을 구현 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙에서는 <xref:System.IntPtr>, <xref:System.UIntPtr> 및 <xref:System.Runtime.InteropServices.HandleRef> 필드가 관리 되지 않는 리소스에 대 한 포인터를 저장 한다고 가정 합니다. 관리 되지 않는 리소스를 할당 하는 형식은 호출자가 요청 시 해당 리소스를 해제 하 고 리소스를 보유 하는 개체의 수명을 단축할 수 있도록 <xref:System.IDisposable>을 구현 해야 합니다.

 관리 되지 않는 리소스를 정리 하는 데 권장 되는 디자인 패턴은 각각 <xref:System.Object.Finalize%2A?displayProperty=fullName> 메서드와 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 메서드를 사용 하 여 해당 리소스를 해제 하기 위한 암시적 및 명시적 수단을 제공 하는 것입니다. 가비지 수집기는 개체에 더 이상 연결할 수 없는 것으로 확인 된 후 개체의 <xref:System.Object.Finalize%2A> 메서드를 결정 하지 않은 시간에 호출 합니다. @No__t_0를 호출한 후 개체를 해제 하려면 추가 가비지 컬렉션이 필요 합니다. 호출자는 <xref:System.IDisposable.Dispose%2A> 메서드를 사용 하 여 요청 시 리소스를 명시적으로 해제할 수 있습니다. 이전에는 가비지 수집기를 사용 하는 경우 리소스를 해제 해야 합니다. 관리 되지 않는 리소스를 정리한 후에는 <xref:System.IDisposable.Dispose%2A> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 메서드를 호출 하 여 가비지 수집기에서 <xref:System.Object.Finalize%2A> 더 이상 호출할 필요가 없음을 알 수 있도록 해야 합니다. 이렇게 하면 추가 가비지 수집을 수행할 필요가 없으며 개체의 수명이 단축 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 <xref:System.IDisposable>을 구현 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 형식이 관리 되지 않는 리소스를 참조 하지 않는 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다. 그렇지 않으면 <xref:System.IDisposable>을 구현 하지 못하면 관리 되지 않는 리소스가 사용할 수 없게 되거나 사용할 수 없게 될 수 있으므로이 규칙에서 경고를 표시 하지 마십시오.

## <a name="example"></a>예제
 다음 예제에서는 <xref:System.IDisposable>을 구현 하 여 관리 되지 않는 리소스를 정리 하는 형식을 보여 줍니다.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>관련 규칙
 [CA2115: 네이티브 리소스를 사용하는 경우에는 GC.KeepAlive를 호출하십시오.](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: GC.SuppressFinalize를 올바르게 호출하십시오.](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: 삭제 가능한 형식은 종료자를 선언해야 합니다.](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: 삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>관련 항목:
  [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
