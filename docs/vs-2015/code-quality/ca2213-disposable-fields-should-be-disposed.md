---
title: 'CA2213: 삭제 가능한 필드는 삭제 해야 합니다. | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8ebeae3e5e367bb2c1a09bc1cb38dcc80d2c3826
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662890"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: 삭제 가능한 필드는 삭제해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 @No__t_0를 구현 하는 형식은 <xref:System.IDisposable>도 구현 하는 형식의 필드를 선언 합니다. 필드의 <xref:System.IDisposable.Dispose%2A> 메서드는 선언 형식의 <xref:System.IDisposable.Dispose%2A> 메서드에 의해 호출 되지 않습니다.

## <a name="rule-description"></a>규칙 설명
 형식은 관리 되지 않는 모든 리소스의 삭제를 담당 합니다. 이는 <xref:System.IDisposable>을 구현 하 여 수행 됩니다. 이 규칙은 삭제 가능한 형식 `T` `F` 삭제 가능한 `FT` 형식의 인스턴스인 필드를 선언 하는지 여부를 확인 합니다. 각 필드 `F`에 대해 규칙은 `FT.Dispose` 호출을 찾으려고 시도 합니다. 규칙은 `T.Dispose`에 의해 호출 되는 메서드를 검색 하 고, 한 수준 아래 (`FT.Dispose`에 의해 호출 된 메서드에 의해 호출 되는 메서드)를 검색 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 필드가 보유 하 고 있는 관리 되지 않는 리소스를 할당 하 고 해제 하는 경우 <xref:System.IDisposable>를 구현 하는 형식의 필드에 대해 <xref:System.IDisposable.Dispose%2A>를 호출 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 필드에서 보유 하는 리소스를 해제 하는 일이 없거나, <xref:System.IDisposable.Dispose%2A>에 대 한 호출이 규칙 검사 보다 더 깊은 호출 수준에서 발생 하는 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 <xref:System.IDisposable> (이전 설명의 `FT`)를 구현 하는 `TypeA` 형식을 보여 줍니다.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>예제
 다음 예에서는 필드 `aFieldOfADisposableType` (이전 설명의 `F`)를 삭제 가능한 형식 (`TypeA`)으로 선언 하 고 필드에 대 한 <xref:System.IDisposable.Dispose%2A>를 호출 하지 않고이 규칙을 위반 하는 `TypeB` 형식을 보여 줍니다. `TypeB`는 이전 토론의 `T`에 해당 합니다.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>관련 항목:
 <xref:System.IDisposable?displayProperty=fullName> [Dispose 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
