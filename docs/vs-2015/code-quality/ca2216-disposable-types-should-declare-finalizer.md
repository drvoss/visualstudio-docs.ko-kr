---
title: 'CA2216: 삭제 가능한 형식은 종료자를 선언 해야 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8a033dbb152542e528b32e26f35a7d63dba30891
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681175"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: 삭제 가능한 형식은 종료자를 선언해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 구현 하는 형식을 <xref:System.IDisposable?displayProperty=fullName>, 및 관리 되지 않는 리소스의 사용을 암시 하는 필드에 설명 된 대로 종료자를 구현 하지 않는 <xref:System.Object.Finalize%2A?displayProperty=fullName>합니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙 위반에는 삭제 가능한 형식에는 다음 형식의 필드가 포함 된 경우 보고 됩니다.

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 호출 하는 종료자를 구현 하면 <xref:System.IDisposable.Dispose%2A> 메서드.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 형식을 구현 하지 않는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다 <xref:System.IDisposable> 관리 되지 않는 리소스를 해제 하기 위해.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 형식을 보여 줍니다.

 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DisposeNoFinalize/cs/FxCop.Usage.DisposeNoFinalize.cs#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA2115: GC를 호출 합니다. KeepAlive 네이티브 리소스를 사용 하는 경우](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: GC를 호출 합니다. SuppressFinalize 올바르게](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA1049: 네이티브 리소스가 있는 형식은 삭제 가능 해야 합니다.](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>참고 항목
 <xref:System.IDisposable?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
