---
title: 'CA1049: 네이티브 리소스는 삭제 가능 해야 합니다. 있는 형식은 | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 34a7b8352da8e8e8a3b92f36fe1d636633e3a8c9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686120"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: 네이티브 리소스가 있는 형식은 삭제 가능해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|범주|Microsoft.Design|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 형식 참조를 <xref:System.IntPtr?displayProperty=fullName> 필드를 <xref:System.UIntPtr?displayProperty=fullName> 필드 또는 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> 필드를 구현 하지 않습니다 하지만 <xref:System.IDisposable?displayProperty=fullName>합니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙이 있다고 가정 <xref:System.IntPtr>, <xref:System.UIntPtr>, 및 <xref:System.Runtime.InteropServices.HandleRef> 필드는 관리 되지 않는 리소스에 대 한 포인터를 저장 합니다. 관리 되지 않는 리소스를 할당 하는 형식은 구현 해야 <xref:System.IDisposable> 호출자가 요청 시 해당 리소스를 해제 하 고 리소스를 보유 하는 개체의 수명을 줄여야 수 있도록 합니다.

 관리 되지 않는 리소스를 정리 하는 좋은 디자인 패턴은 암시적와 사용 하 여 해당 리소스를 해제 하는 명시적 방법을 제공 합니다 <xref:System.Object.Finalize%2A?displayProperty=fullName> 메서드 및 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 메서드를 각각. 가비지 수집기가 호출 된 <xref:System.Object.Finalize%2A> 에서 더 이상 접근할 수를 확인 한 후 아무 때나 개체의 메서드. 후 <xref:System.Object.Finalize%2A> 호출 되는 추가 가비지 컬렉션 개체를 해제 해야 합니다. <xref:System.IDisposable.Dispose%2A> 메서드를 사용 하면 호출자가 명시적으로 요청, 가비지 수집기에 남은 리소스를 해제 되기 이전의 시 리소스를 해제 합니다. 관리 되지 않는 리소스를 정리한 후 <xref:System.IDisposable.Dispose%2A> 를 호출 해야 합니다 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 가비지 수집기를 알고 있어야 하는 방법 <xref:System.Object.Finalize%2A> 호출할; 더 이상 추가 가비지 수집에 대 한 필요성을 제거 하 고 단축이 개체의 수명입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 구현 <xref:System.IDisposable>합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 형식을 관리 되지 않는 리소스를 참조 하지 않는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다. 때문에이 규칙에서 경고를 표시 하지 마십시오이 고, 그렇지 구현 하지 못하면 <xref:System.IDisposable> 하면 관리 되지 않는 리소스를 사용할 수 없게 될 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 구현 하는 형식을 <xref:System.IDisposable> 관리 되지 않는 리소스를 정리 합니다.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA2115: GC를 호출 합니다. KeepAlive 네이티브 리소스를 사용 하는 경우](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: GC를 호출 합니다. SuppressFinalize 올바르게](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: 삭제 가능한 형식은 종료자를 선언 해야 합니다.](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: 삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>참고 항목
  [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
