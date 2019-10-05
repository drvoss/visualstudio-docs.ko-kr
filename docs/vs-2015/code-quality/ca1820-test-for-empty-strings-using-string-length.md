---
title: 'CA1820: 문자열 길이 사용 하 여 문자열이 비었는지 테스트 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bebd3b78881f9e1a2f4908ea667f80cbd7b98dd6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201723"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: 문자열 길이를 사용하여 빈 문자열을 테스트하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|범주|Microsoft.Performance|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 빈 문자열을 사용 하 여 비교 <xref:System.Object.Equals%2A?displayProperty=fullName>합니다.

## <a name="rule-description"></a>규칙 설명
 사용 하 여 문자열을 비교 합니다 <xref:System.String.Length%2A?displayProperty=fullName> 속성 또는 <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> 메서드를 사용 하 여 보다 훨씬 빠릅니다 <xref:System.Object.Equals%2A>합니다. 왜냐하면 <xref:System.Object.Equals%2A> 보다 훨씬 더 많은 MSIL 명령을 실행 <xref:System.String.IsNullOrEmpty%2A> 또는 검색을 실행 하는 명령 수가 <xref:System.String.Length%2A> 속성 값 및 0으로 비교 합니다.

 알고 있어야 하는 <xref:System.Object.Equals%2A> 및 <xref:System.String.Length%2A> = = 0 null 문자열에 다르게 동작 합니다. 값을 가져오려고 시도 합니다 <xref:System.String.Length%2A> null 문자열에서 속성을 공용 언어 런타임에서 throw를 <xref:System.NullReferenceException?displayProperty=fullName>입니다. 공용 언어 런타임; 예외를 throw 하지 않는 빈 문자열과 null 문자열 비교를 수행 하는 경우 비교 반환 `false`합니다. Null에 대 한 테스트 이러한 두 가지 방법의 상대적 성능을 크게 영향을 주지 않습니다. 대상으로 할 때 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]를 사용 하 여를 <xref:System.String.IsNullOrEmpty%2A> 메서드. 그렇지 않은 경우 사용 된 <xref:System.String.Length%2A> 비교 가능한 경우 = =.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반을 해결 하려면 사용할 비교 종류를 변경 합니다 <xref:System.String.Length%2A> 속성과 null 문자열에 대 한 테스트 합니다. 대상으로 하는 경우 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]를 사용 하 여를 <xref:System.String.IsNullOrEmpty%2A> 메서드.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 성능 문제가 없는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 빈 문자열에 대 한 확인 하는 데 사용 되는 다양 한 기법을 보여 줍니다.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
