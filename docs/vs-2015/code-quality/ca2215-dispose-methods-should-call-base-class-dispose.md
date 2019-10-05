---
title: 'CA2215: Dispose 메서드는 기본 클래스 dispose를 호출 해야 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bc934afd9289a6bce425084f3588a7e912baf9b9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681188"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Dispose 메서드는 기본 클래스 Dispose를 호출해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 구현 하는 형식을 <xref:System.IDisposable?displayProperty=fullName> 도 구현 하는 형식에서 상속 <xref:System.IDisposable>합니다. 합니다 <xref:System.IDisposable.Dispose%2A> 상속 하는 형식의 메서드를 호출 하지 않습니다는 <xref:System.IDisposable.Dispose%2A> 부모 형식의 메서드.

## <a name="rule-description"></a>규칙 설명
 삭제 가능한 형식에서 상속 되는 형식은 호출 해야 합니다 <xref:System.IDisposable.Dispose%2A> 자체 내에서 기본 형식 메서드의 <xref:System.IDisposable.Dispose%2A> 메서드. 기본 형식에 의해 만들어진 모든 리소스 해제는 Dispose 되도록 기본 형식 메서드를 호출 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 호출 `base`합니다.<xref:System.IDisposable.Dispose%2A> 사용자 <xref:System.IDisposable.Dispose%2A> 메서드.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 안전 하 게 하는 경우이 규칙에서 경고를 표시 하는 것에 대 한 호출 `base`합니다.<xref:System.IDisposable.Dispose%2A> 규칙 검사 보다 더 하위 수준 호출 발생합니다.

## <a name="example"></a>예제
 다음 예제에서는 형식을 보여 줍니다 `TypeA` 구현 하는 <xref:System.IDisposable>합니다.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>예제
 다음 예제에서는 형식을 보여 줍니다 `TypeB` 형식에서 상속 되 `TypeA` 제대로 호출 및 해당 <xref:System.IDisposable.Dispose%2A> 메서드.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.IDisposable?displayProperty=fullName> [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
