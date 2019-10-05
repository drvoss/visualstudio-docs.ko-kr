---
title: 'CA2213: 삭제 가능한 필드를 삭제 해야 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cbb606729fe89eb5c2ebe3c814096ef39120836a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685263"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: 삭제 가능한 필드는 삭제해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 구현 하는 형식을 <xref:System.IDisposable?displayProperty=fullName> 도 구현 하는 형식의 필드를 선언 <xref:System.IDisposable>합니다. 합니다 <xref:System.IDisposable.Dispose%2A> 필드의 메서드가 호출 되지 않습니다는 <xref:System.IDisposable.Dispose%2A> 메서드의 선언 형식입니다.

## <a name="rule-description"></a>규칙 설명
 형식은 모든 해당 관리 되지 않는 리소스만 해제를 담당 구현 하 여 이렇게 <xref:System.IDisposable>합니다. 이 규칙을 삭제 가능한 형식 되는지 여부를 검사 `T` 필드를 선언 `F` 여러분의 삭제 가능 형식의 인스턴스인 `FT`합니다. 각 필드에 대 한 `F`, 규칙에 대 한 호출을 찾으려고 시도 `FT.Dispose`합니다. 호출할 메서드를 검색 하는 규칙이 `T.Dispose`, 및 한 수준 아래 (호출한 메서드에 의해 호출 된 메서드 `FT.Dispose`).

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 호출 <xref:System.IDisposable.Dispose%2A> 구현 하는 형식의 필드에 <xref:System.IDisposable> 경우 할당에 대 한 책임이 있으며, 필드로 유지 관리 되지 않는 리소스를 해제 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 안전 자신이 담당 하지 않는 필드를 보유 하는 리소스를 해제 한 경우 또는 경우에이 규칙에서 경고를 표시 하 게 호출 <xref:System.IDisposable.Dispose%2A> 규칙 검사를 보다 자세히 호출 수준에서 발생 합니다.

## <a name="example"></a>예제
 다음 예제에서는 형식을 보여 줍니다 `TypeA` 구현 하는 <xref:System.IDisposable> (`FT` 이전 토론에서).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>예제
 다음 예제에서는 형식을 보여 줍니다 `TypeB` 필드를 선언 하 여이 규칙을 위반 하 `aFieldOfADisposableType` (`F` 이전 토론에서) 삭제 가능한 형식으로 (`TypeA`) 호출 하지 <xref:System.IDisposable.Dispose%2A> 필드입니다. `TypeB` 에 해당 `T` 이전 논의 합니다.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.IDisposable?displayProperty=fullName> [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
